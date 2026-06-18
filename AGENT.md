# Vibe App Wiki: Agent Entry Point 🚀

**Welcome to the Application Workspace.** 
This repository is configured with a structured documentation library split into **`/Wiki`** (architecture knowledge) and **`/DevOps`** (operational process tooling), designed to serve as the single source of truth for the codebase, architecture, state management, and user interfaces.

Instead of searching the entire codebase to understand context, **STOP** and read the localized intelligence hub first.

## 📌 MANDATORY READING (The Docs Hub)

Everything you need to execute bug fixes or feature requests flawlessly is mapped out in the `/Wiki` and `/DevOps` directories.

### 1. 🗺️ Start Here: `Wiki/core/00-system-index.md`
This is the master directory containing the Architecture Flow and system index. It maps out how the codebase, modules, and data stores interact.

### 2. 🎨 Need to build or edit a UI element?
**Read `Wiki/core/06-design-system.md` FIRST.**
- Do not guess CSS classes or component styles. The project uses a strict, predefined theme and design tokens.
- Review global layouts and layout wrappers defined here before implementing screens.

### 3. 💾 Need to interact with Application State?
**Read `Wiki/core/07-state-context.md` FIRST.**
- Provides the exact shapes of active contexts, store structures, or data models.

### 4. 🗄️ Database Schemas & API Integration
- Raw schema breakdowns, API specs, and endpoints are located in **`Wiki/database/`** or **`Wiki/api/`**. Always verify keys, types, and constraints before writing queries or integrations.

### 5. 🛠️ Editing an existing Screen or finding an Asset?
- Look up the feature-specific context in **`Wiki/features/`** or check the physical layout of the codebase via **`Wiki/core/04-directory-structure.md`**. It holds the exact file paths and dependencies.

---

## 🔎 TASK LOOKUP

| Task | Read first | Then drill into |
|---|---|---|
| Building or editing a UI component | [Components Index](Wiki/components/components-index.md) | Specific component doc |
| Building or editing a screen / view | [Features Index](Wiki/features/features-index.md) | Specific feature doc |
| Writing a database query / API request | [Database/API Index](Wiki/database/database-index.md) | Specific schema / endpoint doc |
| Editing overall layout or workspace shell | [App Shell Structure](Wiki/core/05-app-structure.md) | Core layout component docs |
| Understanding state shapes / context | [State & Context](Wiki/core/07-state-context.md) | State management docs |
| Extending a utility or custom helper | [Logic Index](Wiki/logic/logic-index.md) | Specific utility / helper doc |
| Checking backlog/roadmap or parked items | [Backlog Index](DevOps/backlog/backlog-index.md) | Specific backlog plan doc |
| Viewing archived implementation plans | [Plan Archive](DevOps/archive-plans/README.md) | Specific archived plan |

---

## ⚡ Core Development Rules
1. **Never Hardcode Components:** Use the global variants inside the component library (e.g., standard UI primitive folders).
2. **Follow Design Specs:** Adhere strictly to the color palettes, fonts, and UI behaviors detailed in the Design System.
3. **Destructive Actions:** Require confirmation modals/prompts for any user actions that delete or destroy data.
4. **Context Review:** Before writing any code, review the last 3 entries in `DevOps/logs/agent-changelog.md` to establish current project state.
5. **Planning & Execution:** For multi-step tasks, create/update a plan file under `DevOps/plans/` using the [Template Plan](DevOps/plans/template-plan.md).
6. **Mandatory Wrap-Up Protocol:** Whenever a task or feature is complete — including when the user says anything like "wrap up", "we're done", "ship it", "that's it", or closes out a conversation — you **MUST** perform the following steps:

   **Part 1 - Audit Logging:** Document your actions by adding a row to `DevOps/logs/agent-changelog.md` using the exact format below:
   ```markdown
   ## [YYYY-MM-DD HH:MM] - [Task Name]
   **Agent:** [Application/Agent Name] ([Model Name])
   **Files Modified:**
   - `src/...`
   **Database/API Changes:** None | [describe if any]
   **Summary:** One sentence summary of changes.
   ```

   **Part 2 — Docs sync:** Update any `/Docs` file whose described behavior changed. These will have been mentioned in planning or used in execution.

   **Part 3 — Version History Logging:** If the task involves a deployment/push using the deployment pipeline, ensure that the newly incremented version (Major, Minor, or Patch) is logged under `DevOps/logs/version-history.md` alongside the deployer and key highlights.

   **Part 4 — Archiving Completed Plans:** Move the completed plan file from `DevOps/plans/[plan-name].md` to `DevOps/archive-plans/[plan-name].md` to keep the active plans directory clean.
