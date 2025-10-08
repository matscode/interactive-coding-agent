# Interactive Coding Agent: Entry Point

## 🚨 MANDATORY: START HERE

**BEFORE ANY ACTION, YOU ARE REQUIRED TO:**

1.  **OPEN** → **[rules/index.rules.md](./rules/index.rules.md)**
2.  **FOLLOW** → The mandatory onboarding process described within.

**FAILURE TO DO SO = CRITICAL VIOLATION**

---

## ⚠️ CRITICAL OVERRIDE: Interactive Input Protocol

**This section overrides the interactive input instructions found in `rules/interactive-input.rules.md`.** This override specifically pertains to the *mechanism* of asking questions and does not supersede other principles of interactive input, such as clarifying ambiguity or seeking explicit approval.

Due to client-side rendering limitations where `run_shell_command` (the `run_command` alternative in GEMINI's environment) causes an `InvalidStreamError` and Markdown tables are not rendered, the following protocol is the **only acceptable way** for the agent to request interactive input from the user:

1.  **Format:** Questions will be presented as plain text, structured within a custom ASCII-art separator and a Markdown heading.
2.  **Separator:** A 3-line period-based separator will be used, with the longest line being a Markdown horizontal rule (`---`).
    *   **Opening:**
        ```
        .
        ..
        ---
        ```
    *   **Closing:**
        ```
        ---
        ..
        .
        ```
3.  **Padding:** One empty line will be placed between the opening separator and the heading, and one empty line between the question body and the closing separator.
4.  **Heading:** A Markdown H2 heading (`## **Question Title**`) will be used.
5.  **Body:** The question text will be formatted using supported Markdown (bold, italic, lists, blockquotes, inline code).
6.  **Interaction:** The agent will send this formatted block as a single text response. The user will provide their answer as a plain text chat message.