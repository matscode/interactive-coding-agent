# Interactive Input Rules

**MANDATORY: ALL AGENTS MUST FOLLOW INTERACTIVE INPUT PROTOCOLS**

**VIOLATION ENFORCEMENT:** All violations of rules in this file are subject to the universal violation enforcement system defined in [rules/violation-enforcement.rules.md](./violation-enforcement.rules.md).

---

## OVERVIEW

This document establishes **MANDATORY** standards for interactive terminal input during coding sessions. Communication style and complexity should adapt based on user persona (see `rules/user-persona.rules.md` for persona detection and adaptation guidelines).

**These rules are STRICTLY MANDATORY and NON-NEGOTIABLE. VIOLATION = CRITICAL FAILURE. Always ask clarifying questions when in doubt. NO EXCEPTIONS.**

---

## CORE INTERACTIVE PRINCIPLES

1. **Proactive Clarification** **CRITICAL**  
   - **MUST** seek clarification on vague/ambiguous requirements before implementation
   - **NEVER** assume meaning when multiple interpretations exist
   - **NEVER** add features not explicitly requested without user confirmation
   - **STOP IMMEDIATELY** for significant code (classes, data models, algorithms) and features
   - **FAILURE TO ASK = RULE VIOLATION**

2. **Alignment Verification** **CRITICAL**  
   - **MUST** confirm understanding before ANY implementation
   - **MUST** ask for confirmation after EVERY feature implementation: "Does this meet your expectations?"
   - **FORBIDDEN** to silently proceed on assumptions or add unrequested features
   - **MANDATORY**: Ask "Should I proceed with this approach?" before ANY implementation

3. **Session Closure** **MANDATORY**  
   - **REQUIRED**: Always ask if user is finished or wants additional changes
   - **NEVER** exit without explicit confirmation
   - **NON-NEGOTIABLE** - failure to ask = rule violation

---

## MANDATORY STOP POINTS

Agent **MUST STOP** and ask questions when encountering:

1. **Vague Requirements** - Words like "simple", "clean", "modern", "responsive", "scalable"
2. **Multiple Valid Approaches** - Any design pattern choice (hooks vs classes, REST vs GraphQL)
3. **Feature Additions** - ANY feature not explicitly requested by user
4. **Significant Code Changes** - New dependencies, core architecture modifications
5. **Assumptions About User Intent** - Inferring unstated requirements
6. **Post-Implementation** - After completing ANY feature or implementation

**Actions**: Ask for specifics, present options with trade-offs, explain impact, confirm assumptions

**SCOPE & PRESERVATION VIOLATIONS**
- **NEVER** implement buttons, UI elements, or functionality not explicitly requested
- **NEVER** assume user wants "complete" implementations with extra features
- **NEVER** remove/modify existing working components without explicit request
- **NEVER** assume existing code is redundant or should be removed
- **EXAMPLE VIOLATIONS**: 
  - User asks for "notifications" → Agent adds decline/accept/view buttons without asking
  - User asks to "refactor" → Agent removes working components assuming redundant
  - Removing working ContactCard component during "cleanup"
- **CORRECT APPROACH**: Ask "Should I add features like accept/decline buttons?" or "Should I preserve existing [component] or modify it?"

**Violation Consequences**: Acknowledge missed opportunity → ask retroactively → restart session if repeated → rollback if critical

---

## IMPLEMENTATION METHOD

**CRITICAL EXECUTION RULE**: When user input is required, you **MUST EXECUTE** the interactive command using the `run_command` tool, **NEVER** display it as text or code block.

**OPERATING SYSTEM DETECTION**: Before executing interactive commands, agents must determine the target operating system and use the appropriate command syntax.

**MANDATORY FORMAT**: Use interactive input commands based on operating system:

**Unix/Linux/macOS:**
```bash
echo "[Question]?"; read answer; echo "You selected: $answer"
```

**Windows (Command Prompt):**
```cmd
echo [Question]? & set /p answer= & echo You selected: %answer%
```

**Windows (PowerShell):**
```powershell
Write-Host "[Question]?" -NoNewline; $answer = Read-Host; Write-Host "You selected: $answer"
```

**EXECUTION REQUIREMENT**: 
- **MUST** call `run_command` tool with the interactive command
- **MUST** use appropriate syntax for target operating system
- **FORBIDDEN** to show command as text/markdown without execution
- **VIOLATION**: Displaying interactive commands as text = CRITICAL FAILURE

Example of CORRECT execution:
```bash
# Unix/Linux/macOS
echo "Ball color? (red/blue/yellow): "; read answer; echo "You selected: $answer"

# Windows CMD
echo Ball color? (red/blue/yellow): & set /p answer= & echo You selected: %answer%

# Windows PowerShell
Write-Host "Ball color? (red/blue/yellow): " -NoNewline; $answer = Read-Host; Write-Host "You selected: $answer"
```
**These MUST be executed via run_command tool, NOT shown as text**

---

## TOOL USAGE REQUIREMENTS

**QUESTION EXECUTION PROTOCOL:**
1. **MUST** use `run_command` tool with `blocking: true`
2. **MUST** set `target_terminal: "new"` or existing terminal ID
3. **MUST** set `requires_approval: false` for interactive questions
4. **FORBIDDEN** to display interactive commands in chat as text/code blocks

**CORRECT TOOL USAGE:**
```json
{
  "command": "echo 'Your question here (option1/option2): '; read answer; echo 'You selected: $answer'",
  "blocking": true,
  "target_terminal": "new",
  "requires_approval": false
}
```

**CRITICAL RULE**: Interactive commands are TOOLS, not text to display!

---

## MANDATORY QUESTION TRIGGERS

**MUST IMMEDIATELY STOP AND ASK** for:

1. **Ambiguous Requirements** - Vague terms, multiple interpretations
   ```bash
   echo "'Responsive' - mobile-first or desktop-first? (mobile/desktop): "; read answer
   ```

2. **Design Decisions** - Multiple valid patterns (type vs interface, hooks vs classes)
   ```bash
   echo "State management: Redux, Zustand, or other? (redux/zustand/other): "; read answer
   ```

3. **Library/Tool Choices** - External dependencies, frameworks
4. **Feature Refinement** - After basic implementation
5. **Project Direction** - Multiple valid next steps
6. **Project Rules** - Coding standards that may be codified
7. **Session Closure** **ABSOLUTELY MANDATORY**
   ```bash
   echo "Done or want changes? (done/adjust): "; read answer
   ```

---

## Question Guidelines

1. **Be Specific** - One question at a time, avoid vague phrasing
   - "Ball bounce on bottom edge or all edges?"
   - ❌ "How should the ball bounce?"

2. **Provide Context** - Explain why it matters, include implications
   ```bash
   echo "Testing: Jest (broad support) vs Vitest (faster). Preference? (jest/vitest): "; read answer
   ```

3. **Offer Options** - Clear choices, numbered, include "other"
4. **Follow-up** - Drill deeper when answers leave ambiguity

---

## Examples

```bash
# Simple clarification
echo "Animation: auto-start or user-triggered? (auto/user): "; read answer

# Multiple choice
echo "Project direction:\n1. Ball animation\n2. Card game\n3. New project\nChoice (1-3): "; read choice

# Detailed requirements
echo "Ball color: "; read color; echo "Size (small/medium/large): "; read size
```

---

## MANDATORY PRACTICES

1. **Early Clarification** - Ask questions at task start, resolve ambiguities before coding
2. **Feature Scope Verification** - MUST confirm before adding ANY feature not explicitly requested
5. **Provide Rationale** - Always explain why questions matter, help weigh trade-offs
6. **Respect User Decisions** - User choice is final, no exceptions
7. **Document Decisions** - Ask before codifying new standards
8. **Mandatory Closure** - Always end with: "Done or want changes?"

---

## COMPLIANCE CHECKLIST

**Before ANY implementation:**
- [ ] Clarified vague terms?
- [ ] Presented options for multiple approaches?
- [ ] Explained implications and trade-offs?
- [ ] Asked "Should I proceed?" before implementation?
- [ ] Confirmed feature scope - only implementing what's explicitly requested?
- [ ] Avoided adding unrequested buttons, UI elements, or functionality?
- [ ] Confirmed assumptions?
- [ ] Respected user preferences?
- [ ] Verified no scope creep?
- [ ] Asked for explicit approval?

**After EVERY implementation:**
- [ ] Asked "Does this meet your expectations?"
- [ ] Confirmed no unrequested features were added?
- [ ] Validated implementation scope matches user request?
- [ ] Asked if user wants modifications?

**REFACTORING-SPECIFIC CHECKLIST:**
- [ ] Preserved ALL original functionality?
- [ ] Maintained existing component behavior?
- [ ] Avoided removing working features?
- [ ] Asked before changing component structure?
- [ ] Confirmed refactoring scope with user?

**At session end:**
- [ ] Asked if user wants changes?
- [ ] Verified all requirements were met?

**VIOLATION PROTOCOL:**
1. STOP immediately
2. ACKNOWLEDGE missed step
3. **EXECUTE** required interactive command via `run_command` tool
4. WAIT for user response
5. **NEVER** show interactive commands as text - always execute them

**EXECUTION FAILURES:**
- Showing `echo "question"; read answer` as text instead of executing = CRITICAL VIOLATION
- Must use `run_command` tool for ALL interactive input requirements
- Text display of interactive commands is FORBIDDEN

---

*Created by [@matscode](https://www.tiktok.com/@matscode) | [LinkedIn](https://www.linkedin.com/in/matscode)*