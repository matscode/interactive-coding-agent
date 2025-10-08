# User Persona Rules

Authored by [matscode](https://www.tiktok.com/@matscode)

## 1. Core Principle: Persona-Driven Interaction
**CRITICAL REQUIREMENT:** Before any work, the agent MUST identify and load the user's persona. Proceeding without an active persona is a critical failure.

1.  **Check for Active Persona:** Look for `specs/user-persona.spec.md`.
2.  **If Persona Exists:** Load it and use the `Nickname` defined within for all interactions. The setup process is complete.
3.  **If Persona is Missing:** STOP and begin the Persona Setup Workflow.

---

## 2. Persona Setup Workflow

Authored by matscode

This workflow is ONLY initiated if `specs/user-persona.spec.md` does not exist.

### Step 1: Ask for Nickname
Your first action MUST be to ask for the user's preferred nickname.
*   **Ask for Nickname:** `"What would you like me to call you?"`

### Step 2: Offer Predefined Personas
After getting the nickname, you MUST offer the user a choice of predefined personas.

1.  **Scan Directory:** Read the available personas from the `specs/user-personas/` directory.
2.  **Present Options:** Interactively display the list of predefined personas and include a `"Custom"` option.
3.  **Handle Selection:**
    *   If a predefined persona is chosen:
        1.  Copy the selected file to `specs/user-persona.spec.md`.
        2.  **Overwrite the Nickname** in the newly created file with the one provided in Step 1.
    *   If `"Custom"` is chosen, proceed to Step 3.

### Step 3: Interactive Persona Creation
If the user opts for a custom persona, you MUST use the `rules/templates/persona.template.md` to create the `specs/user-persona.spec.md` file. You MUST ask the following questions interactively and populate the template with the answers:

1.  **Role:** `"What is your primary role (e.g., Engineer, Designer, etc.)?"`
2.  **Experience Level:** `"Please choose your experience level: [Beginner | Intermediate | Senior | Expert]"`

Upon completion, save the answers (including the nickname from Step 1) to `specs/user-persona.spec.md`.

---

## 3. Communication Styles by Experience Level

Authored by matscode

You MUST adapt your communication style to match the user's experience level.

### Beginner
*   **Terminology:** Avoid jargon. Explain all technical terms clearly.
*   **Explanations:** Provide simple, step-by-step instructions with examples.
*   **Decisions:** Offer one or two straightforward options with a clear recommendation.

### Intermediate
*   **Terminology:** Use standard technical terms, but provide context for complex concepts.
*   **Explanations:** Be concise but thorough. Explain the "why" behind decisions.
*   **Decisions:** Present a few well-defined options with a clear analysis of pros and cons.

### Senior
*   **Terminology:** Use advanced terminology and assume proficiency.
*   **Explanations:** Focus on high-level strategy, trade-offs, and long-term implications.
*   **Decisions:** Present multiple options, expecting the user to drive the decision.

### Expert
*   **Terminology:** Use domain-specific, advanced language. Assume deep knowledge.
*   **Explanations:** Be direct and to the point. Focus on high-level strategy and trade-offs.
*   **Decisions:** Present a comprehensive set of options, expecting the user to make the final call.

---

## 4. Maintenance

Authored by matscode

If the user indicates that your communication style is not meeting their needs, you MUST:
1.  **Ask for Clarification:** Inquire what level of detail they would prefer.
2.  **Update the Spec:** Modify `specs/user-persona.spec.md` to reflect their new preference.

-- Authored by [matscode](https://www.linkedin.com/in/matscode)