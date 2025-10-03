# Core Principles for Interactive Coding Agents

**MANDATORY: ALL CODING AGENTS MUST FOLLOW THIS WORKFLOW**

This file defines the fundamental workflow and core principles that ALL coding agents must follow during any coding session. These are the foundational rules that govern how agents think, research, decide, and implement.

**VIOLATION ENFORCEMENT:** All violations of rules in this file are subject to the universal violation enforcement system defined in [rules/violation-enforcement.rules.md](./violation-enforcement.rules.md).

---

## CORE AGENT WORKFLOW

**MANDATORY SEQUENCE - NEVER SKIP STEPS:**

### 1. PERSONA ASSIMILATION
- **MANDATORY FIRST STEP:** Load and assimilate user persona from `specs/user-personas/`
- **FOLLOW** the persona workflow defined in `rules/user-persona.rules.md`
- **ADAPT** communication style based on user's role and experience level
- **ENSURE** persona is active before proceeding with any coding tasks

### 2. AGENT THINK
- **ANALYZE** the user's request thoroughly
- **IDENTIFY** what needs to be implemented or changed
- **ASSESS** the complexity and scope of the task
- **DETERMINE** if new decisions or patterns will be introduced

### 3. CHECK SPECIFICATIONS
- **MANDATORY:** Always check `project-specs/index.spec.md`
- **SEARCH** existing `.spec.md` files for related decisions
- **REVIEW** established patterns and architectural choices
- **IDENTIFY** gaps where new specifications might be needed

### 4. ASK FOR CLARIFICATION

**CLARIFICATION PROTOCOL:**
- Follow [rules/interactive-input.rules.md](./interactive-input.rules.md) for all user interaction requirements
- **CONFIRM** understanding before proceeding

### 5. CREATE SPECIFICATION (IF NEEDED)
- **MANDATORY:** Create `.spec.md` file for new impactful decisions
- **DOCUMENT** architectural choices, technology selections, patterns
- **FOLLOW** the mandatory template from `rules/templates/spec.template.md`
- **UPDATE** `project-specs/index.spec.md` immediately

### 6. GET APPROVAL FOR IMPLEMENTATION

**APPROVAL PROTOCOL:**
- Follow [rules/interactive-input.rules.md](./interactive-input.rules.md) for all user interaction requirements
- **WAIT** for explicit user approval before coding
- **CONFIRM** implementation steps align with specifications

### 7. IMPLEMENT ACCORDING TO SPECIFICATIONS
- **RE-READ** all relevant specifications after approval but before implementation
- **FOLLOW** approved specifications exactly
- **MAINTAIN** consistency with established patterns
- **IMPLEMENT** only what was approved
- **AVOID** adding unrequested features

### 8. LOOP BACK IF NEW DECISIONS ARISE
- **STOP IMMEDIATELY** if new decisions emerge during implementation
- **RETURN TO STEP 3** (Check Specifications)
- **DOCUMENT** new decisions before continuing
- **GET APPROVAL** for any changes to the implementation plan

---

## CORE PRINCIPLES

### SPECIFICATION-FIRST DEVELOPMENT
- **NEVER** implement without checking existing specifications
- **ALWAYS** document new architectural decisions
- **MANDATORY** specification creation for impactful choices
- **FORBIDDEN** to proceed without proper documentation

### INTERACTIVE CLARIFICATION
- **PAUSE** implementation when requirements are unclear
- **ASK** specific questions using interactive input
- **CONFIRM** understanding before proceeding
- **AVOID** assumptions about user intent
- Follow [rules/interactive-input.rules.md](./interactive-input.rules.md) for all user interaction protocols

### APPROVAL-BASED IMPLEMENTATION
- **WAIT** for explicit approval before implementing
- **PRESENT** clear implementation plans
- **EXPLAIN** what will be built and why
- **RESPECT** user decisions and preferences
- Follow [rules/interactive-input.rules.md](./interactive-input.rules.md) for all user interaction protocols

### CONSISTENCY ENFORCEMENT
- **FOLLOW** established patterns and conventions
- **MAINTAIN** architectural consistency
- **REFERENCE** existing specifications for guidance
- **AVOID** introducing conflicting patterns

---

## CRITICAL VIOLATIONS

**IMMEDIATE STOP AND CORRECTION REQUIRED:**

1. **SKIPPING SPECIFICATION CHECK** - Implementing without reviewing existing specs
2. **ASSUMPTION-BASED IMPLEMENTATION** - Proceeding without clarification
3. **UNDOCUMENTED DECISIONS** - Making architectural choices without specification
4. **UNAUTHORIZED IMPLEMENTATION** - Coding without explicit approval
5. **PATTERN VIOLATIONS** - Ignoring established architectural patterns

**VIOLATION CONSEQUENCES:**
- **FIRST VIOLATION:** Stop immediately, follow proper workflow, restart implementation
- **REPEATED VIOLATIONS:** Session termination and restart with proper compliance
- **CRITICAL VIOLATIONS:** Immediate rollback and specification creation before proceeding

---

## ENFORCEMENT

**ALL CODING AGENTS MUST:**
- Follow this workflow for EVERY coding task
- Reference this file when making implementation decisions
- Prioritize specification compliance over speed
- Maintain consistency with established patterns
- Document all new architectural decisions

**FORBIDDEN ACTIONS:**
- Skipping workflow steps to save time
- Implementing without proper specification review
- Making assumptions about undocumented decisions
- Proceeding without user approval
- Ignoring established patterns and conventions

---

*This file establishes the foundational workflow that all other rule files build upon. Detailed enforcement rules are found in specialized rule files like `spec-management.rules.md`.*

---

*Created by [@matscode](https://www.tiktok.com/@matscode) | [LinkedIn](https://www.linkedin.com/in/matscode)*