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

- **Proactive Clarification**: Agents must seek clarification on vague requirements before implementation
- **Mandatory Stop Points**: Built-in triggers for ambiguous requirements, multiple approaches, and feature additions
- **Interactive Terminal Input**: Standardized question protocols using terminal commands for user input
- **User Persona Adaptation**: Communication style adapts based on detected user experience level (none to expert)
- **Specification Management**: Automatic creation and maintenance of project specifications for architectural decisions
- **Scope Preservation**: Prevents removal of existing working components during refactoring
- **Session Closure Protocol**: Always ends with explicit user confirmation before closing sessions
- **Violation Prevention**: Stops scope creep, unrequested features, and silent assumptions with critical failure protocols

## Setup

### Option 1: Full Setup (Recommended)
**Copy and paste everything** from this folder into your project root. This gives you interactive coding agent capability in all configured/supported editors.

### Option 2: Editor-Specific Setup
If you only want to setup for one editor, copy these files:

**Always Required:**
- `AGENTS.md` (root level)
- `rules/` folder (contains the main rules - **entry point: `rules/index.rules.md`**)

**Plus your editor's config:**
- For **Trae AI**: Copy `.trae/` folder
- For **Cursor**: Copy `.cursor/` folder (if available)
- For **Windsurf**: Copy `.windsurf/` folder
- For **Kiro**: Copy `.kiro/` folder

### How It Works
Once copied, the rules will automatically apply when you start a new coding sessions in supported editors.

**Important:** After copying the configuration files, you must **start a new chat session** for the rules to take effect.

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
| **Kiro** | IDE | `.kiro > steering > rules.md` | ✅ Tested |
| **Codex** | IDE | `AGENTS.md` | ⏳ Not Tested Yet |
| **Claude Code** | IDE | `AGENTS.md` | ⏳ Not Tested Yet |
| **GitHub Copilot** | IDE | `AGENTS.md` | ❌ Not Working Yet |
| **Gemini** | CLI | `AGENTS.md` | ❌ Not Working Yet |
| **Gemini Code Assist (VS Code)** | IDE | `AGENTS.md` | ❌ Not Working Yet |

---

*Created by [@matscode](https://www.tiktok.com/@matscode) | [LinkedIn](https://www.linkedin.com/in/matscode)*