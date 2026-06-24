---
name: backlog
description: Make sure to use this skill whenever the user asks to add a feature, function, upgrade, idea, or task to the backlog. Use it to analyze the request, gather necessary codebase context, and create a comprehensive entry in the project's backlog-index.md and a separate backlog plan file.
---

# Backlog Management

## 1. Analyze and Gather Context
When the user requests to add an item to the backlog:
* Analyze the user's request to understand the core feature, function, or upgrade.
* Proactively explore the workspace to gather relevant context (e.g., related files, current architecture, existing patterns, or dependencies) that will be useful when implementing this in the future.
* Do not ask the user for information you can find yourself by reading the codebase.

## 2. Format the Backlog Entry
For each backlog item, create:
1. A brief entry line for the `docs/dev/backlog/backlog-index.md` index file containing a clickable link to the backlog plan.
2. A full, early-prepared plan file named `<feature-slug>-backlog.md` structured with the standard Pass-the-Parcel Markdown Template, setting the State Dashboard status to `BACKLOG` and active persona to `Planner`. Populate the following sections with the gathered context:
   * **Title:** A clear, concise name for the feature or upgrade.
   * **Phase 1 (Expansion & Scoping):** Frame the intent, in-scope, and out-of-scope tasks.
   * **Phase 2 (Requirements & Context):** Relevant files, current implementation details, and architectural considerations discovered during research.
   * **Phase 3 (User Clarification):** Any edge cases, potential roadblocks, or design decisions that need to be resolved before implementation (left as open checklist items).
   * **Phase 4 (Detailed Execution Plan):** Any tentative steps, commands, or placeholder logic.

## 3. Update the Backlog
* Locate the `backlog-index.md` file within the project's `docs/dev/backlog/` folder (create if missing).
* Add the new backlog item to the appropriate section as a bullet point linking directly to its `<feature-slug>-backlog.md` plan file.
* Create the `<feature-slug>-backlog.md` plan file inside the `docs/dev/backlog/` directory.
