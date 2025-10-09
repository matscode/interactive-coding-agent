# Spec Management & Referencing Rules (MANDATORY)

<!-- Authored by @matscode -->

This document outlines the mandatory workflow for creating, managing, and referencing specifications. Adherence is critical for maintainability and traceability.

---

## 1. Specification Types

This section clarifies the differences between Project and Feature specifications.

- **Project Spec:** A high-level document that outlines the core, project-wide decisions. It is the single source of truth for the project's overall direction and branding.
- **Feature Spec:** A detailed document that describes the requirements, implementation, and affected files for a specific feature or non-trivial code change.

---

## 2. Project Spec Workflow

<!-- Authored by @matscode -->

**MANDATORY**

1.  **Read the Project Spec:** Always read the `specs/project.spec.md` file first to understand the high-level project context.
2.  **Project-Level Decisions:** All project-level decisions, such as project name, description, tagline, and branding, **MUST** be documented in the `specs/project.spec.md` file.
3.  **Spec List Integrity:** Only specification files located within the `specs/` directory are permitted to be included in the `Extra Spec List`.

---

## 3. Feature Spec Workflow

### Updating the Project Spec

If a feature introduces any new project-wide element—such as a **dependency, color, font, or other branding element**—the feature spec's implementation plan **MUST** include a step to update the corresponding section of `specs/project.spec.md`.

---

## 2. When to Create a Spec

<!-- Authored by @matscode -->



A spec is **MANDATORY** for any non-trivial code change (i.e., any change that is not a minor typographical fix).

For a comprehensive list of examples, refer to the **[Specification Decision Examples](./spec-decision-examples.rules.md)** document. This guide provides detailed scenarios to help determine when a specification is necessary.

**When in doubt, create a spec.**

### Decision-Making Trigger Words
When users use these phrases, they're likely making decisions that need documentation:

**INSTALLATION & ADOPTION:**
- "Let's install..." / "Should we install..." / "Install [library/tool]"
- "Add [dependency/package]" / "Use [framework/library]"
- "Switch to..." / "Migrate to..." / "Adopt [technology]"

**COMPARISON & EVALUATION:**
- "Compare [A] vs [B]" / "What's better..." / "Best [solution/approach]"
- "Deciding between..." / "Choose..." / "Pick..."
- "Pros and cons" / "Trade-offs" / "Alternatives"

**ARCHITECTURAL DECISIONS:**
- "How should we..." / "What's the right way to..."
- "Structure..." / "Organize..." / "Design..."
- "Approach for..." / "Strategy for..." / "Pattern for..."

**CONFIGURATION & SETUP:**
- "Configure..." / "Set up..." / "Initialize..."
- "Which settings..." / "How to configure..."
- "Default values" / "Environment setup"

### Context Requirements
A spec is also required when coding agents need context for:
- **Consistency Requirements:** Decisions that must be uniform across the codebase (naming conventions, file organization, API patterns).
- **Trade-off Implications:** Choices with significant pros/cons that affect future development (performance vs readability, flexibility vs simplicity).
- **Knowledge Dependencies:** Decisions requiring domain expertise or research that agents shouldn't repeat (security standards, compliance requirements).
- **Team Alignment:** Choices that impact multiple developers or system components (shared libraries, communication protocols).
- **Future Constraints:** Decisions that limit or enable future options (database schema design, API versioning, plugin architectures).

---

## 3. Agent Response Protocol

Before creating any specification file, agents MUST ask these questions to ensure optimal documentation:

**DECISION CLARITY:**
- "What is your final decision? (If not explicitly stated)"
- "Can you confirm this is the approach you want to proceed with?"

**SPEC DESTINATION:**
- "Should this decision be documented in the project spec or a feature spec? (project/feature)"

**SOURCE DOCUMENTATION:**
- "Are there any specific articles, documentation, or resources that influenced your decision?"

### 3.1 Interactive Input Compliance
All questions in this protocol MUST comply with the rules for asking questions and handling user input as defined in `rules/interactive-input.rules.md`.

---

## 4. Specification Workflow

<!-- Authored by @matscode -->

### Step 1: Specification Selection and Reuse Protocol

**MANDATORY: BEFORE CREATING A NEW SPEC, YOU MUST FOLLOW THIS PROTOCOL:**

1.  **Search the Spec Index:** Perform a comprehensive keyword search against the `title` and `keywords` fields in `feature-specs/index.json` to find all potentially relevant specs.

2.  **Select Candidate Specifications:** From the search results, identify the 2-3 specs that most closely match the current requirement.

3.  **Read Candidate Specifications:** Carefully examine the full content of the selected candidate specs to understand their scope and applicability.

4.  **Determine Specification Strategy:** Based on your reading, choose one of the following strategies:
    -   **Reuse Existing:** If a spec fully covers the requirement, use it. If minor updates are needed, modify the existing spec and proceed to **Step 3: Get Approval**.
    -   **Extend Existing:** If a spec partially covers the requirement, extend it by adding new sections. Ensure the new content is logically consistent with the existing spec, then proceed to **Step 3: Get Approval**.
    -   **Create Supporting Spec:** If an existing spec is related but distinct, create a new, complementary spec. Ensure a clear separation of concerns between the two.
    -   **Create New Spec:** Only create a new specification if no existing spec is relevant or applicable.

5.  **Resolve Conflicts:** If you are uncertain which strategy to choose or which spec to update, present the options to the user and ask for guidance using an interactive command as defined in `rules/interactive-input.rules.md`. Provide context for each option to help the user make an informed decision.

### Step 2: Create
- **Location:** `feature-specs/`
- **Naming:** `kebab-case.spec.md` (e.g., `api-authentication.spec.md`)
- **Template:** Use `rules/templates/spec.template.md` exactly.
- **Implementation Steps:** The `Key Implementation Steps` section **MUST** be detailed and transparent, outlining each step of the implementation.

### Step 3: Get Approval
- **Present:** Share the spec with the user for review.
- **Ask:** Use an interactive command as defined in `rules/interactive-input.rules.md` to ask for approval. The question should be: `"I have created/updated the spec for [decision]. Please review and approve."`
- **Wait:** Do not proceed without explicit approval.

### Step 4: Update Index
- **After Approval:** Once a new spec is approved, you **MUST** add a new entry to the `feature-specs/index.json` file.
- **Format:** The entry must be a JSON object with `title`, `path`, and `keywords` keys.
  ```json
  {
    "title": "Spec Title",
    "path": "feature-specs/spec-name.spec.md",
    "keywords": ["keyword1", "keyword2", "technology"]
  }
  ```

---

## 5. Two-Way Spec Referencing

### From Code to Spec (Mandatory)
All generated code **MUST** reference its guiding spec.

- **Format:** Use a single-line comment.
  ```
  [COMMENT_SYNTAX] Implements: [feature-specs/<filename>.spec.md] - Section: [Section Name]
  ```
- **CRITICAL:** Do NOT use multi-line formats (e.g., JSDoc).
- **Placement:**
  1.  **Primary:** Top of the file.
  2.  **Secondary:** Before a class or function if it implements a different spec/section.
- **Multiple Specs:** List vertically.
  ```javascript
  // Implements:
  // - [feature-specs/authentication.spec.md] - Section: Login Flow
  // - [feature-specs/ui-components.spec.md] - Section: Form Validation
  ```

### From Spec to Code (Mandatory)
Every spec **MUST** list the code files that implement it.

- **Location:** In the spec file, under the `### 3. Affected Files` heading.
- **Format:**
  ```markdown
  ### 3. Affected Files
  - `path/to/file-one.js`
  ```

---

## 6. Legacy Code Workflow

For existing code that lacks a spec reference, you **MUST** follow this protocol **BEFORE** making any changes:

1.  **STOP & Analyze:** Do not modify the code. Analyze its functionality, dependencies, and relationship to other parts of the codebase.
2.  **Search for Existing Spec:** Conduct a thorough search in `feature-specs/index.json` to determine if a relevant spec already exists but is not referenced.
3.  **Create Retroactive Spec:** If no spec exists, create a new one that accurately documents the behavior of the legacy code. The spec should describe the code as it currently exists.
4.  **Get Approval:** Present the newly created spec to the user for approval.
5.  **Add Spec Reference:** Once approved, add the spec reference to the legacy code.
6.  **Propose Changes:** With the spec in place, you may now propose changes to the code, following the standard specification workflow.


---

## 7. Maintenance & Enforcement

- **Specs are Living Documents:** They **MUST** be updated when decisions change or the implementation deviates.
- **Concurrent Updates:** The spec file **MUST** be updated in real-time as the implementation progresses. The "Key Implementation Steps" should be checked off as they are completed.
- **All Changes Documented:** Any change to a specification, no matter how small, **MUST** be followed by an update to the spec file and a request for user approval.
- **Your Responsibility:** Proactively identify when a new decision alters an existing spec. Update the spec and get approval before proceeding.
- **Violations:** Failure to create, reference, get approval for, or **maintain** a spec is a critical violation. Stop all work until the process is followed correctly.

-- Authored by [matscode](https://www.linkedin.com/in/matscode)
