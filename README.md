# Interactive Coding Agent Project

A framework for implementing interactive coding assistants that ask clarifying questions instead of making assumptions, designed for senior engineers who value collaborative decision-making.

## 🎥 See It In Action

Watch how the Interactive Coding Agent works:
- **TikTok**: [Interactive Coding Demo](https://www.tiktok.com/@matscode/video/7548933674947857671?is_from_webapp=1&sender_device=pc&web_id=7517615038972544518)
- **YouTube**: [Interactive Coding Demo](https://www.youtube.com/shorts/dDPBXYnJjB4)

## Purpose

This project provides tested rules for creating coding agents that:
- Stop and ask questions when requirements are vague
- Confirm understanding before implementation
- Verify feature scope matches user intent
- Request explicit approval at each step
- Always end sessions with user confirmation

## Benefits

- **Reduced Assumptions**: Agents ask instead of guessing
- **Scope Control**: Prevents feature creep and unwanted additions
- **Quality Assurance**: Built-in verification at every step
- **Senior Engineer Friendly**: Respects expertise and decision-making
- **Collaborative**: Promotes dialogue over silent implementation
- **Prevents Violations**: Stops scope creep, unrequested features, and silent assumptions

## Setup

### Option 1: TRAE Custom Agent (Fastest & Recommended)

**Requirements:** [TRAE IDE](https://trae.ai) (download if needed)

1. Click the [one-click setup link](https://s.trae.ai/a/ff8cff)
2. The agent will be automatically configured and ready to use

### Option 2: Full Setup (Second Recommended)
**Copy and paste everything** from this folder into your project root. This gives you interactive coding agent capability in all configured editors.

### Option 3: Editor-Specific Setup
If you only want to setup for one editor, copy these files:

**Always Required:**
- `AGENTS.md` (root level)
- `agents/` folder (contains the main rules)

**Plus your editor's config:**
- For **Trae AI**: Copy `.trae/` folder
- For **Cursor**: Copy `.cursor/` folder (if available)
- For **Windsurf**: Copy `.windsurf/` folder

### How It Works
Once copied, the rules will automatically apply when you start coding sessions in supported editors.

**Important:** After copying the configuration files, you must **start a new chat session** for the rules to take effect.

## Supported Agents

| Platform | Type | Status |
|----------|------|--------|
| **TRAE Custom Agent** | Custom | ✅ **Recommended** - [One-click setup](https://s.trae.ai/a/ff8cff) |
| **Trae AI** | IDE | ✅ Tested |
| **Cursor** | IDE | ✅ Tested |
| **Windsurf** | IDE | ✅ Tested |
| **Codex** | IDE | ⏳ Not Tested Yet |
| **Claude Code** | IDE | ⏳ Not Tested Yet |
| **Gemini** | CLI | ❌ Not Working Yet |
| **Gemini Code Assist (VS Code)** | IDE | ❌ Not Working Yet |

---

*Created by [@matscode](https://www.tiktok.com/@matscode) | [LinkedIn](https://www.linkedin.com/in/matscode)*