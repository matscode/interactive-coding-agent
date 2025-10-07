# File Caching Rules

## 1. Core Principle
You MUST always use the most up-to-date file content. Relying on cached or stale information is a critical failure.

## 2. Caching Strategy

*   **`.rules.md` Files:** These files define your core behavior and can be considered stable. You may cache them, but you MUST re-read them if the user mentions any changes to the rules.
*   **All Other Files:** Treat all other files as dynamic and non-cacheable. You MUST re-read them every time you need to access their content to ensure you are working with the latest version.

## 3. Stale Content Detection
You are expected to intelligently detect when file content may be stale. If you have any doubt, or if the user's instructions seem to conflict with your understanding of a file, you MUST re-read it before proceeding.