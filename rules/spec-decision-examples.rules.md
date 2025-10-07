# Specification Decision Examples

This document provides a comprehensive, non-exhaustive list of examples for when a specification is required. It is intended as a reference to be used for validation when there is doubt.

---

## Detailed Triggers for Specification Creation

A specification is required for **ALL** of the following:

### General Code Changes
- **New Features:** Any new functionality, components, functions, endpoints, or capabilities.
- **Bug Fixes:** Any correction of existing code behavior or functionality.
- **Refactoring:** Any restructuring, optimization, or code improvement without changing external behavior.
- **Configuration Changes:** Any modification to build tools, environment settings, or project configuration.
- **Dependency Changes:** Adding, removing, or updating any external libraries or packages.
- **Documentation Updates:** Changes to code comments, README files, or technical documentation.
- **Testing Changes:** Adding, modifying, or removing tests at any level.
- **Performance Optimizations:** Any changes aimed at improving system performance.
- **Security Updates:** Any changes related to security, authentication, or authorization.
- **Maintenance Tasks:** Code cleanup, formatting changes, or routine maintenance.
- **Architecture Changes:** Any modification to system structure, patterns, or design.
- **Database Changes:** Schema modifications, query updates, or data migration scripts.
- **API Changes:** Endpoint modifications, request/response format changes, or protocol updates.
- **UI/UX Changes:** Any modification to user interface or user experience elements.
- **Infrastructure Changes:** Deployment, CI/CD, or environment configuration modifications.

### Architectural Patterns
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

### Data & Persistence
- Storage paradigms (Relational PostgreSQL, document MongoDB, key-value Redis, graph Neo4j, time-series InfluxDB)
- Data serialization (JSON vs Protocol Buffers vs MessagePack vs XML)
- Caching strategies (In-memory, distributed, CDN, database query caching)
- Consistency models (ACID transactions vs eventual consistency vs BASE)
- Schema evolution (Migration strategies, versioning approaches)

### Language & Runtime
- Language selection (Systems programming Rust/C++, web services Go/Java, scripting Python/JavaScript, mobile Swift/Kotlin)
- Compilation strategies (Ahead-of-time Go, just-in-time Java/C#, interpreted Python)
- TypeScript vs JavaScript
- Node.js version and runtime features
- Package manager (npm, yarn, pnpm)
- Build tools (Webpack, Vite, Rollup, etc.)
- Transpilation (Babel, SWC, etc.)
- Dependency management (Package managers, version pinning, lock files)
- Cross-platform deployment (Native compilation, containers, virtual machines)

### Quality & Reliability
- Testing approaches (Unit, integration, end-to-end, property-based testing)
- Testing frameworks (Jest, Vitest, Cypress, etc.)
- Error monitoring (Logging levels, structured logging, distributed tracing)
- Code analysis (Static analysis tools, linters, formatters)
- Performance profiling (Memory profilers, CPU analysis, benchmarking tools)
- Security practices (Input validation, authentication, authorization, encryption)
- Linting and formatting (ESLint, Prettier, etc.)

### Tooling & Workflow
- Build systems (Make, Bazel, Maven, Gradle, Cargo, npm)
- Version control (Git workflows, branching strategies, merge vs rebase)
- Code formatting (Language-specific formatters - gofmt, rustfmt, prettier)
- Development environments (Local setup, containerized development, cloud IDEs)
- Deployment strategies (Blue-green, canary, rolling updates)
- Git workflow and branching strategy
- CI/CD pipeline and deployment
- Development environment setup
- Code quality tools (Husky, lint-staged, etc.)

### Foundational Decisions
- File naming conventions (snake_case vs camelCase vs kebab-case)
- Directory structure (Feature-based vs layer-based organization)
- Configuration management (Environment variables, config files, feature flags)
- Documentation standards (Code comments, API documentation, architectural diagrams)
- Logging conventions (Log levels, structured vs unstructured, centralized collection)