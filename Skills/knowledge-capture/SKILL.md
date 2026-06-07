# Knowledge Capture Skill (SKILL.md)

This skill automates the recording of user decisions, feedback, and "tribal knowledge" to ensure project consistency and long-term learning across all development tasks.

## 🎯 Goal
Capture and persist key architectural or procedural decisions in a centralized log file.

## 🛠 Workflow

### 1. Discovery & Initialization
*   The canonical knowledge capture file is **always** located at:
    ```
    docs/core/17-knowledge-capture.md
    ```
    Resolve the absolute path relative to the active workspace root. **Do not search for alternative filenames or locations.**
*   If the file **does not exist**, create it using the Initial Content Template below.
*   **Initial Content Template:**
    ```markdown
    # Knowledge Capture & Decision Log
    
    This document records key decisions and user feedback to ensure project continuity and alignment.
    
    ## Decision Log
    | Date | Theme | Decision / Suggestion | Impact |
    | :--- | :--- | :--- | :--- |
    ```

### 2. Entry Capture
*   Accept a "Decision" or "Suggestion" from the user.
*   Determine the current project context and assign a **Theme** that best categorises the entry. Common themes include:
    - `UI/UX Preferences`, `Architecture & Patterns`, `Data & State Management`, `Tooling & DevOps`, `Business Logic & Rules`, `Performance & Constraints`, `Testing & QA`, `Naming Conventions & Style`
*   Append a new row to the Decision Log table with the current date (YYYY-MM-DD) and the assigned Theme.

### 3. Validation
*   Confirm to the user that the knowledge has been persisted.
*   Summarize the impact of the decision.

## 📢 Usage Guidelines
*   **Proactive Recording**: If a user says "I prefer X over Y" or "Always do Z in this project", activate this skill immediately.
*   **App Dev Universal**: This skill is NOT limited to estimation briefs; use it for all coding, architectural, and design decisions.
