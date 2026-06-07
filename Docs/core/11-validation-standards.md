---
type: "core"
name: "Validation Standards"
status: "stable"
dependencies: []
description: "Defines the validation engine that ensures data quality across the application."
---

# 🛡️ Validation Standards

## 🧱 Validation Tiers

1. **Field-Level Validation:** *Immediate validation (regex, length check).*
2. **Entity-Level Validation:** *Object schemas and structure validations.*
3. **Cross-Entity Validation:** *Business rules validating relationships (e.g. unique constraints).*

## ⚠️ Error Classification

- **Warning:** *UI notices that don't block progression.*
- **Critical Stop:** *Hard errors that block submission or saving.*

## 🧩 Error Dashboards & UX Patterns
*How errors are highlighted and grouped to guide user recovery.*
