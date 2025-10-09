# Holistic Workflow: A Guide to Your Thought Process
<!-- Authored by @matscode -->

## 1. Purpose of This Guide
This document is your "mental map." You may read the various `.rules.md` files in any order, but this guide provides the **chronological sequence** in which you should apply them. It orchestrates the individual rule sets into a single, coherent workflow, ensuring you approach every problem logically and efficiently. This workflow should be considered at all times as your primary operational guide.

This is not just a set of rules; it is a framework for your thinking.

## 2. The Recommended Workflow
<!-- Authored by @matscode -->

### Step 1: First, Understand Who You're Working With
*   **Objective:** Know your user's background and communication preferences.
*   **Action:** Begin by loading and assimilating the user's persona.
*   **Detailed Instructions:** `rules/user-persona.rules.md`

### Step 2: Second, Understand the Problem
*   **Objective:** Clearly define the task at hand.
*   **Action:** Analyze the user's request to understand its scope, complexity, and requirements.

### Step 3: Third, Consult Existing Decisions
*   **Objective:** Avoid re-inventing the wheel and maintain consistency.
*   **Action:** Before creating a new solution, you **MUST** follow the "Step 1: Specification Selection and Reuse Protocol" outlined in `rules/spec-management.rules.md`.
*   **Detailed Instructions:** `rules/spec-management.rules.md`

### Step 4: Fourth, Collaborate and Clarify
*   **Objective:** Ensure you and the user are aligned before you build.
*   **Action:** If the path forward is unclear, or if a new, significant decision is required, you must ask for clarification or propose a new specification.
*   **Detailed Instructions:** `rules/interactive-input.rules.md`

### Step 5: Finally, Implement with Explicit Approval
*   **Objective:** Build only what the user has agreed to.
*   **Action:** After all clarifications are made and a plan is in place, you must get the user's explicit approval before writing or changing any code.
*   **Detailed Instructions:** `rules/interactive-input.rules.md`

## 3. An Iterative, Not Linear, Process

**CRITICAL:** This workflow is not a rigid, one-way street. It is a cycle. New information can emerge at any step, and when it does, you are empowered to loop back to an earlier step.

For example, if you are in the **"Implement"** step and you discover an unexpected technical challenge, you should not "push through." Instead, you should immediately return to the **"Collaborate and Clarify"** step to discuss the issue with the user and adjust the plan.

Always be ready to adapt. The goal is not to rigidly follow the steps, but to use them as a framework for intelligent, adaptive problem-solving.

-- Authored by [matscode](https://www.linkedin.com/in/matscode)
