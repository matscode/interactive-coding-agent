# Command Execution Rules

**MANDATORY: ALL AGENTS MUST FOLLOW THESE COMMAND EXECUTION PROTOCOLS**

---

## 🚨 VIOLATION REFERENCE
**VIOLATION ENFORCEMENT:** All violations of rules in this file are subject to the universal violation enforcement system defined in [rules/violation-enforcement.rules.md](./violation-enforcement.rules.md).

---

## Overview

This document establishes **MANDATORY** standards for command execution during coding sessions. Communication style must adapt to the user's persona as defined in `specs/user-persona.spec.md` following the guidelines in [rules/user-persona.rules.md](./user-persona.rules.md).

**These rules are STRICTLY MANDATORY and NON-NEGOTIABLE. VIOLATION = CRITICAL FAILURE. Always ask clarifying questions when in doubt. NO EXCEPTIONS.**

---

## Core Principles

<!-- Command execution standards by @matscode -->

1. **Mandatory Documentation** ⚠️ **CRITICAL**  
   - **ALL non-interactive commands MUST include detailed multiline comments**
   - **INTERACTIVE commands (using `read`, `set /p`, `Read-Host`) do NOT require the `# ---\n` separator**
   - **NEVER** execute commands without proper documentation
   - **FAILURE TO DOCUMENT = RULE VIOLATION**

2. **Approval-Based Execution** ⚠️ **CRITICAL**  
   - **MUST** request user permission for build and development commands
   - **FORBIDDEN** to execute build/dev commands without explicit approval
   - **MANDATORY**: Provide detailed testing steps if approval is denied

3. **Shell-Specific Formatting** ⚠️ **MANDATORY**  
   - **REQUIRED**: Use appropriate comment syntax for target operating system
   - **NEVER** use generic comments - adapt to shell environment
   - **NON-NEGOTIABLE** - failure to use proper syntax = rule violation

**🚨 COMMAND TYPE DISTINCTION:**
- **Regular Commands**: Require multiline comments with `# ---\n` separator
- **Interactive Commands**: Follow [rules/interactive-input.rules.md](./interactive-input.rules.md) format (no `# ---\n` separator)

---

## 🚨 MANDATORY COMMENT REQUIREMENTS

**ALL NON-INTERACTIVE COMMANDS MUST INCLUDE:**

### Comment Format by Operating System

**Unix/Linux/macOS (bash/zsh):**
```bash
# Command: Install Express.js package for Node.js web server
# Purpose: Adds Express framework to project dependencies
# Impact: Enables web server functionality and routing capabilities
# ---

npm install express
```

**Windows (Command Prompt):**
```cmd
REM Command: Install Express.js package for Node.js web server
REM Purpose: Adds Express framework to project dependencies  
REM Impact: Enables web server functionality and routing capabilities
REM ---

npm install express
```

**Windows (PowerShell):**
```powershell
<# 
Command: Install Express.js package for Node.js web server
Purpose: Adds Express framework to project dependencies
Impact: Enables web server functionality and routing capabilities

#>

npm install express
```

### Required Comment Elements

**MANDATORY COMMENT STRUCTURE:**
1. **Command**: Brief description of what the command does
2. **Purpose**: Why this command is being executed
3. **Impact**: What changes or effects this will have on the project

**🚨 CRITICAL FORMATTING REQUIREMENT:**
- **ALL command comments MUST be multiline** (minimum 3 lines)
- **VIOLATION**: Single-line or missing comments = CRITICAL FAILURE

---

## 🛑 BUILD & DEVELOPMENT COMMAND APPROVAL

**COMMANDS REQUIRING MANDATORY APPROVAL:**

### Build Commands
- `npm run build`, `yarn build`, `pnpm build`
- `flutter build`, `dart compile`
- `cargo build`, `go build`
- `mvn compile`, `gradle build`
- `python setup.py build`, `pip install -e .`
- `make`, `cmake --build`
- Any command containing "build", "compile", or "package"

### Development Server Commands  
- `npm run dev`, `yarn dev`, `npm start`
- `flutter run`, `dart run`
- `python manage.py runserver`, `flask run`
- `rails server`, `php artisan serve`
- `cargo run`, `go run`
- Any command containing "serve", "server", "run", or "dev"

### Testing Commands
- `npm test`, `yarn test`, `pytest`
- `flutter test`, `cargo test`
- `mvn test`, `gradle test`
- Any command containing "test" or "spec"

---

## 🔧 NON-INTERACTIVE COMMAND APPROVAL WORKFLOW

**MANDATORY APPROVAL PROCESS FOR BUILD/DEV/TEST COMMANDS:**

### Step 1: Request Permission Using Interactive Input
**MUST follow interactive input format and tool usage requirements from [rules/interactive-input.rules.md](./interactive-input.rules.md).**

**Example approval request (see interactive-input.rules.md for complete format requirements):**
```bash
echo -e "\n\n🚨 BUILD/DEV COMMAND APPROVAL REQUIRED\n\nCommand to execute:\n# Command: Start development server for React application\n# Purpose: Launch local development environment for testing changes  \n# Impact: Opens localhost server on port 3000, enables hot reloading\nnpm run dev\n\nApprove execution? (yes/no): "; read approval; echo "You selected: $approval"
```

### Step 2A: If Approved - Execute Command
```bash
# Command: Start development server for React application
# Purpose: Launch local development environment for testing changes
# Impact: Opens localhost server on port 3000, enables hot reloading
# ---

npm run dev
```

### Step 2B: If Denied - Provide Testing Steps
**MANDATORY FALLBACK - Provide detailed manual testing instructions:**

```bash
echo -e "\n\n📋 MANUAL TESTING STEPS\n\nSince build/dev command was not approved, here are detailed steps to test the implemented features:\n\n1. Navigate to project directory: cd /path/to/project\n2. Install dependencies: npm install\n3. Start development server: npm run dev\n4. Open browser to: http://localhost:3000\n5. Test specific features:\n   - Feature A: Click button X, verify behavior Y\n   - Feature B: Navigate to page Z, check element W\n6. Verify responsive design on mobile viewport\n7. Check browser console for errors\n\nPress Enter to continue..."; read continue
```

---

## 🎯 COMMAND CATEGORIZATION

### Interactive Commands (Exempt from Comment Requirements)
- Commands using `read`, `input()`, or similar user input functions
- Commands following [rules/interactive-input.rules.md](./interactive-input.rules.md) format
- **EXEMPTION**: Interactive commands already have built-in documentation

### Command Classification Rules

**🚨 UNIVERSAL RULE: ALL non-interactive commands MUST have multiline comments**

**Interactive Commands (NO comments required):**
- Commands using `read`, `set /p`, `Read-Host` for user input
- Follow [rules/interactive-input.rules.md](./interactive-input.rules.md) format

**Non-Interactive Commands (REQUIRE multiline comments with `# ---\n` separator):**
- **ALL commands that don't request user input**
- **Examples include but NOT LIMITED TO:**
  - Package installation: `npm install`, `pip install`, `cargo add`
  - File operations: `cp`, `mv`, `mkdir`, `rm`, `wc`, `ls`, `cat`
  - Git operations: `git add`, `git commit`, `git push`, `git status`
  - Database operations: `psql`, `mysql`, `mongosh`
  - System commands: `chmod`, `chown`, `systemctl`, `ps`, `top`
  - Text processing: `grep`, `sed`, `awk`, `sort`, `uniq`
  - Network commands: `curl`, `wget`, `ping`, `ssh`
  - **ANY other command that executes without user interaction**

**🚨 CRITICAL: If unsure whether a command is interactive, assume it requires comments**

### Approval-Required Commands (Build/Dev/Test)
- All build, development server, and testing commands
- **DOUBLE REQUIREMENT**: Must have comments AND approval

---

## 📋 PRE-COMMAND VALIDATION CHECKLIST

**MANDATORY VALIDATION - Before executing ANY run_command:**

- [ ] **Is this an interactive command?**
  - If YES: Follow interactive-input.rules.md format
  - If NO: Continue to next check

- [ ] **Does this command have proper multiline comments?**
  - Must include Command, Purpose, and Impact
  - Must use shell-appropriate comment syntax
  - Must be minimum 3 lines

- [ ] **Is this a build/dev/test command?**
  - If YES: Must request approval using interactive format
  - If NO: Can execute with comments

- [ ] **Are comments using correct shell syntax?**
  - Unix/macOS: Use `#` comments
  - Windows CMD: Use `REM` comments  
  - PowerShell: Use `<# #>` block comments

- [ ] **Is the command syntax valid for target OS?**
  - Verify command exists on target platform
  - Check for proper path separators and syntax

**VIOLATION DETECTION TRIGGERS:**
- Any non-interactive command without multiline comments
- Build/dev commands executed without approval
- Comments using wrong syntax for target shell
- Missing Command, Purpose, or Impact in comments

---

## 📋 ENHANCED COMPLIANCE CHECKLIST

**Before ANY command execution:**
- [ ] Identified command type (interactive/regular/build-dev)?
- [ ] Added proper multiline comments for non-interactive commands?
- [ ] Used correct shell syntax for comments?
- [ ] Requested approval for build/dev/test commands?
- [ ] Prepared fallback testing steps if approval denied?
- [ ] Verified command syntax for target operating system?
- [ ] Set appropriate requires_approval flag in tool usage?

**After command execution:**
- [ ] Verified command executed successfully?
- [ ] Provided output interpretation if needed?
- [ ] Offered next steps or follow-up actions?

**If approval denied:**
- [ ] Provided detailed manual testing steps?
- [ ] Explained how to verify implemented features?
- [ ] Offered alternative approaches?

**🚨 VIOLATION PROTOCOL:**
1. STOP immediately upon detecting missing comments or unauthorized execution
2. ACKNOWLEDGE violation type and specific rule broken
3. **EXECUTE** required documentation or approval process
4. WAIT for user response before proceeding
5. **NEVER** execute build/dev commands without explicit approval

---

## Examples

### Regular Command with Proper Documentation
```bash
# Command: Create new React component directory structure
# Purpose: Organize component files following project conventions
# Impact: Creates components/Button folder with index.js and styles
# ---

mkdir -p src/components/Button && touch src/components/Button/index.js src/components/Button/Button.module.css
```

### Build Command with Approval Workflow
**Follow interactive input format from [rules/interactive-input.rules.md](./interactive-input.rules.md) for approval requests.**

**Example approval workflow (see interactive-input.rules.md for complete format requirements):**
```bash
# First: Request approval using interactive input format
echo -e "\n\n🚨 BUILD COMMAND APPROVAL REQUIRED\n\nCommand to execute:\n# Command: Build production-ready React application\n# Purpose: Compile and optimize code for deployment\n# Impact: Creates optimized build folder, minifies assets\nnpm run build\n\nApprove execution? (yes/no): "; read approval; echo "You selected: $approval"
```

If approved, then execute:

```bash
# Command: Build production-ready React application  
# Purpose: Compile and optimize code for deployment
# Impact: Creates optimized build folder, minifies assets
# ---

npm run build
```

### Fallback Testing Steps (If Approval Denied)
```bash
echo -e "\n\n📋 MANUAL TESTING STEPS\n\nTo test the new Button component:\n\n1. Navigate to project: cd /path/to/project\n2. Install dependencies: npm install\n3. Start dev server: npm run dev\n4. Open: http://localhost:3000\n5. Test Button component:\n   - Verify button renders correctly\n   - Test click functionality\n   - Check hover states\n   - Validate accessibility\n\nPress Enter to continue..."; read continue
```

---

## 🎯 MANDATORY PRACTICES

1. **Universal Documentation** - Every non-interactive command must have multiline comments
2. **Approval-First Execution** - Never execute build/dev commands without permission
3. **Shell-Appropriate Syntax** - Use correct comment format for target operating system
4. **Comprehensive Fallbacks** - Always provide testing steps when approval denied
5. **Violation Prevention** - Validate all requirements before command execution
6. **User Respect** - Honor approval decisions and provide alternatives
7. **File Content Verification** - Re-read all configuration and project files before executing commands that depend on them
8. **Fresh Content Protocol** - Never execute commands based on stale file content or cached understanding
9. **Mandatory Closure** - Always end with session closure following [rules/interactive-input.rules.md](./interactive-input.rules.md)

**FILE READING INTEGRATION:**
- **MANDATORY:** Follow [rules/file-caching.rules.md](./file-caching.rules.md) for all file content verification
- **BEFORE COMMANDS:** Re-read dependency files, configuration files, and project specs before executing related commands
- **VERIFY DEPENDENCIES:** Check current file state before running build, test, or development commands

---

*Created by [@matscode](https://www.tiktok.com/@matscode) | [LinkedIn](https://www.linkedin.com/in/matscode)*