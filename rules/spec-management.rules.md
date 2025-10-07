# Spec Management & Referencing Rules (MANDATORY)

This document outlines the mandatory workflow for creating, managing, and referencing specifications. Adherence is critical for maintainability and traceability.

---

## 1. When to Create a Spec

A spec is **MANDATORY** for any non-trivial code change (i.e., more than a typo fix). All decisions on **architecture, technology, data models, or APIs** require a spec.

**When in doubt, create a spec.**

---

## 2. Specification Workflow

### Step 1: Research
- **Search First:** Before creating a spec, query `project-specs/index.json` to find existing, relevant specs.
- **No Duplicates:** If a similar spec exists, update it. Do not create a new one.

### Step 2: Create
- **Location:** `project-specs/`
- **Naming:** `kebab-case.spec.md` (e.g., `api-authentication.spec.md`)
- **Template:** Use `rules/templates/spec.template.md` exactly.

### Step 3: Get Approval
- **Present:** Share the spec with the user for review.
- **Ask:** Use an interactive command: `"I have created/updated the spec for [decision]. Please review and approve."`
- **Wait:** Do not proceed without explicit approval.

### Step 4: Update Index
- **After Approval:** Once a new spec is approved, you **MUST** add a new entry to the `project-specs/index.json` file.
- **Format:** The entry must be a JSON object with `title`, `path`, and `affectedFiles` keys.
  ```json
  {
    "title": "Spec Title",
    "path": "project-specs/spec-name.spec.md",
    "affectedFiles": [
      "path/to/file-one.js",
      "path/to/file-two.ts"
    ]
  }
  ```
- **Synchronization:** The `affectedFiles` list in this JSON entry **MUST** be identical to the list in the corresponding spec markdown file.

---

## 3. Two-Way Spec Referencing

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

## 4. Legacy Code Workflow

For existing code without a spec reference:
1.  **STOP.**
2.  **Analyze** the code's purpose.
3.  **Create Spec** by reverse-engineering the code.
4.  **Get Approval** from the user.
5.  **Add Reference** comment to the legacy code.
6.  **Proceed** with original modifications.

---

## 5. Maintenance & Enforcement

- **Specs are Living Documents:** They **MUST** be updated when decisions change or the implementation deviates.
- **Your Responsibility:** Proactively identify when a new decision alters an existing spec. Update the spec and get approval before proceeding.
- **Violations:** Failure to create, reference, get approval for, or **maintain** a spec is a critical violation. Stop all work until the process is followed correctly.