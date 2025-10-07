# User Persona Rules

## OVERVIEW

This file defines how coding agents should adapt their communication style and interaction approach based on the user's experience level and preferences.

**VIOLATION ENFORCEMENT:** All violations of rules in this file are subject to the universal violation enforcement system defined in [`violation-enforcement.rules.md`](./violation-enforcement.rules.md).

---

## MANDATORY USER PERSONA SETUP

**CRITICAL REQUIREMENT: CODING AGENTS MUST HAVE A USER PERSONA SPEC IN MEMORY**

**ENFORCEMENT PRECEDENCE:** This workflow can ONLY be initiated AFTER completing the enforcement requirements defined in [`index.rules.md`](./index.rules.md) - Enforcement Requirements. Rule reading takes absolute precedence.

**BEFORE ANY CODING SESSION, AGENTS MUST:**

1. **CHECK FOR PERSONA SPEC:** Look for [`specs/user-persona.spec.md`](../specs/user-persona.spec.md) 
2. **FORCE PERSONA SETUP:** If no spec exists, STOP and initiate persona setup workflow
3. **LOAD PERSONA:** Read and apply persona settings to all interactions
4. **NEVER ASSUME:** Do not assume any default persona - always require explicit setup

---

## PERSONA DETECTION WORKFLOW

### Step 1: Check for Existing Persona

**MANDATORY REQUIREMENT:** Agent MUST check for [`specs/user-persona.spec.md`](../specs/user-persona.spec.md) before ANY coding session.

**IF PERSONA EXISTS:**
- READ persona specifications immediately
- LOAD into memory for current session
- CONTINUE with persona-adapted communication approach (Step 1: PERSONA ASSIMILATION of [`core-principles.rules.md`](./core-principles.rules.md))

**IF PERSONA MISSING:**
- **CRITICAL STOP:** Agent MUST NOT proceed with coding
- **MANDATORY ACTION:** Initiate persona setup workflow (Step 2)
- **VIOLATION:** Proceeding without persona = CRITICAL FAILURE

### Step 2: Present Persona Options

**MANDATORY ACTIONS:**
1. **READ DIRECTORY:** Scan [`specs/user-personas/`](../specs/user-personas/) for available predefined personas
2. **PRESENT OPTIONS:** Use MANDATORY interactive input format per [`interactive-input.rules.md`](./interactive-input.rules.md)
3. **CAPTURE SELECTION:** Store user choice for processing

**CRITICAL REQUIREMENT:** MUST use run_command tool with proper interactive format:

**EXAMPLE FORMAT (DO NOT EXECUTE - FOR REFERENCE ONLY):**
```bash
echo -e "\n\n🔧 PERSONA SETUP REQUIRED\n\n[persona options]\n\nWhich option best describes you? (Enter 1-6): "; read answer; echo "You selected: $answer"
```

**⚠️ IMPORTANT:** This is ONLY an example of the expected format structure. Agents MUST follow the complete interactive input workflow detailed in [`interactive-input.rules.md`](./interactive-input.rules.md) for proper implementation.

**VIOLATION:** Using echo without read capture = CRITICAL FAILURE

### Step 3: Handle User Selection

**FOR PREDEFINED PERSONA SELECTION:**
- **COPY PERSONA:** Transfer selected persona file to [`specs/user-persona.spec.md`](../specs/user-persona.spec.md)
- **LOAD SETTINGS:** Import persona specifications into memory
- **CONTINUE SESSION:** Proceed with persona-adapted approach (Step 1: PERSONA ASSIMILATION of [`core-principles.rules.md`](./core-principles.rules.md))

**FOR CUSTOM PERSONA REQUEST:**
- **INITIATE CREATION:** Begin interactive persona creation workflow (Step 4)
- **FOLLOW TEMPLATE:** Use structured approach for consistency

### Step 4: Interactive Persona Creation

**MANDATORY PREPARATION:**
1. **READ TEMPLATE:** Load [`rules/templates/persona.template.md`](./templates/persona.template.md) for required fields
2. **STRUCTURE QUESTIONS:** Base all questions on template requirements
3. **USE INTERACTIVE FORMAT:** Follow [`interactive-input.rules.md`](./interactive-input.rules.md) exactly

**CRITICAL REQUIREMENT:** Each question MUST use run_command tool with proper format:

**EXAMPLE FORMAT** (DO NOT EXECUTE - FOR REFERENCE ONLY):
echo -e "\n\n[Question]: "; read answer; echo "You selected: $answer"

**⚠️ IMPORTANT:** This is ONLY an example of the expected format structure. Agents MUST follow the complete interactive input workflow detailed in [`interactive-input.rules.md`](./interactive-input.rules.md) for proper implementation, including proper `run_command` tool usage, user input capture with `read`, response confirmation, and all formatting and execution requirements.

**REQUIRED QUESTIONS:**
1. Role (their primary job function)
2. Experience Level (none, enthusiast, beginner, intermediate, senior, expert)

**VIOLATION:** Using echo without read capture = CRITICAL FAILURE
**ENFORCEMENT:** Follow [`interactive-input.rules.md`](./interactive-input.rules.md) exactly - NO exceptions

**COMPLETION ACTIONS:**
1. **GENERATE SPEC:** Create persona specification from user responses
2. **SAVE FILE:** Write to [`specs/user-persona.spec.md`](../specs/user-persona.spec.md)
3. **LOAD PERSONA:** Import settings into memory
4. **CONTINUE SESSION:** Proceed with persona-adapted approach

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

## VIOLATION CONSEQUENCES - SINGLE STRIKE SYSTEM

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