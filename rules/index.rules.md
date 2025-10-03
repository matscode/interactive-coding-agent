# Interactive Coding Agent Rules

🚨 **MANDATORY: YOU MUST READ ALL REQUIRED RULE FILES** 🚨

**VIOLATION ENFORCEMENT:** All violations of rules in this project are subject to the universal violation enforcement system defined in [rules/violation-enforcement.rules.md](./violation-enforcement.rules.md).

---

## REQUIRED READING

**AGENTS MUST READ THESE RULE FILES:**

1. **[rules/user-persona.rules.md](./user-persona.rules.md)** - User persona detection and adaptive communication
2. **[rules/core-principles.rules.md](./core-principles.rules.md)** - Core agent behavior and workflow principles
3. **[rules/spec-management.rules.md](./spec-management.rules.md)** - Project specification and decision documentation requirements
4. **[rules/interactive-input.rules.md](./interactive-input.rules.md)** - Interactive terminal input and user clarification protocols
5. **[rules/violation-enforcement.rules.md](./violation-enforcement.rules.md)** - Universal violation enforcement system and compliance protocols  

**FAILURE TO READ AND FOLLOW ALL RULES = CRITICAL VIOLATION**

---

## 📁 FILE NAMING CONVENTIONS

**RULES FOLDER (`rules/`):**
- **`.rules.md`** - Agent behavior and enforcement rules
- Examples: `interactive-input.rules.md`, `spec-management.rules.md`, `user-persona.rules.md`

**PROJECT SPECIFICATIONS FOLDER (`project-specs/`):**
- **`.spec.md`** - Project-specific decisions and technical specifications  
- **Agent-Generated:** All files in this folder are created by coding agents
- **Creation Methods:** 
  - Explicitly requested by user on one-time basis
  - Automatically generated per rule compliance requirements
- **Exception:** `index.spec.md` is REQUIRED and serves as entry point for all specifications
- Examples: `index.spec.md`, `architecture.spec.md`, `ui-components.spec.md`

**GENERAL SPECIFICATIONS FOLDER (`specs/`):**
- **`.spec.md`** - General templates and reusable specifications
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