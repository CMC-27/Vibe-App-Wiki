---
type: "core"
name: "Docs Blueprint"
status: "stable"
dependencies: []
description: "A lightweight, in-repo reference to the Documentation Architecture Bootstrap standard."
---

# 📖 Documentation Architecture Blueprint

This project implements the **Documentation Library Standard** using a two-library split.

## 🗺️ Library Folder Taxonomy

### 📖 wiki — Architecture Knowledge Base
- `wiki/core/` (Brain: core indexes, architecture, design system)
- `wiki/features/` (Nervous System: view logic & feature modules)
- `wiki/components/` (Muscle: reusable UI components)
- `wiki/database/` (Skeleton: database schemas, relations)
- `wiki/logic/` (Internal Organs: utilities, helpers, custom hooks)

### ⚙️ DevOps — Operational Process Tooling
- `dev/plans/` (Strategy: multi-agent execution plans, templates)
- `dev/logs/` (Memory: agent log records & version history)
- `dev/backlog/` (Queue: project backlog index and individual backlog plans)
- `dev/archive-plans/` (Archive: completed implementation plans)

## 📌 Standard File Naming

- **Core:** `wiki/core/0x-name.md` (Numbered onboarding flow)
- **Features:** `wiki/features/feat-name.md`
- **Components:** `wiki/components/ui-name.md`
- **Database:** `wiki/database/db-name.md`
- **Logic:** `wiki/logic/util-name.md` or `hook-name.md`
- **Plans:** `dev/plans/name-plan.md`
- **Logs:** `dev/logs/agent-changelog.md` or `version-history.md`
- **Backlog:** `dev/backlog/backlog-index.md` or `<feature-slug>-backlog.md`
- **Archive:** `dev/archive-plans/name-plan.md`
