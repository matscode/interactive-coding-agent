# Interactive Coding Agent Project

A comprehensive rule framework that enforces mandatory interactive protocols for coding assistants. Features proactive clarification requirements, standardized terminal input protocols, user persona adaptation, and automatic specification management - designed to prevent assumptions and ensure collaborative decision-making with critical failure protocols for violations.

## 🚀 Forget Perfect Prompts - Just Be Vague!

**The whole point of AI is to make our work easier, not harder.** With these rules configured in your project, you can finally stop worrying about crafting the "perfect prompt" and just be as vague and simple as you like.

Say goodbye to:
- ❌ "Please create a responsive React component with TypeScript, using Tailwind CSS, following best practices..."
- ❌ Overthinking every request to avoid unwanted features
- ❌ Getting frustrated when AI assumes what you didn't ask for

Say hello to:
- ✅ "Make a button"
- ✅ "Add some styling"
- ✅ "Lets fix a bug"
- ✅ "Refactor this code"

**The agent will ask YOU the clarifying questions.** No more guessing games, no more unwanted features, no more assumptions. Just natural, collaborative coding that feels like pair programming with a thoughtful colleague.

**Working with coding agents just got 10x better.**

## 🎥 See It In Action

Watch how the Interactive Coding Agent works:
- **TikTok**: [Interactive Coding Demo](https://www.tiktok.com/@matscode/video/7548933674947857671?is_from_webapp=1&sender_device=pc&web_id=7517615038972544518)
- **YouTube**: [Interactive Coding Demo](https://www.youtube.com/shorts/dDPBXYnJjB4)

## Benefits

- **Holistic Workflow**: A master guide that orchestrates all other rules, ensuring a flexible and iterative process.
- **Proactive Clarification**: Agents must seek clarification on vague requirements before implementation.
- **Mandatory Stop Points**: Built-in triggers for ambiguous requirements, multiple approaches, and feature additions.
- **Interactive Terminal Input**: Standardized "one question, one answer" protocols using terminal commands for user input.
- **User Persona Adaptation**: Communication style adapts based on your detected experience level.
- **Specification Management**: Automatic creation and maintenance of project specifications for significant decisions.
- **Scope Preservation**: Prevents removal of existing working components during refactoring.
- **Session Closure Protocol**: Always ends with explicit user confirmation before closing sessions.
- **Violation Prevention**: Stops scope creep, unrequested features, and silent assumptions with critical failure protocols.

## Setup

### Quick Start (Recommended)
**🚀 Easiest and fastest setup - works with all supported coding agents!**

**Copy this `interactive-coding-agent` folder's contents** (the AGENTS.md file, rules/ folder, and others) **into your project root.** That's it! You now have interactive coding agents configured for all platforms.

### Minimal Setup
Want just the essentials? Copy these:

**Required Files and Folders:**
- `rules/` folder (the main rules)
- `specs/` folder (for user persona and other specs)
- `feature-specs/` folder (for project specifications)

**Your Editor Config:**
- **Trae AI**: Copy `.trae/` folder
- **Cursor**: Copy `.cursor/` folder
- **Windsurf**: Copy `.windsurf/` folder
- **Kiro**: Copy `.kiro/` folder
- **Gemini**: Copy `GEMINI.md` file

### Standalone Agent
**⚙️ Manual setup flow** - For those who prefer a single, self-contained set of rules, the `standalone-agent.rules.md` file offers a streamlined setup. Instead of copying multiple folders, you can use this single file.

**This requires manual configuration following the instructions below:**

**Setup Instructions:**
1.  Download the `standalone-agent.rules.md` file from this repository.
2.  Rename it to match the filename your coding assistant requires.
3.  Place the renamed file in your project's root directory.

**Example:**
-   If you use **Cursor** or another agent that reads from `AGENTS.md`, you would rename `standalone-agent.rules.md` to `AGENTS.md`.

*This file provides a quick, single-file setup that includes all the necessary rules for persona personalization and interactive coding. However, it does not include the more advanced spec-driven development workflow available in the full rule set.*

### Rule Activation

- **Close and reopen project** (optional but recommended).
- **Start a new chat session**.
- **Trigger the rules** using one of the methods below:

  - **Vague Trigger (Recommended)**: Start the session with a simple, vague statement like:
    - "Hello"
    - "Let's make some changes"
  - **Explicit Trigger**: If the agent doesn't respond interactively, you can explicitly ask it to read the rules:
    - "Read the rules"

*Note: The rules must be triggered for each new chat session for the agent to follow them.*

**First Time Expectation:** The agent will guide you through creating a `user-persona.spec.md` file, which will tailor its communication style to your preferences.

## 👤 User Persona System

**Personalized AI that adapts to YOUR expertise level and communication style.**

The agent will automatically ask you to set up a user persona by answering a few simple questions, then generate a personalized profile that transforms how it communicates with you:

### 🎯 Persona Benefits by Role

**🔧 Senior Engineer**
- Skip basic explanations, focus on architecture decisions
- Present technical trade-offs and performance implications
- Assume familiarity with design patterns and best practices

**📊 Product Manager**
- Emphasize user impact and business value
- Focus on feature scope and timeline implications
- Translate technical decisions into business outcomes

**📈 Data Analyst**
- Prioritize data integrity and analytical accuracy
- Focus on visualization and reporting capabilities
- Emphasize statistical significance and data quality

**🌟 Enthusiast/Beginner**
- Provide detailed explanations and learning opportunities
- Suggest best practices and explain the "why" behind decisions
- Offer educational context and alternative approaches

The persona system ensures you get exactly the right level of detail and communication style for your expertise - no more overwhelming technical jargon for beginners, no more basic explanations for experts.

### 📝 Managing Your Persona

- **Persona File Location:** `specs/user-persona.spec.md`
- **Update Persona:** Edit the file directly to modify your preferences
- **Start Fresh:** Delete the persona file and start a new chat session to trigger the setup workflow again
- **Version Control:** Add `specs/user-persona.spec.md` to your `.gitignore` - personal preferences shouldn't be committed

## Rule Files Overview

| Rule File | Purpose |
|-----------|---------|
| **Main Rules** | Master index and overview of all rules |
| **Core Principles** | Fundamental workflow and decision-making protocols |
| **Interactive Input** | Terminal input standards and question protocols |
| **User Persona** | User detection and communication adaptation |
| **Spec Management** | Specification creation and management rules |

## Supported Agents

| Platform | Type | Entry Point | Status |
|----------|------|-------------|--------|
| **Trae AI** | IDE | `.trae > rules > project_rules.md` | ✅ Tested |
| **Cursor** | IDE | `AGENTS.md` | ✅ Tested |
| **Windsurf** | IDE | `.windsurf > rules > project_rules.md` | ✅ Tested |
| **Kiro (Vibe Mode)** | IDE | `.kiro > steering > rules.md` | ✅ Tested |
| **Gemini** | CLI | `GEMINI.md` | ✅ Tested |
| **Gemini Code Assist (VS Code)** | IDE | `GEMINI.md` | ✅ Tested |
| **Codex** | IDE | `AGENTS.md` | ⏳ Not Tested Yet |
| **Claude Code** | IDE | `AGENTS.md` | ⏳ Not Tested Yet |
| **GitHub Copilot** | IDE | `AGENTS.md` | ❌ Not Working Yet |

## 🔧 Troubleshooting

### Quick Fix (Try This First!)
**Problem**: Agent not behaving as expected
- **Simple Solution**: Ask the AI to "read the project rules" 
- **Fun Trick**: Just type "You violated" - agents usually take responsibility and self-correct
- **Reset**: These prompts often trigger proper rule compliance immediately

### Agent Not Following Rules
**Problem**: Agent ignores interactive protocols or makes assumptions
- **Solution**: Start a **new chat session** - rules only activate on fresh sessions
- **Check**: Verify `AGENTS.md` or editor config files are in your project root
- **Verify**: Look for rule violations in agent responses and point them out directly

### Rules Not Activating  
**Problem**: Agent behaves normally without interactive questioning
- **Solution**: Confirm you copied the correct files for your editor (see Setup section)
- **Check**: Ensure `rules/` folder is present with `index.rules.md` as entry point
- **Restart**: Close and reopen your editor, then start a new chat session

### Interactive Questions Not Working
**Problem**: Agent shows questions as text instead of executing them like a command
- **Solution**: This indicates a rule violation - remind agent to use `run_command` tool
- **Check**: Agent should execute questions like `echo "question"; read answer`
- **Escalate**: If persistent, explicitly request: "Use the run_command tool for questions"

### Persona Setup Issues
**Problem**: Agent doesn't ask about user persona or uses wrong communication style  
- **Solution**: Delete `specs/user-persona.spec.md` and start a new chat session
- **Manual**: Create persona file manually using templates in `rules/templates/`
- **Predefined**: Copy from `specs/user-personas/` (senior-software-engineer.spec.md, product-designer.spec.md, etc.) to `specs/user-persona.spec.md`
- **Override**: Edit existing persona file directly to update preferences
- **Final Step**: Start a new chat and ask the agent to "setup my user persona"

### Specification Management Issues

**Problem**: The agent is not creating specs for major decisions, or references are incorrect.

*   **Check the Rules:** Ask the agent to "read `spec-management.rules.md`" to re-familiarize itself with the mandatory workflow.
*   **Verify the Index:** Ensure that `feature-specs/index.json` is not corrupted and that all recent specs are correctly listed.
*   **Force a Sync:** If you suspect a mismatch, ask the agent to "verify and synchronize the spec index with the spec files."

---

*Created by [@matscode](https://www.tiktok.com/@matscode) | [LinkedIn](https://www.linkedin.com/in/matscode)*
