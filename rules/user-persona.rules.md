# User Persona Rules

## OVERVIEW

This file defines how coding agents should adapt their communication style and interaction approach based on the user's experience level and preferences.

**VIOLATION ENFORCEMENT:** All violations of rules in this file are subject to the universal violation enforcement system defined in [rules/violation-enforcement.rules.md](./violation-enforcement.rules.md).

---

## MANDATORY USER PERSONA SETUP

**CRITICAL REQUIREMENT: CODING AGENTS MUST HAVE A USER PERSONA SPEC IN MEMORY**

**BEFORE ANY CODING SESSION, AGENTS MUST:**

1. **CHECK FOR PERSONA SPEC:** Look for `specs/user-persona.spec.md` 
2. **FORCE PERSONA SETUP:** If no spec exists, STOP and initiate persona setup workflow
3. **LOAD PERSONA:** Read and apply persona settings to all interactions
4. **NEVER ASSUME:** Do not assume any default persona - always require explicit setup

---

## PERSONA DETECTION WORKFLOW

### Step 1: Check for Existing Persona
```
IF specs/user-persona.spec.md EXISTS:
  READ persona specifications
  LOAD into memory for session
  CONTINUE with adapted approach
ELSE:
  INITIATE persona setup workflow (Step 2)
```

### Step 2: Present Persona Options
```
READ specs/user-personas/ directory to discover available predefined options
PRESENT available options:
1. Predefined personas (list discovered options from directory)
2. Custom persona option

WAIT for user selection following **USE `run_command` TOOL** for all questions - **MUST FOLLOW** [rules/interactive-input.rules.md](./interactive-input.rules.md) for context on using run_command tool
```

### Step 3: Handle User Selection
```
IF user selects predefined persona:
  COPY selected persona to specs/user-persona.spec.md
  LOAD persona settings
  CONTINUE with session

IF user selects custom option:
  INITIATE interactive persona creation (Step 4)
```

### Step 4: Interactive Persona Creation
```
READ rules/templates/persona.template.md for required fields and structure
ASK user questions based on persona template following **USE `run_command` TOOL** for all questions - **MUST FOLLOW** [rules/interactive-input.rules.md](./interactive-input.rules.md) for context on using run_command tool:
1. Role (their primary job function)
2. Experience Level (none, enthusiast, beginner, intermediate, senior, expert)

CREATE specs/user-persona.spec.md with responses
LOAD persona settings
CONTINUE with session
```

---

## TEMPLATE ACCESS RULES

### Persona Template Access
- **Template Location:** `rules/templates/persona.template.md`
- **Access Rule:** READ ONLY during Step 4 (Interactive Persona Creation)
- **Prohibition:** NEVER read template file outside of persona creation workflow
- **Purpose:** Performance optimization - template only accessed when needed

---

## PERSONA FILE LOCATIONS

### Active Persona (Required)
- **Location:** `specs/user-persona.spec.md`
- **Purpose:** Current user's persona for this project
- **Priority:** MANDATORY - must exist before any coding session

### Predefined Personas (Templates)
- **Location:** `specs/user-personas/` directory
- **Purpose:** Well-crafted persona options for agent to present to user during setup
- **Access Rules:**
  - **READ DIRECTORY:** Only when `specs/user-persona.spec.md` does NOT exist
  - **IGNORE DIRECTORY:** If `specs/user-persona.spec.md` already exists (saves response time)
  - **Usage:** Agent reads available options to present choices during persona setup workflow

---

## COMMUNICATION ADAPTATION RULES

### Experience Level Adaptations

#### None/Enthusiast (0-1 years)
- **Terminology:** Explain all technical terms with context
- **Explanations:** Step-by-step with examples and analogies
- **Decisions:** Present 1-2 simple options with clear recommendations

#### Beginner (1-2 years)
- **Terminology:** Explain technical terms, provide context
- **Explanations:** Detailed explanations with key concepts highlighted
- **Decisions:** Present 2 options with pros/cons clearly explained

#### Intermediate (3-5 years)
- **Terminology:** Use standard terminology with brief explanations when needed
- **Explanations:** Moderate detail focusing on important concepts
- **Decisions:** Present 2-3 options with trade-off analysis

#### Senior (6-9 years)
- **Terminology:** Use advanced terminology without basic explanations
- **Explanations:** Concise explanations focusing on trade-offs and implications
- **Decisions:** Present multiple options with detailed trade-off analysis

#### Expert (10+ years)
- **Terminology:** Use domain-specific jargon and assume deep knowledge
- **Explanations:** Brief summaries with assumptions clearly stated
- **Decisions:** Present comprehensive options with nuanced considerations

---

## PERSONA SPECIFICATION REQUIREMENTS

### File Format
- **Extension:** `.spec.md`
- **Location:** `specs/user-persona.spec.md`
- **Template:** Follow persona template structure for consistency

---

## VIOLATION CONSEQUENCES

**FAILURE TO SETUP PERSONA:**
1. **CRITICAL ERROR:** Session cannot proceed without persona spec
2. **MANDATORY ACTION:** Force persona setup workflow immediately
3. **NO ASSUMPTIONS:** Never assume default persona or skip setup

**INCORRECT PERSONA APPLICATION:**
1. **Detection:** Monitor user feedback for communication mismatches
2. **Adjustment:** Modify approach based on user corrections
3. **Update:** Modify `specs/user-persona.spec.md` if needed

---

## MAINTENANCE RULES

### Persona Updates
- **When:** User provides feedback about communication preferences
- **How:** Update `specs/user-persona.spec.md` with new preferences
- **Validation:** Confirm changes improve user experience

---

*Simplified persona system for consistent user-adapted communication*