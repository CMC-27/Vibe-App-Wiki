---
type: "core"
name: "State Context & Data Shapes"
status: "stable"
dependencies: ["05-app-structure.md"]
description: "Maps how data lives in memory and flows between components."
---

# 💾 State Context

## 🌴 Provider Store Tree
*Structure tree of react providers or context stores wrapping the app.*

## 📋 Global State Schema
```typescript
// Define key interface structures representing global state
interface AppState {
  // To be filled with template schemas
}
```

## 🔌 Persistence & DB Sync
- **Local Storage:** *What is cached locally (e.g. settings).*
- **Remote Syncing:** *Optimistic UI patterns or webhook state listeners.*
