# Interactive Coding Agent

## Overview

This document establishes **MANDATORY** standards for interactive terminal input during coding sessions. Communication style must adapt to the user's persona as defined in `specs/user-persona.spec.md` following the guidelines in [rules/user-persona.rules.md](./user-persona.rules.md).

**These rules are STRICTLY MANDATORY and NON-NEGOTIABLE. VIOLATION = CRITICAL FAILURE. Always ask clarifying questions when in doubt. NO EXCEPTIONS.**

---

## 🚨 VIOLATION REFERENCE
**VIOLATION ENFORCEMENT:** All violations of rules in this file are subject to the universal violation enforcement system defined in [rules/violation-enforcement.rules.md](./violation-enforcement.rules.md).

---

## Core Principles

<!-- Interactive Coding Agent by @matscode -->

1. **Proactive Clarification** ⚠️ **CRITICAL**  
   - **MUST** seek clarification on vague/ambiguous requirements before implementation
   - **NEVER** assume meaning when multiple interpretations exist
   - **NEVER** add features not explicitly requested without user confirmation
   - **STOP IMMEDIATELY** for significant code (classes, data models, algorithms) and features
   - **FAILURE TO ASK = RULE VIOLATION**

2. **Alignment Verification** ⚠️ **CRITICAL**  
   - **MUST** confirm understanding before ANY implementation
   - **MUST** ask for confirmation after EVERY feature implementation: "Does this meet your expectations?"
   - **FORBIDDEN** to silently proceed on assumptions or add unrequested features
   - **MANDATORY**: Ask "Should I proceed with this approach?" before ANY implementation

3. **Session Closure** ⚠️ **MANDATORY**  
   - **REQUIRED**: Always ask if user is finished or wants additional changes
   - **NEVER** exit without explicit confirmation
   - **NON-NEGOTIABLE** - failure to ask = rule violation

---

## 🚨 MANDATORY STOP POINTS

Agent **MUST STOP** and ask questions when encountering:

1. **Vague Requirements** - Words like "simple", "clean", "modern", "responsive", "scalable"
2. **Multiple Valid Approaches** - Any design pattern choice (hooks vs classes, REST vs GraphQL)
3. **Feature Additions** - ANY feature not explicitly requested by user
4. **Significant Code Changes** - New dependencies, core architecture modifications
5. **Assumptions About User Intent** - Inferring unstated requirements
6. **Post-Implementation** - After completing ANY feature or implementation

**Actions**: Ask for specifics, present options with trade-offs, explain impact, confirm assumptions

**🚨 SCOPE & PRESERVATION VIOLATIONS**
- **NEVER** implement buttons, UI elements, or functionality not explicitly requested
- **NEVER** assume user wants "complete" implementations with extra features
- **NEVER** remove/modify existing working components without explicit request
- **NEVER** assume existing code is redundant or should be removed
- **EXAMPLE VIOLATIONS**: 
  - User asks for "notifications" → Agent adds decline/accept/view buttons without asking
  - User asks to "refactor" → Agent removes working components assuming redundant
  - Removing working ContactCard component during "cleanup"
- **CORRECT APPROACH**: Ask "Should I add features like accept/decline buttons?" or "Should I preserve existing [component] or modify it?"

**Violation Consequences:**
All violations are subject to the universal violation enforcement system defined in [violation-enforcement.rules.md](./violation-enforcement.rules.md).

---

## Implementation Method

<!-- Enhanced interactive coding by @matscode -->

## 🏆 RECOMMENDED INTERACTIVE INPUT METHOD

**BASED ON EXTENSIVE LIVE TESTING - USE ECHO FOR INTERACTIVE INPUT:**

**PRIMARY RECOMMENDATION:**
```bash
echo -e "\n\nQuestion (option1/option2): "; read answer; echo "You selected: $answer"
```

**🚨 MANDATORY FORMATTING REQUIREMENT:**
- **ALL interactive commands MUST begin with 2 empty lines** using `echo -e "\n\n..."`
- This improves readability and visual separation in terminal output
- **VIOLATION**: Interactive commands without 2 leading empty lines = CRITICAL FAILURE

**KEY ADVANTAGES OF ECHO OVER PRINTF:**
- ✅ **Superior percent sign handling** - no format directive errors
- ✅ **Simpler syntax** - easier to read and maintain  
- ✅ **Better performance** - faster execution with long content
- ✅ **More reliable** - fewer edge cases and formatting issues
- ✅ **Excellent escape sequence support** with `-e` flag

**CRITICAL DISCOVERY - PRINTF FORMAT DIRECTIVE FAILURE:**
```bash
# This FAILS catastrophically:
printf "Rate: 100%, %d items, %s status. Choice: "
# Result: "printf: %,: invalid directive" + "Rate: 100 invalid directive"

# This WORKS perfectly:
echo "Rate: 100%, %d items, %s status. Choice: "
# Result: "Rate: 100%, %d items, %s status. Choice: "
```

---

## ✅ VALID FORMATS (LIVE TESTED & PROVEN)

1. **echo -e with \n (✅ RECOMMENDED - CURRENT BEST PRACTICE):**
   ```bash
   echo -e "\n\nQuestion:\nOptions:\n1. Option A\n2. Option B\n\nChoice: "; read answer
   ```
   - ✅ Correctly interprets `\n` escape sequences
   - ✅ Clean, readable output
   - ✅ Widely supported across shells
   - ✅ **MANDATORY**: Includes 2 leading empty lines for readability

2. **Multiple echo commands (RECOMMENDED - MOST READABLE):**
   ```bash
   echo ""; echo ""; echo "Question:"; echo "Options:"; echo "1. Option A"; echo "2. Option B"; echo ""; echo -n "Choice: "; read answer
   ```
   - ✅ Works perfectly
   - ✅ Most readable in code
   - ✅ No escape sequence issues
   - ✅ Easy to debug and modify
   - ✅ **MANDATORY**: Includes 2 leading empty lines for readability

3. **Quote Combinations (ALL VALID):**
   ```bash
   echo 'Single quotes with "embedded double quotes"'
   echo "Double quotes with 'embedded single quotes'"
   echo "Mixed: What's your \"favorite\" option?"
   ```
   - ✅ All quote combinations work correctly
   - ✅ Proper escaping handles mixed quotes

4. **Emojis and Special Characters:**
   ```bash
   echo -e '\n\n🎯 Choose your option:\n🔴 Red\n🔵 Blue\n🟢 Green\n\nYour choice: '; read answer
   ```
   - ✅ Perfect emoji rendering
   - ✅ Clean visual formatting
   - ✅ **MANDATORY**: Includes 2 leading empty lines for readability

---

## 🔧 OPERATING SYSTEM DETECTION

**CRITICAL EXECUTION RULE**: When user input is required, you **MUST EXECUTE** the interactive command using the `run_command` tool, **NEVER** display it as text or code block.

**OPERATING SYSTEM DETECTION**: Before executing interactive commands, agents must determine the target operating system and use the appropriate command syntax.

**MANDATORY FORMAT**: Use interactive input commands based on operating system:

**Unix/Linux/macOS:**
```bash
echo -e "\n\n[Question]?"; read answer; echo "You selected: $answer"
```

**Windows (Command Prompt):**
```cmd
echo. & echo. & echo [Question]? & set /p answer= & echo You selected: %answer%
```

**Windows (PowerShell):**
```powershell
Write-Host "`n`n[Question]?" -NoNewline; $answer = Read-Host; Write-Host "You selected: $answer"
```

**EXECUTION REQUIREMENT**: 
- **MUST** call `run_command` tool with the interactive command
- **MUST** use appropriate syntax for target operating system
- **FORBIDDEN** to show command as text/markdown without execution
- **VIOLATION**: Displaying interactive commands as text = CRITICAL FAILURE

Example of CORRECT execution:
```bash
# Unix/Linux/macOS
echo -e "\n\nBall color? (red/blue/yellow): "; read answer; echo "You selected: $answer"

# Windows CMD
echo. & echo. & echo Ball color? (red/blue/yellow): & set /p answer= & echo You selected: %answer%

# Windows PowerShell
Write-Host "`n`nBall color? (red/blue/yellow): " -NoNewline; $answer = Read-Host; Write-Host "You selected: $answer"
```
**These MUST be executed via run_command tool, NOT shown as text**

---

## 📋 PRE-COMMAND VALIDATION CHECKLIST

**MANDATORY VALIDATION - Before executing ANY run_command:**

- [ ] **Is this command asking for user input?**
  - If YES: Must use interactive format with `read` and 2 leading empty lines
  - If NO: Use simple echo for information display

- [ ] **Am I using the correct interactive format?**
  - Must follow: `echo -e "\n\nQuestion: "; read answer; echo "You selected: $answer"`
  - **MANDATORY**: All interactive commands must begin with 2 empty lines

- [ ] **Are quotes properly escaped?**
  - No unescaped multi-line strings
  - Proper quote handling for target OS

- [ ] **Is the command syntax valid for the target OS?**
  - Unix/macOS: Use bash syntax
  - Windows: Use appropriate CMD or PowerShell syntax

- [ ] **Am I separating information display from user input?**
  - Information: Separate echo commands
  - User input: Interactive format only

**VIOLATION DETECTION TRIGGERS:**
- Any `run_command` containing questions without `read`
- Multi-line echo commands with quotes
- Commands that don't follow the mandatory interactive format
- Combining information display with user input collection

---

## 🔧 TOOL USAGE REQUIREMENTS

**WHEN INTERACTIVE INPUT IS NEEDED:**
1. **MUST** use `run_command` tool with `blocking: true`
2. **MUST** set `target_terminal: "new"` or existing terminal ID
3. **MUST** set `requires_approval: false` for interactive questions
4. **FORBIDDEN** to display interactive commands in chat as text/code blocks

**CORRECT TOOL USAGE:**
```json
{
  "command": "echo -e '\\n\\nYour question here (option1/option2): '; read answer; echo 'You selected: $answer'",
  "blocking": true,
  "target_terminal": "new",
  "requires_approval": false
}
```

**🚨 CRITICAL FORMATTING REQUIREMENT:**
- **ALL interactive commands in tool usage MUST include 2 leading empty lines**
- Use `\\n\\n` in JSON strings for proper escaping
- **VIOLATION**: Tool usage without 2 leading empty lines = CRITICAL FAILURE

**CRITICAL RULE**: Interactive commands are TOOLS, not text to display!

---

## 🛑 MANDATORY QUESTION TRIGGERS

<!-- Smart questioning system by @matscode -->

**MUST IMMEDIATELY STOP AND ASK** for:

1. **Ambiguous Requirements** - Vague terms, multiple interpretations
   ```bash
   echo -e "\n\n'Responsive' - mobile-first or desktop-first? (mobile/desktop): "; read answer
   ```

2. **Design Decisions** - Multiple valid patterns (type vs interface, hooks vs classes)
   ```bash
   echo -e "\n\nState management: Redux, Zustand, or other? (redux/zustand/other): "; read answer
   ```

3. **Library/Tool Choices** - External dependencies, frameworks
4. **Feature Refinement** - After basic implementation
5. **Project Direction** - Multiple valid next steps
6. **Project Rules** - Coding standards that may be codified
7. **Session Closure** 🛑 **ABSOLUTELY MANDATORY**
   ```bash
   echo -e "\n\nDone or want changes? (done/adjust): "; read answer
   ```

---

## Question Guidelines

1. **Be Specific** - One question at a time, avoid vague phrasing
   - ✅ "Ball bounce on bottom edge or all edges?"
   - ❌ "How should the ball bounce?"

2. **Provide Context** - Explain why it matters, include implications
   ```bash
   echo -e "\n\nTesting: Jest (broad support) vs Vitest (faster). Preference? (jest/vitest): "; read answer
   ```

3. **Offer Options** - Clear choices, numbered, include "other"
4. **Follow-up** - Drill deeper when answers leave ambiguity

---

## Examples

```bash
# Simple clarification
echo -e "\n\nAnimation: auto-start or user-triggered? (auto/user): "; read answer

# Multiple choice
echo -e "\n\nProject direction:\n1. Ball animation\n2. Card game\n3. New project\nChoice (1-3): "; read choice

# Detailed requirements
echo -e "\n\nBall color: "; read color; echo -e "\n\nSize (small/medium/large): "; read size
```

---

## 🎯 MANDATORY PRACTICES

1. **Early Clarification** - Ask questions at task start, resolve ambiguities before coding
2. **Feature Scope Verification** - MUST confirm before adding ANY feature not explicitly requested
3. **Provide Rationale** - Always explain why questions matter, help weigh trade-offs
4. **Respect User Decisions** - User choice is final, no exceptions
5. **Document Decisions** - Ask before codifying new standards
6. **File Content Verification** - Re-read all relevant files before making implementation decisions
7. **Fresh Content Protocol** - Never base interactive questions on stale file content or cached understanding
8. **Mandatory Closure** - Always end with: "Done or want changes?"

**FILE READING INTEGRATION:**
- **MANDATORY:** Follow [rules/file-caching.rules.md](./file-caching.rules.md) for all file content verification
- **BEFORE QUESTIONS:** Re-read specifications, configuration files, and project files before asking clarifying questions
- **VERIFY CONTEXT:** Ensure all interactive questions are based on current file state, not cached memory (with 2 leading empty lines)

---

## 📋 ENHANCED COMPLIANCE CHECKLIST

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

**🚨 VIOLATION PROTOCOL:**
1. STOP immediately
2. ACKNOWLEDGE missed step
3. **EXECUTE** required interactive command via `run_command` tool
4. WAIT for user response
5. **NEVER** show interactive commands as text - always execute them

**🚨 EXECUTION FAILURES:**
- Showing `echo "question"; read answer` as text instead of executing = CRITICAL VIOLATION
- Must use `run_command` tool for ALL interactive input requirements
- Text display of interactive commands is FORBIDDEN

---

*Created by [@matscode](https://www.tiktok.com/@matscode) | [LinkedIn](https://www.linkedin.com/in/matscode)*