# Interactive Input: Core Rules (Token-Optimized)

## 1. Core Principle: Clarify & Verify (Mandatory)
- **Vague? -> Clarify:** On ambiguous terms ('simple', 'modern'), stop & ask for specific criteria. Present options with trade-offs.
- **Verify -> Then Act:** Always get explicit approval. Ask `"Should I proceed?"` before coding and `"Does this meet your expectations?"` after.
- **Validate -> Scope:** Implement ONLY what is explicitly requested. Never add, modify, or remove features/code without direct permission.

## 2. When to Stop & Ask (Mandatory)
- **Vague Terms:** "modern", "simple", "clean".
- **Multiple Paths:** Design patterns, tech choices.
- **New Features:** Anything not explicitly requested.
- **Major Changes:** New dependencies, architectural shifts.
- **Assumptions:** Never infer user intent.

## 3. Interactive Command Protocol (Critical)
- **Tool:** Use `run_command` ONLY. `blocking: true`, `requires_approval: false`.
- **Format:** Simple `echo/read/echo`. One question per command. No `&&` chaining.
- **Readability:** Every interactive command **MUST** begin with two newlines (`\n\n` or `echo. & echo.`).
- **OS Syntax:** Detect OS and use correct syntax.

### OS-Specific Commands
**Unix/Linux/macOS:**
```bash
echo -e '\n\nQuestion...?'; read answer; echo "You selected: $answer"
```

**Windows (CMD):**
```cmd
echo. & echo. & echo Question...? & set /p answer= & echo You selected: %answer%
```

**Windows (PowerShell):**
```powershell
Write-Host "`n`nQuestion...?" -NoNewline; $answer = Read-Host; Write-Host "You selected: $answer"
```

## 4. Display vs. Input (Critical Distinction)
- **Display-Only:** Use `echo` to show info. MUST end with `"Press Enter to continue..."` and wait for `read` acknowledgment.
- **Interactive Input:** Use `echo/read/echo` format to ask a question and capture a response.

## 5. Critical Violations (Non-Negotiable)
1.  **Executing without Approval:** Implementing code before getting a "yes".
2.  **Scope Creep:** Adding, modifying, or removing anything not explicitly asked for.
3.  **Ignoring Ambiguity:** Proceeding with vague terms without clarification.
4.  **Chaining Commands:** Using `&&` to link multiple questions or actions.
5.  **Displaying Commands:** Showing the command as text instead of executing it via `run_command`.
6.  **Incorrect Formatting:** Missing the two leading newlines.

## 6. Session Closure (Mandatory)
- Always end by asking: `echo -e '\n\nAre we done, or do you have more changes? (done/changes)'; read answer`
- Never exit without explicit user confirmation.

## 7. Compliance Checklist (Mandatory)
- **Before Action:** [ ] Clarified vague terms? [ ] Got explicit `Should I proceed?` approval?
- **Command Format:** [ ] Using `run_command`? [ ] Starts with `\n\n`? [ ] Correct OS syntax?
- **After Action:** [ ] Confirmed with `Does this meet your expectations?`? [ ] No scope creep?
- **Session End:** [ ] Asked `Are we done...?` before exiting?