# Interactive Coding Agent Rules

🚨 **MANDATORY: YOU MUST READ ALL REQUIRED RULE FILES** 🚨

**VIOLATION ENFORCEMENT:** All violations of rules in this project are subject to the universal violation enforcement system defined in [rules/violation-enforcement.rules.md](./violation-enforcement.rules.md).

---

## 🚨 ENFORCEMENT REQUIREMENTS

**CRITICAL:** These 4 enforcement requirements take absolute precedence over all other actions:

1. **Reading all required rules takes precedence over any agent action**
   - NO exceptions - rules must be read before ANY file operations, code changes, or workflow triggers
   - Agent MUST halt all activities until rule reading is complete

2. **All required rules must be read before acting on any file**
   - File modifications, creations, deletions FORBIDDEN until rules are read
   - Includes viewing, editing, or analyzing any project files

3. **All required rules must be read before triggering workflows or handling user requests in every new session**
   - Persona setup, spec creation, violation enforcement FORBIDDEN until rules are read
   - User request handling, file operations, code changes FORBIDDEN until rules are read
   - No workflow exceptions - rules reading is the prerequisite for ALL workflows and user interactions
   - After rule reading completion, agent proceeds with Core Agent Workflow from [rules/core-principles.rules.md](./core-principles.rules.md)
   - Ensures comprehensive rule compliance before proceeding with any agent activities

**VIOLATION:** Proceeding without reading rules = CRITICAL VIOLATION requiring immediate session restart

---

## REQUIRED READING

**MANDATORY:** Read ALL rule files in this exact order before any coding session:

1. **[rules/core-principles.rules.md](./core-principles.rules.md)** - Core workflow and principles
2. **[rules/interactive-input.rules.md](./interactive-input.rules.md)** - Interactive input protocols and run_command usage
3. **[rules/file-caching.rules.md](./file-caching.rules.md)** - File caching policies and stale content prevention
4. **[rules/user-persona.rules.md](./user-persona.rules.md)** - User persona management
5. **[rules/spec-management.rules.md](./spec-management.rules.md)** - Specification creation and management (includes legacy code specification workflow)
6. **[rules/spec-reference.rules.md](./spec-reference.rules.md)** - Mandatory spec reference requirements for all generated code
7. **[rules/violation-enforcement.rules.md](./violation-enforcement.rules.md)** - Universal violation enforcement system  

**FAILURE TO READ AND FOLLOW ALL RULES = CRITICAL VIOLATION**

---

## ✅ RULE ACKNOWLEDGMENT PROTOCOL

When asked prompts like “Do you remember the rules?” or “Do you still remember the rules?”, agents must:
- CONFIRM: Acknowledge that the rules were read this session and are being followed
- REFERENCE: Point to this index and the core rule files by name
- OFFER SUMMARY: Ask if the user wants a brief summary of the key rules or specific sections
- ENFORCEMENT: State that violations are governed by rules/violation-enforcement.rules.md

Example response:
- "Yes. I’ve read and I’m following the Interactive Coding Agent rules. The main entry is rules/index.rules.md with Core Principles, Interactive Input, File Caching, Persona, Spec Management, Spec Reference, and Violation Enforcement. Would you like a brief summary of any section?"

---

## 📁 FILE NAMING CONVENTIONS

**RULES FOLDER (`rules/`):**
- **`.rules.md`** - Agent behavior and enforcement rules
- Examples: `interactive-input.rules.md`, `spec-management.rules.md`, `user-persona.rules.md`

**PROJECT SPECIFICATIONS FOLDER (`project-specs/`):**
- **🚨 MANDATORY LOCATION FOR ALL NEW PROJECT SPECIFICATIONS 🚨**
- **`.spec.md`** - Project-specific decisions and technical specifications  
- **Agent-Generated:** All files in this folder are created by coding agents
- **Creation Methods:** 
  - Explicitly requested by user on one-time basis
  - Automatically generated per rule compliance requirements
- **Exception:** `index.spec.md` is REQUIRED and serves as entry point for all specifications
- **CRITICAL:** This is the ONLY folder where agents should create new project specifications
- Examples: `index.spec.md`, `architecture.spec.md`, `ui-components.spec.md`

**GENERAL SPECIFICATIONS FOLDER (`specs/`):**
- **🚨 READ-ONLY: FOR TEMPLATES AND USER PERSONAS ONLY 🚨**
- **`.spec.md`** - General templates and predefined user personas
- **USAGE:** Contains templates and predefined personas that agents READ but DO NOT modify
- **RESTRICTION:** Agents should NEVER create new specifications in this folder
- **PURPOSE:** Houses user persona templates and general specification templates
- Examples: `user-personas/software-engineer.spec.md`, `user-personas/persona-template.spec.md`

**CONVENTION RULES:**
- `.rules` files define HOW agents must behave and enforce standards
- `.spec` files document WHAT decisions have been made or templates to follow
- All rule files in `rules/` folder MUST use `.rules.md` extension
- All specification files MUST use `.spec.md` extension

---

## 📂 DIRECTORY STRUCTURE

**`rules/`** - Agent behavior rules and protocols
- Contains all `.rules.md` files that define agent behavior
- Single source of truth for how agents should operate
- **`templates/`** - Template files for agent-generated content
  - `persona.template.md` - Template for user persona specifications
  - `spec.template.md` - Template for project specification files
  - **ACCESS RULE:** Templates ONLY read during their respective workflows
  - **PERFORMANCE:** Never read template files outside of its respective workflows

**`project-specs/`** - Project-specific specifications
- Contains `.spec.md` files documenting project decisions
- `index.spec.md` serves as the main specification registry

**`specs/`** - General specifications and templates
- Contains reusable specifications and templates
- Subdirectories for organized specification categories (e.g., `user-personas/`)

---

**NO EXCEPTIONS. NO ASSUMPTIONS. FOLLOW THE RULES.**

---

*Single source of truth for maintainability - MUST be followed by all agents.*

---

*Created by [@matscode](https://www.tiktok.com/@matscode) | [LinkedIn](https://www.linkedin.com/in/matscode)*