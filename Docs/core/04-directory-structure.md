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
├── Docs/               # Local intelligence library
│   ├── archive-plans/  # Archive of completed implementation plans
│   ├── backlog/        # Pending/roadmap backlog index and plan files
│   ├── core/           # System core brain documents
│   ├── features/       # Feature/screen documentation
│   ├── components/     # Reusable component documentation
│   ├── database/       # Schema/data models documentation
│   ├── logic/          # Custom hooks, utilities, services
│   ├── logs/           # Agent changelog and version history
│   └── plans/          # Active implementation plans
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
- **`Docs/backlog/`**: Master project backlog index and individual feature backlog plans.
- **`Docs/archive-plans/`**: Completed and closed implementation plans.
