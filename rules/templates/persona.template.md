# User Persona Template

## REQUIRED FIELDS

- **Role:** Primary job function (free text)
- **Experience Level:** none, enthusiast, beginner, intermediate, senior, expert
- **Agent Collaboration Style:** Based on experience level adaptations (see user-persona.rules.md)

---

## TEMPLATE

```
# User Persona

## PERSONA IDENTIFICATION

**Role:** [Primary job function - engineer, pm, qa, designer, manager, student, etc.]
**Experience Level:** [Select one: none, enthusiast, beginner, intermediate, senior, expert]

## AGENT COLLABORATION STYLE

**Communication Approach:** [Based on experience level - ENFORCEMENT: see [rules/user-persona.rules.md](../user-persona.rules.md) "Experience Level Adaptations" section]
- **Terminology:** [How technical terms should be handled - reference specific level from rules]
- **Explanations:** [Level of detail required - reference specific level from rules]
- **Decisions:** [How options should be presented - reference specific level from rules]

**VIOLATION ENFORCEMENT:** All agents MUST follow the communication requirements defined in [rules/user-persona.rules.md](../../rules/user-persona.rules.md) → "Experience Level Adaptations" → {experience_level}. Violations are subject to the universal violation enforcement system defined in [rules/violation-enforcement.rules.md](../../rules/violation-enforcement.rules.md).

---

*Note: Changes to this persona configuration require starting a new chat session to take effect.*

---

*User persona specification for adaptive communication*
```

---

## IMPORTANT NOTE FOR USERS

⚠️ **CONFIGURATION CHANGES REQUIRE NEW CHAT SESSION**
Any changes to this user persona configuration will only take effect when you start a new chat session. Most agents loads persona settings at the beginning of each conversation.

---

*Template for user persona specifications with required fields and shell formatting*