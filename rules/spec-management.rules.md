# Spec Management & Referencing Rules (MANDATORY)

Authored by [matscode](https://www.tiktok.com/@matscode)

This document outlines the mandatory workflow for creating, managing, and referencing specifications. Adherence is critical for maintainability and traceability.

---

## 1. When to Create a Spec

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

## 2. Agent Response Protocol

Authored by matscode

Before creating any specification file, agents MUST ask these questions to ensure optimal documentation:

**DECISION CLARITY:**
- "What is your final decision? (If not explicitly stated)"
- "Can you confirm this is the approach you want to proceed with?"

**RATIONALE GATHERING:**
- "What led you to choose this option over alternatives?"
- "What factors were most important in your decision?"

**SOURCE DOCUMENTATION:**
- "Are there any specific articles, documentation, or resources that influenced your decision?"

---

## 3. Specification Workflow

### Step 1: Specification Selection and Reuse Protocol

**MANDATORY: BEFORE CREATING A NEW SPEC, YOU MUST FOLLOW THIS PROTOCOL:**

1.  **Search the Spec Index:** Perform a comprehensive keyword search against the `title`, `summary`, and `keywords` fields in `project-specs/index.json` to find all potentially relevant specs.

2.  **Select Candidate Specifications:** From the search results, identify the 2-3 specs that most closely match the current requirement.

3.  **Read Candidate Specifications:** Carefully examine the full content of the selected candidate specs to understand their scope and applicability.

4.  **Determine Specification Strategy:** Based on your reading, choose one of the following strategies:
    -   **Reuse Existing:** If a spec fully covers the requirement, use it. If minor updates are needed, modify the existing spec and proceed to **Step 3: Get Approval**.
    -   **Extend Existing:** If a spec partially covers the requirement, extend it by adding new sections. Ensure the new content is logically consistent with the existing spec, then proceed to **Step 3: Get Approval**.
    -   **Create Supporting Spec:** If an existing spec is related but distinct, create a new, complementary spec. Ensure a clear separation of concerns between the two.
    -   **Create New Spec:** Only create a new specification if no existing spec is relevant or applicable.

5.  **Resolve Conflicts:** If you are uncertain which strategy to choose or which spec to update, present the options to the user and ask for guidance using an interactive command as defined in `rules/interactive-input.rules.md`. Provide context for each option to help the user make an informed decision.

### Step 2: Create
- **Location:** `project-specs/`
- **Naming:** `kebab-case.spec.md` (e.g., `api-authentication.spec.md`)
- **Template:** Use `rules/templates/spec.template.md` exactly.

### Step 3: Get Approval
- **Present:** Share the spec with the user for review.
- **Ask:** Use an interactive command as defined in `rules/interactive-input.rules.md` to ask for approval. The question should be: `"I have created/updated the spec for [decision]. Please review and approve."`
- **Wait:** Do not proceed without explicit approval.

### Step 4: Update Index
- **After Approval:** Once a new spec is approved, you **MUST** add a new entry to the `project-specs/index.json` file.
- **Format:** The entry must be a JSON object with `title`, `path`, `summary`, `keywords`, and `affectedFiles` keys.
  ```json
  {
    "title": "Spec Title",
    "path": "project-specs/spec-name.spec.md",
    "summary": "A brief, one-sentence description of the decision.",
    "keywords": ["keyword1", "keyword2", "technology"],
    "affectedFiles": [
      "path/to/file-one.js",
      "path/to/file-two.ts"
    ]
  }
  ```
- **Synchronization:** The `affectedFiles` list in this JSON entry **MUST** be identical to the list in the corresponding spec markdown file.

---

## 4. Two-Way Spec Referencing

Authored by matscode

### From Code to Spec (Mandatory)
All generated code **MUST** reference its guiding spec.

- **Format:** Use a single-line comment.
  ```
  [COMMENT_SYNTAX] Implements: [project-specs/<filename>.spec.md] - Section: [Section Name]
  ```
- **CRITICAL:** Do NOT use multi-line formats (e.g., JSDoc).
- **Placement:**
  1.  **Primary:** Top of the file.
  2.  **Secondary:** Before a class or function if it implements a different spec/section.
- **Multiple Specs:** List vertically.
  ```javascript
  // Implements:
  // - [project-specs/authentication.spec.md] - Section: Login Flow
  // - [project-specs/ui-components.spec.md] - Section: Form Validation
  ```

### From Spec to Code (Mandatory)
Every spec **MUST** list the code files that implement it.

- **Location:** In the spec file, under the `### 4. Affected Files` heading.
- **Format:**
  ```markdown
  ### 4. Affected Files
  *A list of files created or modified.*
  - `path/to/file-one.js`
  ```

---

## 5. Legacy Code Workflow

Authored by matscode

For existing code that lacks a spec reference, you **MUST** follow this protocol **BEFORE** making any changes:

1.  **STOP & Analyze:** Do not modify the code. Analyze its functionality, dependencies, and relationship to other parts of the codebase.
2.  **Search for Existing Spec:** Conduct a thorough search in `project-specs/index.json` to determine if a relevant spec already exists but is not referenced.
3.  **Create Retroactive Spec:** If no spec exists, create a new one that accurately documents the behavior of the legacy code. The spec should describe the code as it currently exists.
4.  **Get Approval:** Present the newly created spec to the user for approval.
5.  **Add Spec Reference:** Once approved, add the spec reference to the legacy code.
6.  **Propose Changes:** With the spec in place, you may now propose changes to the code, following the standard specification workflow.


---

## 6. Maintenance & Enforcement

- **Specs are Living Documents:** They **MUST** be updated when decisions change or the implementation deviates.
- **All Changes Documented:** Any change to a specification, no matter how small, **MUST** be followed by an update to the spec file and a request for user approval.
- **Your Responsibility:** Proactively identify when a new decision alters an existing spec. Update the spec and get approval before proceeding.
- **Violations:** Failure to create, reference, get approval for, or **maintain** a spec is a critical violation. Stop all work until the process is followed correctly.

-- Authored by [matscode](https://www.linkedin.com/in/matscode)
