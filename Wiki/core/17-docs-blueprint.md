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

### 📖 Wiki — Architecture Knowledge Base
- `Wiki/core/` (Brain: core indexes, architecture, design system)
- `Wiki/features/` (Nervous System: view logic & feature modules)
- `Wiki/components/` (Muscle: reusable UI components)
- `Wiki/database/` (Skeleton: database schemas, relations)
- `Wiki/logic/` (Internal Organs: utilities, helpers, custom hooks)

### ⚙️ DevOps — Operational Process Tooling
- `DevOps/plans/` (Strategy: multi-agent execution plans, templates)
- `DevOps/logs/` (Memory: agent log records & version history)
- `DevOps/backlog/` (Queue: project backlog index and individual backlog plans)
- `DevOps/archive-plans/` (Archive: completed implementation plans)

## 📌 Standard File Naming

- **Core:** `Wiki/core/0x-name.md` (Numbered onboarding flow)
- **Features:** `Wiki/features/feat-name.md`
- **Components:** `Wiki/components/ui-name.md`
- **Database:** `Wiki/database/db-name.md`
- **Logic:** `Wiki/logic/util-name.md` or `hook-name.md`
- **Plans:** `DevOps/plans/name-plan.md`
- **Logs:** `DevOps/logs/agent-changelog.md` or `version-history.md`
- **Backlog:** `DevOps/backlog/backlog-index.md` or `<feature-slug>-backlog.md`
- **Archive:** `DevOps/archive-plans/name-plan.md`
