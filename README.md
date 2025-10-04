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

### Quick Start (Recommended)
**Copy this `interactive-coding-agent` folder's contents** (the AGENTS.md file, rules/ folder, and others) **into your project root.** That's it! You now have interactive coding agents.

### Minimal Setup
Want just the essentials? Copy these:

**Required Files and Folders:**
- `AGENTS.md` (put in your project root)
- `rules/` folder (the main rules)
- `project-specs/` folder
- `specs/` folder

**Your Editor Config:**
- **Trae AI**: Copy `.trae/` folder
- **Cursor**: Copy `.cursor/` folder  
- **Windsurf**: Copy `.windsurf/` folder
- **Kiro**: Copy `.kiro/` folder

### Activation
After copying files, **start a new chat** in your editor. The rules activate automatically.

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
| **Codex** | IDE | `AGENTS.md` | ⏳ Not Tested Yet |
| **Claude Code** | IDE | `AGENTS.md` | ⏳ Not Tested Yet |
| **GitHub Copilot** | IDE | `AGENTS.md` | ❌ Not Working Yet |
| **Gemini** | CLI | `AGENTS.md` | ❌ Not Working Yet |
| **Gemini Code Assist (VS Code)** | IDE | `AGENTS.md` | ❌ Not Working Yet |

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

---

*Created by [@matscode](https://www.tiktok.com/@matscode) | [LinkedIn](https://www.linkedin.com/in/matscode)*