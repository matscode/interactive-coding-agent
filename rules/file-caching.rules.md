# File Caching and Stale Content Prevention Rules

🚨 **MANDATORY FOR ALL AGENTS** 🚨

**VIOLATION ENFORCEMENT:** All violations of rules in this file are subject to the universal violation enforcement system defined in [rules/violation-enforcement.rules.md](./violation-enforcement.rules.md).

---

## Core Principle

**NEVER use stale or cached file content when making decisions or generating code.**

## File Categories

### Simple Rule: Format-Based Caching

- **`.rules.md` files** - CACHEABLE (stable rules, can be cached between sessions)
- **Everything else** - NON-CACHEABLE (must be re-read every time)

---

## 🔄 RULES RELOAD PROTOCOL

### MANDATORY RULES RELOAD TRIGGERS

**AGENT MUST RELOAD ALL RULES WHEN:**

1. **User Explicitly Mentions Rules Update:**
   - "I updated the rules"
   - "Rules have changed"
   - "Check the new rules"
   - "Reload the rules"
   - Any variation indicating rules modification

2. **User References Specific Rule Changes:**
   - "I modified core-principles.rules.md"
   - "Updated the interactive input rules"
   - "Changed the violation enforcement"

3. **User Indicates Rule Inconsistency:**
   - "That's not what the rules say"
   - "The rules are different now"
   - "You're not following the current rules"

### RELOAD PROCEDURE

**WHEN RELOAD TRIGGERED:**

```bash
# MANDATORY: Confirm rules reload with user
echo -e "Rules update detected. Reloading ALL rule files. Proceed? (yes/no): "; read consent
```

**IF USER CONFIRMS:**
1. **Clear all cached rule content**
2. **Re-read ALL `.rules.md` files as specified in [rules/index.rules.md](./index.rules.md)**
3. **Confirm successful reload**
4. **Apply new rules immediately**

---

## 🚨 STALE CONTENT PREVENTION

### POINT-OF-USE ENFORCEMENT

**MANDATORY:** Before any file interaction, change, open, update, or using file content to make decisions, agent MUST re-read the file at the point of use.

**APPLIES TO ALL NON-RULES FILES:**
- Source code files
- Configuration files  
- Specification files
- Data files
- Any file not ending in `.rules.md`

### MANDATORY VERIFICATION STEPS

**BEFORE ANY FILE OPERATION:**

1. **Identify File Type:** `.rules.md` files are cacheable, everything else requires re-reading
2. **Re-read Non-Rules Files:** Always get fresh content before any operation
3. **Content Synchronization:** Verify content matches expectations before proceeding

### VIOLATION PREVENTION

**CRITICAL VIOLATIONS TO PREVENT:**

1. **Stale Source Code**: Operating on outdated file content
2. **Stale Configuration**: Using cached config that has changed
3. **Stale Specifications**: Referencing outdated project specs
4. **Stale Dependencies**: Missing new packages or version changes

**PREVENTION PROTOCOL:**
- **RE-READ** all non-rules files before any operation
- **VERIFY** content freshness through timestamps
- **ASK USER** if unexpected content is discovered
- **STOP IMMEDIATELY** if file content differs from expectations

---

## 📋 COMPREHENSIVE FILE READING PROTOCOLS

### MANDATORY FILE READING PROTOCOL

**CRITICAL: ALWAYS RE-READ FILES BEFORE MODIFICATION**

**MANDATORY PROTOCOL - NO EXCEPTIONS:**

**1. ALWAYS Re-read Before ANY File Modification:**
- **MANDATORY:** Before any edit_file/update_file/write_to_file operation
- **ACTION:** Use view_files to read current content first
- **THEN:** Proceed with modification based on current state

**2. ALWAYS Re-read Specifications Before Implementation:**
- **MANDATORY:** Before implementing any specification
- **ACTION:** Re-read the current specification content using view_files
- **VERIFY:** Compare with agent's memory of the specification
- **CLARIFY:** If content differs from expectations, ask user for clarification
- **THEN:** Proceed with implementation based on current specification content

**3. Content Verification Requirements:**
- **COMPARE** current file content with agent's memory/understanding
- **DETECT** any changes between expected and actual content
- **UPDATE** internal understanding when differences are found
- **ASK USER** for clarification if unexpected changes are detected
- **STOP IMPLEMENTATION** if file content is unexpected

**4. Specification Re-reading Rules:**
- **NEVER** implement specifications without re-reading them first
- **VERIFY** specification content matches expected requirements
- **ASK USER** if specification content differs from expectations
- **COMPARE** current specification with agent's memory of previous content
- **UPDATE** understanding when specification has been modified

### CONTENT COMPARISON PROTOCOL

**CRITICAL: COMPARE CURRENT FILE STATE WITH AGENT MEMORY**

**PURPOSE:** Prevent violations caused by operating on stale understanding by comparing current file content with agent's memory.

**MANDATORY VERIFICATION STEPS:**

**1. Memory vs Current State Comparison:**
- **RECALL** agent's last known understanding of file content
- **RE-READ** current file content using view_files
- **COMPARE** current content with remembered state
- **IDENTIFY** any differences between memory and current reality

**2. Change Detection Process:**
- **DETECT** differences between expected and actual content
- **ANALYZE** whether changes affect current task or implementation
- **UPDATE** internal understanding to match current file state
- **NOTE** what has changed since last interaction

**3. User Clarification Protocol:**
- **IF** unexpected changes found: Ask user about the changes
- **IF** changes affect current task: Seek guidance on how to proceed
- **ALWAYS** acknowledge when file content differs from expectations

**4. Content Synchronization Protocol:**
- **UPDATE** agent understanding to match current file state
- **PROCEED** with modifications based on current content, not memory
- **VERIFY** all dependencies and related files for consistency
- **DOCUMENT** any discrepancies found during verification

**5. Implementation Safety Rules:**
- **STOP** implementation if unexpected file content is discovered
- **ASK** user for guidance when file content differs from expectations
- **BASE** all decisions on current file state, not cached memory
- **NEVER** assume file content matches agent's memory without verification

### STANDARD IMPLEMENTATION PATTERN

**IMPLEMENTATION PATTERN:**
```bash
# Step 1: Recall agent's memory of file content
# (Internal process - what does agent remember about this file?)

# Step 2: Read current file state  
view_files [target_files]

# Step 3: Compare current content with agent memory
# If different: update understanding and ask user for clarification if needed

# Step 4: Proceed with modifications based on current file state
edit_file/update_file [with updated current content understanding]
```

### COMPREHENSIVE VIOLATION PREVENTION

**VIOLATION PREVENTION:**
- **Treat all file content as dynamic, never static**
- **Assume user may have made changes** since last agent interaction
- **Build content comparison steps** into all file interaction workflows
- **Create habits** of re-reading and comparing before acting
- **Never skip** the re-reading step, even for "recently" read files
- **Build memory vs reality comparison** into all file interaction workflows
- **Create verification habits** before any modification
- **Treat content differences** as indicators of file changes
- **Never skip** content verification, even for "simple" tasks

---

## 📁 FILE TYPE CLASSIFICATION

### RULES FILES (CACHEABLE)
- **Pattern**: `*.rules.md`
- **Location**: `rules/` directory
- **Behavior**: Read once per session, cache until reload triggered
- **Purpose**: Define agent behavior and protocols

### PROJECT FILES (NON-CACHEABLE)
- **Pattern**: All other files
- **Location**: Any directory
- **Behavior**: Re-read every time before use
- **Purpose**: Active development content that changes frequently

### EXCEPTION HANDLING

**EDGE CASES:**
- **Template Files**: `rules/templates/*.md` - NON-CACHEABLE (read only when needed)
- **Hidden Files**: `.gitignore`, `.env` - NON-CACHEABLE
- **Binary Files**: Images, executables - NON-CACHEABLE (but rarely read anyway)

---

## 🛡️ IMPLEMENTATION REQUIREMENTS

### MANDATORY AGENT BEHAVIOR

**EVERY AGENT MUST:**

1. **Classify files correctly** - rules vs non-rules
2. **Re-read non-rules files** before every operation
3. **Cache rules files** until reload triggered
4. **Respond to reload triggers** immediately
5. **Verify content freshness** through timestamps
6. **Ask for clarification** when content differs from expectations

### PERFORMANCE CONSIDERATIONS

**OPTIMIZATION GUIDELINES:**
- **Rules caching** improves performance (stable content)
- **Non-rules re-reading** ensures accuracy (dynamic content)
- **Batch file reads** when possible to minimize tool calls
- **Prioritize accuracy** over performance for non-rules files

---

## Violation Handling

### When User Complains About Violations

**MANDATORY FIRST STEP:** Agent MUST reload ALL rules as specified in [rules/index.rules.md](./index.rules.md) before addressing the violation complaint.

**Protocol:**
1. **IMMEDIATELY** re-read all `.rules.md` files per index.rules.md
2. **THEN** address the violation complaint with current rules
3. **NEVER** respond to violation complaints with potentially stale rule knowledge

### Violation Consequences

All violations are subject to the universal violation enforcement system defined in [violation-enforcement.rules.md](./violation-enforcement.rules.md).

---

**NO EXCEPTIONS. NO ASSUMPTIONS. ALWAYS USE FRESH CONTENT.**

---

*Single source of truth for file caching policies - MUST be followed by all agents.*

---

*Created by [@matscode](https://www.tiktok.com/@matscode) | [LinkedIn](https://www.linkedin.com/in/matscode)*