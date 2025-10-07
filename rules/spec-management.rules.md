# Spec Management & Referencing Rules

**MANDATORY: ALL CODING AGENTS MUST FOLLOW THESE SPECIFICATION RULES**

This document defines the complete, unified workflow for creating, managing, and referencing specifications. It combines the core principles of specification-driven development with the practical rules for referencing those specifications in code. Adherence to these rules is critical for ensuring maintainability, traceability, and consistency.

---

## 1. Core Principles: When to Create a Spec

A spec is **MANDATORY** for any code change that is not a trivial fix (e.g., a typo or minor bug).

If you are making a decision about **architecture, technology, data models, or APIs**, you **MUST** create a spec first.

**When in doubt, create a spec.**

---

## 2. The Specification Workflow

### Step 1: Research and Validate
- **Search First:** Before creating a new spec, search the `project-specs/` directory to see if an existing spec already covers the decision.
- **Check the Index:** Review `project-specs/index.spec.md` for related decisions.
- **No Duplicates:** Never create a duplicate spec. If a similar one exists, update it.

### Step 2: Create the Specification File
- **Location:** All specs **MUST** be placed in the `project-specs/` directory.
- **Naming:** Use kebab-case and the `.spec.md` extension (e.g., `api-authentication.spec.md`).
- **Template:** Use the exact structure from `rules/templates/spec.template.md`. Do not deviate.

### Step 3: Get Approval
- **Present to User:** Share the new or updated spec with the user for review.
- **Ask for Approval:** Use an interactive command to ask, `"I have created/updated the specification for [decision]. Please review and approve."`
- **Wait:** Do not proceed until you receive explicit approval.

---

## 3. Spec Reference Rules

To ensure full traceability, referencing between code and specifications **MUST** be a two-way link.

### From Code to Spec (Mandatory)

All generated code files **MUST** include a reference to the specification that guided their implementation.

#### Standard Format
Use a simple, single-line comment at the top of the file.

```
[COMMENT_SYNTAX] Implementation based on: [project-specs/<filename>.spec.md] - Section: [Specific Section Name]
```

**CRITICAL:** Do NOT use JSDoc or other complex, multi-line formats for spec references.

#### Language-Specific Examples
- **JavaScript/TypeScript:** `// ...`
- **Python:** `# ...`
- **CSS:** `/* ... */`
- **HTML:** `<!-- ... -->`
- **SQL:** `-- ...`

#### Placement
1.  **Primary:** At the top of the file, after license headers but before imports.
2.  **Secondary:** Before a specific class or function if it implements a different spec section.

#### Multiple Specs
If a file implements multiple specs, list them vertically:
```javascript
// Implementation based on:
// - [project-specs/authentication.spec.md] - Section: Login Flow
// - [project-specs/ui-components.spec.md] - Section: Form Validation
```

### From Spec to Code (Mandatory)

To complete the two-way link, every spec file **MUST** list the code files that implement it under the `### 4. Affected Files` section.

- **Reference**: In the spec file, you MUST use the `### 4. Affected Files` heading.
- **Format**:
  ```markdown
  ### 4. Affected Files
  *A list of files that will be created or modified as part of this implementation.*
  - `path/to/file-one.js`
  - `path/to/file-two.css`
  ```
- **Purpose**: This creates a link from the decision to the code that implements it, making it easy to find all related code.

---

## 4. Legacy Code Workflow

When you encounter existing code that has no spec reference:

1.  **STOP:** Do not modify the code.
2.  **Analyze:** Understand the code's purpose, logic, and dependencies.
3.  **Create Spec:** Reverse-engineer a specification from the code and place it in `project-specs/`.
4.  **Get Approval:** Present the new spec to the user for approval.
5.  **Add Reference:** Once approved, add the spec reference comment to the top of the legacy code file.
6.  **Proceed:** Only now may you proceed with your original modifications, following the new spec.

---

## 5. Maintenance and Enforcement

- **Specs are Living Documents:** Specifications are not static. They are living documents that **MUST** be updated whenever a decision changes, new requirements are introduced, or the implementation deviates from the original plan.
- **Your Responsibility:** It is your responsibility to proactively identify when a new decision invalidates or alters an existing spec. When this happens, you **MUST** update the spec and get approval before proceeding.
- **Violations:** Failure to create, reference, get approval for, or **maintain** a spec is a critical violation. All work must stop until the specification process is correctly followed.