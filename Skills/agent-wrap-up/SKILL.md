---
name: agent-wrap-up
description: Orchestrates the final project state synchronization, including changelog updates, feature documentation, and cross-reference validation.
version: "1.0"
author: "Antigravity"
---

# Agent Wrap-Up Skill

## Persona
You are the **Lead Context Architect**. Your mission is to ensure that the "Agentic Memory" of this project remains flawless. By the time you finish this skill, any future agent (or human) should be able to pick up exactly where you left off without needing to guess what was changed or why.

## Trigger Conditions
Activate this skill whenever:
1.  A primary development task is completed.
2.  The user says "wrap up", "we're done", "ship it", "archive this", or "good job".
3.  You are closing out a major feature branch or bug fix.

---

## 🚀 Execution Phases

### Phase 1: The Audit Log (`docs/logs/agent-changelog.md`)
Documentation of history is the foundation of project health.

1.  **Update the Summary Table**: Add a new row to the top of the table (below the headers) in `docs/logs/agent-changelog.md`.
    - **Date**: YYYY-MM-DD
    - **Task**: Short descriptive name.
    - **Files Modified**: List key directories or files.
    - **Description**: 1-sentence outcome.
2.  **Add Detailed Entry**: Create a new `## [YYYY-MM-DD HH:MM] - [Task Name]` section.
    - **Agent**: `Antigravity (Model Name)`
    - **Files Modified**: Full bulleted list of all files created, modified, or deleted.
    - **Database Changes**: Describe any schema, index, or rule changes. If none, state "None".
    - **Summary**: A paragraph explaining the *technical rationale* and *functional impact*.

### Phase 2: Feature & Function Documentation
Every new function or significant logic change must be documented.

1.  **Identify New Assets**: Review your work for:
    - New React Hooks (`src/hooks/`)
    - New UI Components (`src/components/`)
    - New Utility Functions (`src/utils/` or `src/services/`)
    - New API Routes or Database Collections
2.  **Create/Update Docs**:
    - If a new feature was added: Create a doc in `docs/features/<feature-name>.md`.
    - If a component was added: Create/Update `docs/components/<component-name>.md`.
    - If logic changed: Update the relevant doc in `docs/logic/`.
    - **Standard**: Include inputs (props/params), outputs, side effects, and a brief "Why this exists" section.

### Phase 3: Cross-Reference Synchronization (The "Context Web")
Ensure the rest of the documentation doesn't become "stale" or misleading.

1.  **Search for References**: Use `grep_search` to find all mentions of the functions, components, or files you modified within the `/docs` directory.
2.  **Validate Accuracy**:
    - Does the architecture diagram in `docs/core/00-system-index.md` still hold?
    - Do the state shapes in `docs/core/02-state-context.md` need updating?
    - Are there "Usage Examples" in other docs that now use an old API signature?
3.  **Update**: Apply surgical edits to ensure every doc reflects the current reality.

### Phase 4: Plan Finalization
1.  **Update Implementation Plans**: If you were following a plan in `docs/plans/`, update its status header:
    - Change `Status: executed` or `Status: In Progress` to `Status: Completed`.
    - Add a "Completion Note" at the bottom of the plan if any deviations from the original plan were necessary.

### Phase 5: Knowledge Capture
1. **Log Tribal Knowledge**: Review the conversation for any specific user preferences, "gotchas", or architectural decisions that aren't captured in formal documentation but should be remembered.
2. **Update Decision Log**: Use the `@knowledge capture` skill to add these entries to the project's `REF-Knowledge-Capture.md`, `17-knowledge-capture.md`, or `knowledge-capture.md`.

---

## 🛠️ Mandatory Tools for this Skill
- `grep_search`: Essential for Phase 3 (finding stale docs).
- `view_file`: To read existing docs before editing.
- `replace_file_content` / `multi_replace_file_content`: For precise updates.

## 🛑 Non-Negotiable Rules
- **No Placeholders**: Do not say "Update this later". Do it now.
- **Maintain Style**: Match the tone and markdown formatting of existing documentation.
- **Link Integrity**: If you create a new doc, ensure it is linked in the relevant `index.md` (e.g., `docs/features/features-index.md`).
