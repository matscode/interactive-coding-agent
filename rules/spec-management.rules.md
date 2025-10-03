# Specification Management Rules

**MANDATORY: ALL AGENTS MUST FOLLOW THESE SPECIFICATION RULES**

**VIOLATION ENFORCEMENT:** All violations of rules in this file are subject to the universal violation enforcement system defined in [rules/violation-enforcement.rules.md](./violation-enforcement.rules.md).

---

## SPECIFICATION DOCUMENTATION REQUIREMENTS

**MANDATORY: CODING AGENTS MUST READ SPECIFICATIONS FIRST:**
- **BEFORE ANY CODING:** Read `project-specs/index.spec.md` to understand existing decisions
- **FOLLOW EXISTING PATTERNS:** Use established patterns from existing specifications (see `project-specs/index.spec.md` for documented patterns)
- **CREATE SPECIFICATION FIRST:** Document NEW decisions before implementation
- **WAIT FOR APPROVAL:** Do NOT implement until explicit approval received

---

## WHEN TO CREATE SPEC FILES

**MANDATORY TRIGGERS** - Create specification when encountering:

1. **Architectural decisions** (state management, data flow, component structure)
2. **Technology choices** (libraries, frameworks, tools)
3. **Data persistence decisions** (database, storage, caching)
4. **API design decisions** (REST, GraphQL, endpoints)
5. **Security implementations** (authentication, authorization)
6. **Performance optimizations** (caching, lazy loading, bundling)

**DECISION-MAKING TRIGGER WORDS:**
When users use these phrases, they're likely making decisions that need documentation:

**INSTALLATION & ADOPTION:**
- "Let's install..." / "Should we install..." / "Install [library/tool]"
- "Add [dependency/package]" / "Use [framework/library]"
- "Switch to..." / "Migrate to..." / "Adopt [technology]"

**COMPARISON & EVALUATION:**
- "Compare [A] vs [B]" / "What's better..." / "Best [solution/approach]"
- "Deciding between..." / "Choose..." / "Pick..."
- "Pros and cons" / "Trade-offs" / "Alternatives"

**ARCHITECTURAL DECISIONS:**
- "How should we..." / "What's the right way to..."
- "Structure..." / "Organize..." / "Design..."
- "Approach for..." / "Strategy for..." / "Pattern for..."

**CONFIGURATION & SETUP:**
- "Configure..." / "Set up..." / "Initialize..."
- "Which settings..." / "How to configure..."
- "Default values" / "Environment setup"

**CONTEXT REQUIREMENTS:**
When coding agents need context for:
- **Consistency Requirements:** Decisions that must be uniform across the codebase (naming conventions, file organization, API patterns)
- **Trade-off Implications:** Choices with significant pros/cons that affect future development (performance vs readability, flexibility vs simplicity)
- **Knowledge Dependencies:** Decisions requiring domain expertise or research that agents shouldn't repeat (security standards, compliance requirements)
- **Team Alignment:** Choices that impact multiple developers or system components (shared libraries, communication protocols)
- **Future Constraints:** Decisions that limit or enable future options (database schema design, API versioning, plugin architectures)

---

## AGENT RESPONSE PROTOCOL FOR SPECIFICATION CREATION

**WHEN ENCOUNTERING DECISION POINTS THAT REQUIRE SPECIFICATION:**

1. **READ EXISTING SPECIFICATIONS** - Check `project-specs/index.spec.md` first
2. **FOLLOW EXISTING PATTERNS** - Use established patterns if applicable (see `project-specs/index.spec.md` for documented patterns)
3. **PAUSE IMPLEMENTATION** - Stop coding when new decisions are needed
4. **ASK CLARIFYING QUESTIONS** - **USE `run_command` TOOL** for all questions - **MUST FOLLOW** [rules/interactive-input.rules.md](./interactive-input.rules.md) for context on using run_command tool
5. **RESEARCH OPTIONS** - Present alternatives with trade-offs
6. **PROPOSE SPECIFICATION** - Create spec file with decision rationale
7. **WAIT FOR APPROVAL** - **USE `run_command` TOOL** for approval questions - **MUST FOLLOW** [rules/interactive-input.rules.md](./interactive-input.rules.md) for context on using run_command tool
8. **RE-READ SPECIFICATIONS** - **MANDATORY:** Read all relevant specs again after approval but before implementation to ensure most current information
9. **IMPLEMENT ACCORDING TO SPEC** - Follow approved specification exactly

**AGENT QUESTIONING PROTOCOL FOR SPECIFICATION DOCUMENTATION:**
Before creating any specification file, agents MUST ask these questions to ensure optimal documentation:

**USE `run_command` TOOL** for all questions - **MUST FOLLOW** [rules/interactive-input.rules.md](./interactive-input.rules.md) for context on using run_command tool

**DECISION CLARITY:**
- "What is your final decision? (If not explicitly stated)"
- "Can you confirm this is the approach you want to proceed with?"
- "Are there any constraints or requirements I should be aware of?"

**RATIONALE GATHERING:**
- "What led you to choose this option over alternatives?"
- "What factors were most important in your decision?"
- "Were there any specific pain points with current solutions that influenced this choice?"

**SOURCE DOCUMENTATION:**
- "Are there any specific articles, documentation, or resources that influenced your decision?"
- "Would you like me to include any particular sources in the spec?"
- "Did you reference any benchmarks, comparisons, or case studies?"

**CONTEXT & SCOPE:**
- "What problem does this decision solve?"
- "How does this impact the existing codebase/architecture?"
- "Are there any future considerations or migration paths to document?"

**USE `run_command` TOOL** for all questions - **MUST FOLLOW** [rules/interactive-input.rules.md](./interactive-input.rules.md) for context on using run_command tool when executing these questions.

**RESEARCH REQUIREMENTS:**
- **MANDATORY RESEARCH:** Perform online research for current best practices, latest versions, and community consensus before making decisions
- **VERIFICATION:** Confirm no existing spec covers the same decision
- **BEST PRACTICES:** Include research findings and industry-standard practices from last 12 months with >1000 GitHub stars OR official documentation recommendations

---

## MANDATORY SPEC-FIRST ENFORCEMENT RULE

**CRITICAL VIOLATIONS:**
- Implementing code without checking existing specifications = CRITICAL VIOLATION
- Making architectural decisions without creating specification = CRITICAL VIOLATION
- Proceeding with implementation before user approval = CRITICAL VIOLATION

**DECISION IMPACT CATEGORIES:**

**HIGH IMPACT DECISIONS** (ALWAYS require specification):
- Core architecture changes
- New external dependencies
- Database schema changes
- Authentication/authorization systems
- State management patterns
- API design patterns

**MEDIUM IMPACT DECISIONS** (Usually require specification):
- Component structure patterns
- Styling approaches
- Testing strategies
- Build/deployment configurations
- Error handling patterns

**LOW IMPACT DECISIONS** (May require specification if establishing patterns):
- Individual component implementations
- Utility function designs
- Minor styling choices
- Variable naming conventions

**ARCHITECTURAL PATTERNS:**
- Component architecture (atomic design, feature-based, etc.)
- State management (Redux, Zustand, Context, etc.)
- Data fetching (REST, GraphQL, SWR, React Query, etc.)
- Routing (React Router, Next.js, etc.)
- Form handling (Formik, React Hook Form, etc.)
- Styling (CSS Modules, Styled Components, Tailwind, etc.)
- Concurrency models (Threading vs async/await vs actor model - Go goroutines, Rust tokio, Erlang processes)
- Memory management (Manual C/C++, garbage collected Java/C#, ownership-based Rust)
- Error handling strategies (Exceptions vs result types vs error codes)
- Module organization (Monolithic vs microservices vs modular monolith)
- Communication patterns (Message queues, event streams, RPC, REST APIs)

**DATA & PERSISTENCE:**
- Storage paradigms (Relational PostgreSQL, document MongoDB, key-value Redis, graph Neo4j, time-series InfluxDB)
- Data serialization (JSON vs Protocol Buffers vs MessagePack vs XML)
- Caching strategies (In-memory, distributed, CDN, database query caching)
- Consistency models (ACID transactions vs eventual consistency vs BASE)
- Schema evolution (Migration strategies, versioning approaches)

**LANGUAGE & RUNTIME:**
- Language selection (Systems programming Rust/C++, web services Go/Java, scripting Python/JavaScript, mobile Swift/Kotlin)
- Compilation strategies (Ahead-of-time Go, just-in-time Java/C#, interpreted Python)
- TypeScript vs JavaScript
- Node.js version and runtime features
- Package manager (npm, yarn, pnpm)
- Build tools (Webpack, Vite, Rollup, etc.)
- Transpilation (Babel, SWC, etc.)
- Dependency management (Package managers, version pinning, lock files)
- Cross-platform deployment (Native compilation, containers, virtual machines)

**QUALITY & RELIABILITY:**
- Testing approaches (Unit, integration, end-to-end, property-based testing)
- Testing frameworks (Jest, Vitest, Cypress, etc.)
- Error monitoring (Logging levels, structured logging, distributed tracing)
- Code analysis (Static analysis tools, linters, formatters)
- Performance profiling (Memory profilers, CPU analysis, benchmarking tools)
- Security practices (Input validation, authentication, authorization, encryption)
- Linting and formatting (ESLint, Prettier, etc.)

**TOOLING & WORKFLOW:**
- Build systems (Make, Bazel, Maven, Gradle, Cargo, npm)
- Version control (Git workflows, branching strategies, merge vs rebase)
- Code formatting (Language-specific formatters - gofmt, rustfmt, prettier)
- Development environments (Local setup, containerized development, cloud IDEs)
- Deployment strategies (Blue-green, canary, rolling updates)
- Git workflow and branching strategy
- CI/CD pipeline and deployment
- Development environment setup
- Code quality tools (Husky, lint-staged, etc.)

**FOUNDATIONAL DECISIONS:**
- File naming conventions (snake_case vs camelCase vs kebab-case)
- Directory structure (Feature-based vs layer-based organization)
- Configuration management (Environment variables, config files, feature flags)
- Documentation standards (Code comments, API documentation, architectural diagrams)
- Logging conventions (Log levels, structured vs unstructured, centralized collection)

---

## MANDATORY ACTIONS FOR AGENTS

**SPECIFICATION MANAGEMENT REQUIREMENTS:**
1. **RESEARCH** existing specifications in `project-specs/` directory before any implementation
2. **CREATE** `.spec.md` file for new decisions using mandatory template from `rules/templates/spec.template.md`
3. **UPDATE** `project-specs/index.spec.md` with new specification reference immediately after creation
4. **REFERENCE** existing specifications when making related decisions to ensure alignment with past decisions
5. **MAINTAIN** specifications when original decision no longer applies OR new requirements invalidate assumptions OR implementation reveals better approach

**SPECIFICATION COMPLIANCE ENFORCEMENT:**
- All agents MUST follow the core workflow defined in `rules/core-principles.rules.md`
- Specification creation is MANDATORY for all impactful architectural decisions
- Template adherence is REQUIRED - no deviations from `rules/templates/spec.template.md`
- Index file updates are CRITICAL - never skip this step

**VIOLATION CONSEQUENCES:**
- **FIRST VIOLATION:** Stop immediately, create required specification, restart implementation
- **REPEATED VIOLATIONS:** Session termination and restart with proper spec compliance
- **CRITICAL VIOLATIONS:** Immediate rollback and specification creation before proceeding

---

## STEP-BY-STEP SPECIFICATION FILE CREATION WORKFLOW

**PRE-CREATION CHECKS FOR SPECIFICATION FILES:**
1. **MANDATORY SEARCH:** Search existing specs in `project-spec/` directory for duplicates
2. **MANDATORY INDEX CHECK:** Check `project-spec/index.spec.md` for related decisions
3. **FORBIDDEN DUPLICATES:** NEVER create duplicate specs - merge with existing if similar
4. **RESEARCH REQUIREMENT:** Perform online research for industry-standard practices from last 12 months with >1000 GitHub stars OR official documentation recommendations
5. **CONTEXT GATHERING:** **USE `run_command` TOOL** for all questions - **MUST FOLLOW** [rules/interactive-input.rules.md](./interactive-input.rules.md) for context on using run_command tool
6. **VERIFICATION:** Confirm no existing spec covers the same decision

**SPECIFICATION FILE CREATION:**
- **MANDATORY DIRECTORY:** All specs MUST be in `project-spec/` directory - NO EXCEPTIONS
- **MANDATORY NAMING:** Use format `[decision-topic].spec.md` with kebab-case
- **MANDATORY EXTENSION:** Must use `.spec.md` extension - NOT `.md` or other extensions
- **FORBIDDEN LOCATIONS:** Never create specs outside `project-spec/` directory
- **EXAMPLES:** `react-state-management.spec.md`, `database-choice.spec.md`, `testing-framework.spec.md`
- **VIOLATION CONSEQUENCES:** Creating spec files in wrong location = CRITICAL VIOLATION

**SPECIFICATION CONTENT DEVELOPMENT:**
- **TEMPLATE ACCESS RULE:** READ `rules/templates/spec.template.md` ONLY during specification creation workflow
- **MANDATORY TEMPLATE USAGE:** Use exact template from `rules/templates/spec.template.md`
- **FORBIDDEN DEVIATIONS:** Never modify template structure
- **PERFORMANCE OPTIMIZATION:** Never read spec template file outside of spec creation workflow
- **COMPLETENESS CHECK:** All template sections must be filled - no empty sections allowed
- **RESEARCH INTEGRATION:** Include research findings and industry-standard practices from last 12 months with >1000 GitHub stars OR official documentation recommendations
- **ALTERNATIVES DOCUMENTATION:** Document all alternatives considered with pros/cons
- **SOURCE INCLUSION:** Add specific sources that influenced the decision
- **IMPLEMENTATION DETAILS:** Include installation commands + configuration files + code examples + migration steps + rollback procedures

**SPECIFICATION VALIDATION & INTEGRATION:**
- **MANDATORY INDEX UPDATE:** MUST update `project-spec/index.spec.md` immediately after creation
- **FORBIDDEN SKIP:** NEVER skip index file update - this is a CRITICAL VIOLATION
- **VERIFICATION:** Ensure specification addresses the decision completely
- **COMPLETENESS REVIEW:** Review spec for completeness and accuracy
- **LOCATION CONFIRMATION:** Confirm spec file exists in correct `project-specs/` directory location

---

## MAINTENANCE RULES

**AGENT RESPONSIBILITIES:**
- Update specifications when decisions change
- Reference specifications in implementation comments
- Validate implementations against specifications
- Keep `project-specs/index.spec.md` current

**VIOLATION CONSEQUENCES:**
- Outdated specifications = specification update required before proceeding
- Missing specification references = immediate specification creation required
- Implementation deviation from specification = rollback and specification review required

---

*Created by [@matscode](https://www.tiktok.com/@matscode) | [LinkedIn](https://www.linkedin.com/in/matscode)*