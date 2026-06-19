---
type: "core"
name: "Directory Structure"
status: "stable"
description: "Prevents file sprawl by defining where every type of file belongs."
---

# 🗺️ Directory Structure

## 📂 Project Source Tree

```
/
├── wiki/               # Application architecture knowledge base
│   ├── core/           # System core brain documents (00–18 series)
│   ├── features/       # Feature/screen documentation
│   ├── components/     # Reusable component documentation
│   ├── database/       # Schema/data models documentation
│   └── logic/          # Custom hooks, utilities, services
├── dev/             # Operational process & workflow tooling
│   ├── backlog/        # Pending/roadmap backlog index and plan files
│   ├── plans/          # Active implementation plans
│   ├── archive-plans/  # Archive of completed implementation plans
│   └── logs/           # Agent changelog and version history
├── src/                # Application source code
│   ├── components/     # Reusable presentation components
│   ├── features/       # Screen-level features and state
│   ├── hooks/          # Global React / framework hooks
│   ├── services/       # Third-party integration clients
│   └── utils/          # Pure utility helpers
```

## 📍 Path Mapping Rules

- **`src/components/`**: Only pure reusable UI elements without business domain logic.
- **`src/features/`**: Feature-specific view directories containing page shells, subcomponents, and local hooks.
- **`src/utils/`**: Pure functional code (input-to-output), free of UI dependencies.
- **`dev/backlog/`**: Master project backlog index and individual feature backlog plans.
- **`dev/archive-plans/`**: Completed and closed implementation plans.
