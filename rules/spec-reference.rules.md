# Spec Reference Enforcement Rules

**MANDATORY: ALL CODING AGENTS MUST FOLLOW THESE SPEC REFERENCE REQUIREMENTS**

This file defines the mandatory requirements for including specification references in all generated code files. These rules ensure maintainability, traceability, and consistency across the codebase.

**VIOLATION ENFORCEMENT:** All violations of rules in this file are subject to the universal violation enforcement system defined in [violation-enforcement.rules.md](./violation-enforcement.rules.md).

---

## CORE REQUIREMENT

**MANDATORY SPEC REFERENCES:**
ALL generated code files MUST include spec reference comments that clearly identify:
1. The specification file that guided the implementation
2. The specific section within that specification
3. The relationship between the code and the spec requirements

---

## COMMENT FORMAT REQUIREMENTS

### STANDARD FORMAT
```
[COMMENT_SYNTAX] Implementation based on: [project-specs/<filename>.spec.md] - Section: [Specific Section Name]
```

**CRITICAL: NEVER USE JSDOC OR COMPLEX FORMATS**
- **FORBIDDEN:** JSDoc-style formats with @fileoverview, @specification, @lastUpdated
- **FORBIDDEN:** Multi-line documentation blocks for spec references
- **REQUIRED:** Simple single-line comment format only
- **STANDARD:** Use the exact format shown above with appropriate comment syntax

### LANGUAGE-SPECIFIC COMMENT ADAPTATION

**AGENT RESPONSIBILITY:**
- **KNOW** the appropriate comment syntax for the target programming language
- **ADAPT** the spec reference format to use the correct comment syntax
- **RESEARCH** comment syntax if uncertain about a language

**COMMON LANGUAGE EXAMPLES:**
```javascript
// Implementation based on: [project-specs/ui-components.spec.md] - Section: Button Component Design
```

```python
# Implementation based on: [project-specs/data-processing.spec.md] - Section: CSV Parser Requirements
```

```css
/* Implementation based on: [project-specs/styling.spec.md] - Section: Color Palette and Typography */
```

```html
<!-- Implementation based on: [project-specs/layout.spec.md] - Section: Header Navigation Structure -->
```

```sql
-- Implementation based on: [project-specs/database.spec.md] - Section: User Table Schema
```

**UNKNOWN LANGUAGE PROTOCOL:**
1. **RESEARCH** the language's comment syntax using available tools
2. **WEB SEARCH** if necessary to find official documentation
3. **ASK USER** if research yields no results or conflicting information - **USE `run_command` TOOL** - **MUST FOLLOW** [interactive-input.rules.md](./interactive-input.rules.md) for context on using run_command tool
4. **USE** the format: "What is the proper comment syntax for [language name]?" - **USE `run_command` TOOL** - **MUST FOLLOW** [interactive-input.rules.md](./interactive-input.rules.md) for context on using run_command tool
5. **DOCUMENT** the decision for future reference - **FOLLOW** [spec-management.rules.md](./spec-management.rules.md) for specification documentation workflow

---

## PLACEMENT REQUIREMENTS

### PRIMARY PLACEMENT
**TOP OF FILE** - Immediately after any license/copyright headers, before any imports or code

### SECONDARY PLACEMENTS
1. **Before imports** - Spec references come before any import statements
2. **Function-specific** - Additional references before complex functions implementing different spec sections
3. **Class-specific** - Additional references before class definitions implementing specific spec components
4. **Module-specific** - References at module level for large implementations

---

## MULTIPLE SPEC REFERENCES

When code implements multiple specifications, use multi-line format:

```javascript
// Implementation based on:
// - [project-specs/authentication.spec.md] - Section: Login Flow
// - [project-specs/ui-components.spec.md] - Section: Form Validation
// - [project-specs/security.spec.md] - Section: Password Requirements
```

**ORGANIZATION:**
- List specs in order of implementation priority
- Include specific section names for each spec
- Maintain consistent formatting across all references

---

## EXISTING CODE ENFORCEMENT

### MANDATORY CHECKS
When modifying existing code files, agents MUST:

1. **CHECK** for existing spec reference comments
2. **READ** and understand all referenced specifications
3. **FOLLOW** the patterns and requirements from referenced specs
4. **MAINTAIN** consistency with existing spec-driven implementations
5. **UPDATE** spec references when adding new functionality
6. **VERIFY** all new code includes proper spec references
7. **CONFIRM** spec references match the actual specifications being implemented

### MODIFICATION PROTOCOL
- **PRESERVE** existing spec references unless they become obsolete
- **ADD** new spec references for additional functionality
- **UPDATE** section references if spec sections change
- **MAINTAIN** the same comment format as existing references
- **VALIDATE** that all modifications include appropriate spec references
- **CROSS-CHECK** spec references against actual specification content

### LEGACY CODE HANDLING

**TRIGGER CONDITION:** When modifying existing code files that lack spec reference comments

**MANDATORY WORKFLOW REFERENCE:**
For complete workflow requirements when handling legacy code without specifications, agents MUST follow the comprehensive workflow defined in [spec-management.rules.md](./spec-management.rules.md) under the "LEGACY CODE SPECIFICATION WORKFLOW" section.

**IMMEDIATE REQUIREMENTS:**
- **HALT** all modification activities when encountering code without spec references
- **FOLLOW** the complete legacy code workflow in [spec-management.rules.md](./spec-management.rules.md)
- **ADD** proper spec reference comments after workflow completion
- **ENSURE** correct comment syntax for the file's programming language

---

## MAINTENANCE BENEFITS

**QUICK SPEC IDENTIFICATION:**
- Developers can immediately identify relevant specifications
- Maintenance tasks can quickly locate governing requirements
- Code reviews can verify spec compliance
- Refactoring can maintain spec alignment

**TRACEABILITY:**
- Clear connection between code and requirements
- Audit trail for implementation decisions
- Documentation of architectural choices
- Historical context for code changes

---

## ENFORCEMENT PROTOCOL

**MANDATORY COMPLIANCE:**
- **NO EXCEPTIONS** - All generated code files must include spec references
- **IMMEDIATE IMPLEMENTATION** - Add references during initial code generation
- **CONSISTENT FORMAT** - Use language-appropriate comment syntax
- **COMPLETE INFORMATION** - Include both spec file and section names
- **VERIFICATION REQUIRED** - Agent must verify spec references are added to ALL created/modified files
- **POST-IMPLEMENTATION CHECK** - After any code generation, confirm spec references are present

**CRITICAL VIOLATION PREVENTION:**
- **NEVER** create or modify code files without adding spec reference comments
- **ALWAYS** verify spec references are included before completing implementation
- **STOP IMMEDIATELY** if spec references are missing from generated code
- **REVIEW ALL FILES** created or modified during implementation for spec references
- **VERIFY** format matches the standard before completing implementation

**VIOLATION CONSEQUENCES:**
All violations are subject to the universal violation enforcement system defined in [violation-enforcement.rules.md](./violation-enforcement.rules.md).

---

## INTEGRATION WITH OTHER RULES

**CROSS-REFERENCES:**
- **Spec Management:** [spec-management.rules.md](./spec-management.rules.md) - Overall specification workflow and legacy code handling
- **Core Principles:** [core-principles.rules.md](./core-principles.rules.md) - Implementation workflow integration
- **Interactive Input:** [interactive-input.rules.md](./interactive-input.rules.md) - User clarification procedures
- **Violation Enforcement:** [violation-enforcement.rules.md](./violation-enforcement.rules.md) - Universal violation enforcement system

**WORKFLOW INTEGRATION:**
This rule integrates with the core agent workflow at the "IMPLEMENT ACCORDING TO SPECIFICATIONS" step, ensuring all generated code maintains proper spec traceability. For legacy code without specifications, agents must follow the "LEGACY CODE SPECIFICATION WORKFLOW" defined in [spec-management.rules.md](./spec-management.rules.md).