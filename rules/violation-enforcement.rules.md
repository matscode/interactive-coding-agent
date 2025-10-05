# Violation Enforcement Rules

**MANDATORY: ALL AGENTS MUST FOLLOW THESE VIOLATION ENFORCEMENT PROTOCOLS**

---

## 🚨 UNIVERSAL VIOLATION ENFORCEMENT SYSTEM

**CRITICAL RULE:** This file establishes the universal violation enforcement system that applies to ALL rule files in this project. Every `.rules.md` file MUST reference this enforcement system.

---

## VIOLATION CLASSIFICATION SYSTEM

### CRITICAL VIOLATIONS (Immediate Correction Required)
**Stop immediately, acknowledge violation, and implement correction:**

1. **Implementation without user approval** → STOP immediately, acknowledge violation, restart with proper approval *(See: [core-principles.rules.md](./core-principles.rules.md))*
2. **Adding unrequested features or scope creep** → STOP immediately, acknowledge violation, rollback changes *(See: [core-principles.rules.md](./core-principles.rules.md))*
3. **Proceeding without clarification on ambiguous requirements** → STOP immediately, acknowledge assumption error *(See: [interactive-input.rules.md](./interactive-input.rules.md))*
4. **Implementing without reading existing specifications** → STOP immediately, acknowledge spec violation *(See: [spec-management.rules.md](./spec-management.rules.md))*
5. **Not re-reading specifications immediately before implementation** → STOP immediately, acknowledge timing violation *(See: [spec-management.rules.md](./spec-management.rules.md))*
6. **Displaying interactive commands as text instead of executing** → STOP immediately, acknowledge execution failure *(See: [interactive-input.rules.md](./interactive-input.rules.md))*
7. **Making architectural decisions without creating specifications** → STOP immediately, acknowledge documentation failure *(See: [spec-management.rules.md](./spec-management.rules.md))*
8. **Generating code files without mandatory spec reference comments** → STOP immediately, acknowledge spec reference violation *(See: [spec-reference.rules.md](./spec-reference.rules.md))*
9. **Modifying legacy code without creating and approving specifications** → STOP immediately, acknowledge legacy code violation *(See: [spec-management.rules.md](./spec-management.rules.md) - Legacy Code Workflow)*
10. **Violating AGENT COLLABORATION STYLE requirements** → STOP immediately, acknowledge communication violation, restart with proper persona adherence *(See: [user-persona.rules.md](./user-persona.rules.md))*
11. **Operating on stale/cached file content without re-reading** → STOP immediately, acknowledge file content staleness violation *(See: [file-caching.rules.md](./file-caching.rules.md) - Comprehensive file caching policies and stale content prevention)*
12. **Shell syntax errors in interactive commands** → STOP immediately, acknowledge syntax violation, implement correct shell format *(See: [interactive-input.rules.md](./interactive-input.rules.md) - Shell Syntax Guidelines)*
13. **Combining information display with user input in single command** → STOP immediately, acknowledge separation violation, use separate commands *(See: [interactive-input.rules.md](./interactive-input.rules.md) - Separation of Concerns)*
14. **Making code changes without user consent** → STOP immediately, acknowledge consent violation, implement proper approval protocol *(See: [core-principles.rules.md](./core-principles.rules.md) - User Consent Requirements)*
15. **Missing mandatory stop points** → STOP immediately, acknowledge missed step, execute required question *(See: [interactive-input.rules.md](./interactive-input.rules.md))*
16. **Skipping session closure protocol** → STOP immediately, execute mandatory closure question *(See: [interactive-input.rules.md](./interactive-input.rules.md))*
17. **Failing to ask "Does this meet expectations?"** → STOP immediately, ask retroactively *(See: [core-principles.rules.md](./core-principles.rules.md))*
18. **Not asking about decision documentation** → STOP immediately, ask: "Should this decision be documented in the relevant spec file for future reference?" *(See: [spec-management.rules.md](./spec-management.rules.md))*
19. **Removing working components without permission** → STOP immediately, acknowledge preservation violation *(See: [core-principles.rules.md](./core-principles.rules.md))*
20. **Ignoring established patterns without justification** → STOP immediately, acknowledge pattern violation *(See: [core-principles.rules.md](./core-principles.rules.md))*
21. **Skipping specification index updates** → STOP immediately, update index file *(See: [spec-management.rules.md](./spec-management.rules.md))*
22. **Using incorrect comment syntax for spec references** → STOP immediately, research and correct syntax *(See: [spec-reference.rules.md](./spec-reference.rules.md))*
23. **Missing spec references in existing code modifications** → STOP immediately, add required references *(See: [spec-reference.rules.md](./spec-reference.rules.md))*
24. **Proceeding without user approval of generated specifications** → STOP immediately, request approval *(See: [spec-management.rules.md](./spec-management.rules.md))*
25. **Not following AGENT COLLABORATION STYLE communication requirements** → STOP immediately, acknowledge persona violation, adjust communication approach *(See: [user-persona.rules.md](./user-persona.rules.md))*
26. **Using incorrect shell command format for user input** → STOP immediately, acknowledge format violation, use correct interactive format *(See: [interactive-input.rules.md](./interactive-input.rules.md) - Shell Syntax Guidelines)*
27. **Failing to validate shell commands before execution** → STOP immediately, acknowledge validation failure, implement pre-command validation *(See: [interactive-input.rules.md](./interactive-input.rules.md) - Pre-Command Validation Checklist)*
28. **Making assumptions about file content without verification** → STOP immediately, acknowledge assumption violation, re-read files *(See: [file-caching.rules.md](./file-caching.rules.md) - Point-of-Use Enforcement)*
29. **Missing descriptive comments in code** → STOP immediately, acknowledge, add proper documentation *(See: [core-principles.rules.md](./core-principles.rules.md))*
30. **Inconsistent naming conventions** → STOP immediately, acknowledge, standardize naming *(See: [core-principles.rules.md](./core-principles.rules.md))*
31. **Missing error handling** → STOP immediately, acknowledge, implement proper error handling *(See: [core-principles.rules.md](./core-principles.rules.md))*
32. **Incomplete test coverage** → STOP immediately, acknowledge, add necessary tests *(See: [core-principles.rules.md](./core-principles.rules.md))*
33. **Inconsistent spec reference formatting** → STOP immediately, acknowledge, standardize format *(See: [spec-reference.rules.md](./spec-reference.rules.md))*
34. **Missing section names in spec references** → STOP immediately, acknowledge, add specific section references *(See: [spec-reference.rules.md](./spec-reference.rules.md))*
35. **Incomplete analysis of legacy code** → STOP immediately, acknowledge, perform thorough code analysis *(See: [spec-management.rules.md](./spec-management.rules.md) - Legacy Code Workflow)*
36. **Using inappropriate communication style for user experience level** → STOP immediately, acknowledge, adjust to proper persona requirements *(See: [user-persona.rules.md](./user-persona.rules.md))*

---

## VIOLATION RESPONSE PROTOCOL

### IMMEDIATE RESPONSE REQUIREMENTS

**When ANY violation occurs:**

1. **STOP IMMEDIATELY** - Halt all current activities
2. **ACKNOWLEDGE** - Explicitly state the violation that occurred
3. **CORRECT** - Implement the required correction immediately
4. **CONTINUE** - Proceed only after correction is complete

### VIOLATION DETECTION

**Agents must actively monitor for violations:**
- Before each action, verify compliance with all applicable rules
- During implementation, continuously check for rule adherence
- After completion, validate that all requirements were met

### ESCALATION PROTOCOL

**For repeated violations:**
- First violation: Immediate correction as specified above
- Second violation: Acknowledge pattern, implement additional safeguards
- Third violation: Request user guidance on rule enforcement preferences

### PREVENTION STRATEGIES

**Proactive compliance measures:**
- Review applicable rules before starting any task
- Use checklists for complex workflows
- Verify file content freshness before modifications
- Confirm user approval before implementation
- Document decisions for future reference

---

## 📊 ESCALATION MATRIX FOR REPEATED VIOLATIONS

### First Violation
- **ACTION:** Acknowledge and correct immediately
- **REQUIREMENT:** Follow standard violation response protocol
- **CONTINUATION:** Session continues with heightened awareness

### Second Violation (Same Type)
- **ACTION:** Acknowledge, correct, and implement additional verification steps
- **REQUIREMENT:** Review entire relevant rule file before continuing
- **CONTINUATION:** Session continues with mandatory checkpoints

### Third Violation (Same Type)
- **ACTION:** Session restart required with full rule review
- **REQUIREMENT:** Re-read ALL applicable rule files
- **CONTINUATION:** Fresh session start with enhanced compliance monitoring

### Persistent Violations (4+ Same Type)
- **ACTION:** Escalate to user for rule clarification or modification
- **REQUIREMENT:** User intervention required
- **CONTINUATION:** Cannot proceed without user guidance

---

## 🔍 VIOLATION DETECTION TRIGGERS

**AGENTS MUST SELF-MONITOR FOR THESE VIOLATION INDICATORS:**

### Pre-Implementation Checks
- [ ] Have I read all relevant specifications?
- [ ] Have I asked for clarification on ambiguous requirements?
- [ ] Have I received explicit user approval?
- [ ] Am I following established patterns?
- [ ] Am I implementing only what was requested?
- [ ] Do I know the correct comment syntax for the target language?
- [ ] Have I identified which spec file(s) will guide this implementation?
- [ ] If modifying existing code, have I checked for existing spec references?
- [ ] If no spec references exist, am I prepared to create specifications first?
- [ ] Have I checked file timestamps for recent changes?
- [ ] Have I re-read all files I plan to modify?
- [ ] Have I validated my shell command syntax before execution?
- [ ] Am I separating information display from user input properly?
- [ ] Have I obtained explicit user consent for all planned changes?

### During Implementation Checks
- [ ] Am I adding any unrequested features?
- [ ] Am I removing any existing functionality?
- [ ] Am I following the approved specification exactly?
- [ ] Am I maintaining consistency with existing code?
- [ ] Have I added spec reference comments to all generated files?
- [ ] Are my spec references using the correct comment syntax?
- [ ] Do my spec references include specific section names?
- [ ] If I created new specifications, have I received user approval?
- [ ] Am I using correct shell syntax for any interactive commands?
- [ ] Am I keeping information display separate from user input?
- [ ] Have I verified file content matches my expectations before modifying?
- [ ] Am I staying within the scope of user-approved changes?

### Post-Implementation Checks
- [ ] Have I asked "Does this meet your expectations?"
- [ ] Have I updated all relevant documentation?
- [ ] Have I followed the session closure protocol?
- [ ] Have I verified all requirements were met?
- [ ] Are all generated files properly tagged with spec references?
- [ ] Have I updated existing code with appropriate spec references?

---

## 🚨 ZERO TOLERANCE ENFORCEMENT POLICY

**NON-NEGOTIABLE PRINCIPLES:**

1. **NO EXCEPTIONS** for any violations - all violations must be acknowledged and corrected
2. **USER SAFETY AND CONSENT** are paramount - never proceed without explicit approval
3. **RULE ADHERENCE** is non-negotiable - rules exist for user protection and project quality
4. **TRANSPARENCY** is required - all violations must be explicitly acknowledged to the user
5. **CONTINUOUS IMPROVEMENT** - each violation is a learning opportunity for better compliance

**ENFORCEMENT AUTHORITY:**
- Every agent has the authority and responsibility to enforce these rules
- Users have the authority to modify or override these rules as needed
- Rule violations by other agents must be reported and corrected
- Self-reporting of violations is encouraged and demonstrates good faith compliance

---

## 📋 COMPLIANCE VERIFICATION CHECKLIST

**MANDATORY VERIFICATION BEFORE ANY CRITICAL ACTION:**

### Before Starting Implementation
- [ ] All relevant specifications read and understood?
- [ ] User requirements clarified and confirmed?
- [ ] Explicit approval received for implementation approach?
- [ ] Established patterns identified and will be followed?
- [ ] Target language comment syntax identified for spec references?
- [ ] Relevant spec files identified for reference comments?
- [ ] Legacy code analysis completed if modifying existing files?
- [ ] User approval obtained for any newly created specifications?

### During Implementation
- [ ] Staying within approved scope?
- [ ] Following specifications exactly?
- [ ] Not adding unrequested features?
- [ ] Maintaining existing functionality?
- [ ] Adding spec reference comments to all generated files?
- [ ] Using correct comment syntax for spec references?

### After Implementation
- [ ] User satisfaction confirmed?
- [ ] All documentation updated?
- [ ] Session closure protocol followed?
- [ ] No violations occurred during implementation?
- [ ] All generated files contain proper spec reference comments?
- [ ] Existing modified files updated with appropriate spec references?

---

## 🔗 CROSS-REFERENCE REQUIREMENTS

**MANDATORY FOR ALL RULE FILES:**

Every `.rules.md` file in this project MUST include a reference to this violation enforcement system using this exact format:

```markdown
**VIOLATION ENFORCEMENT:** All violations of rules in this file are subject to the universal violation enforcement system defined in [rules/violation-enforcement.rules.md](./violation-enforcement.rules.md).
```

**PLACEMENT REQUIREMENT:** This reference must be placed in a prominent location within each rule file, preferably near the beginning or in a dedicated enforcement section.

---

*Created by [@matscode](https://www.tiktok.com/@matscode) | [LinkedIn](https://www.linkedin.com/in/matscode)*