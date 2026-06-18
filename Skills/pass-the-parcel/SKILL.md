a---
name: pass-the-parcel
description: Make sure to use this skill whenever the user mentions "pass the parcel", "parcel mode", "/parcel", "token saving planning", "multi-agent planning", "stateless execution", "clear context", "independent reviewer", or wants to run a highly token-efficient, robust design-and-execution pipeline where state is passed entirely within a .md plan in docs/plans/.
---

# SKILL: Pass-the-Parcel (Low-Token Self-Contained Agent Orchestration)

Execute highly complex multi-agent engineering workflows with minimal token usage by maintaining the entire system state, goals, reviews, and execution checklists in a self-contained markdown "parcel" file at `docs/plans/[plan-name].md`. Each agent session operates stateless, reading the plan, executing its specific role, editing the plan, and immediately exiting without carrying conversation history.

---

## 🎯 Trigger Conditions

* User invokes the `/parcel` command or mentions "pass the parcel" or "parcel mode".
* User requests a complex feature that requires multiple design, review, coding, and testing steps, while demanding token-efficiency.
* Agent detects a long-running or multi-agent task and wants to structure it to avoid context inflation and conversation memory creep.

---

## 🛑 Review Gates & Context Isolation Protocol

To prevent context inflation and ensure complete control over design and execution, the agent **MUST** adhere to strict execution boundaries:

1. **Strict Context Isolation (Single Phase Rule):**
   - The agent is permitted to execute **ONLY ONE** phase grouping (e.g., scoping, planning, or executing) per conversation session.
   - Once a phase grouping is updated in the plan, the agent **MUST save the plan and immediately halt** (conclude the turn). It must never proceed to subsequent phases or touch code without the user explicitly initiating the next session.
   
2. **The Three Mandatory Review Gates:**
   - **🚪 Gate A (Scope & Context Review):** Stop after completing **Phases 1-3**. Present the expanded scope and clarification questions, then halt. Do not write a detailed technical plan or touch files.
   - **🚪 Gate B (Plan & Design Review):** Stop after completing **Phases 4-6** (Detailed Planning, Product Owner Review, Senior Dev Hygiene Review). Present the complete technical blueprint, then halt. **Do NOT begin Phase 7 execution.**
   - **🚪 Gate C (User Verification Review):** Stop after completing **Phases 7-8** (Execution & QA verification). Present the verification results and file changes. Wait for explicit user sign-off in **Phase 9** before performing **Phase 10 wrap up and archiving**.

---

## 🧭 Linguistic Rules (Caveman Integration)

To maximize token-savings during interaction and within the plan updates, agents must adhere to strict **Linguistic Token Compression**:
* **Terse Communication:** Drop pleasantries ("sure", "happy to help"), articles ("a", "an", "the"), fillers ("just", "actually"), and hedging.
* **Fragments & Arrows:** Write in fragments and use arrows for causality (`X -> Y`). Keep sentences short.
* **Abbreviate:** Use standard shorthand (e.g., `impl`, `spec`, `req`, `fn`, `test`, `auth`, `DB`).
* **Brevity first:** Only include exact, necessary code blocks or errors. Let the plan file speak for itself.

---

## 🧭 Execution Steps

### 📂 Backlog Pick-up Flow (Pre-Phase 1)
If the requested feature exists as a backlog item:
1. Locate its early-prepared plan file at `docs/backlog/<feature-slug>-backlog.md`.
2. Move (rename) this file to `docs/plans/<feature-slug>-plan.md`.
3. Update the State Dashboard in the plan:
   - Change **Status** to `PHASE_1`
   - Change **Active Persona** to `Scoper`
   - Update **Last Updated** to the current timestamp.
4. Remove the item from the active checklist in `docs/backlog/backlog-index.md`.
5. Proceed directly to Phase 1, building on top of the pre-populated context.

### 📌 GROUP A: Scoping & Context (Phases 1-3)
* **Goal:** Understand intent, locate context, resolve ambiguities.
* **Steps:**
  * **Phase 1 (Expansion & Scoping):** Expand request. Define in-scope and out-of-scope in `docs/plans/[plan-name].md`.
  * **Phase 2 (Requirements Gathering):** Search codebase and docs. Link exact files and context.
  * **Phase 3 (User Clarification):** Formulate concise clarifying questions for any remaining ambiguity. **You MUST use the `ask_question` tool — one question at a time — to collect answers interactively before updating the plan.** For each question, offer 2–4 selectable options with your recommended answer listed first (prefixed `(Recommended)`). Only after all answers are received, write the resolved Q&A into Phase 3 of the plan as `[x]` checked items. Always ask at least 5 questions.
* **🛑 HALT POINT (Gate A):** Once all clarifying questions have been answered interactively and Phase 3 is populated in the plan, update State to `PHASE_3`. Present the scoping summary and Phase 3 answers. **Stop execution immediately and wait for the user to approve the scope before proceeding to Group B.**

### 📌 GROUP B: Planning & Design (Phases 4-6)
* **Goal:** Architect solution, self-review for quality, security, and standards.
* **Steps:**
  * **Phase 4 (Detailed Execution Plan):** Write exact file-level steps, code blueprints, and verification commands in the plan.
  * **Phase 5 (Product Owner Review):** Audit the proposed changes using the **Senior Product Owner Lens**:
    * **Vision & Scope Integrity:** Verify the plan solves the *right* problem, respects defined scope boundaries, and lists UX flow details.
    * **Business Logic & Edge Cases:** Ensure empty states, loading indicators, error boundary strategies, and user-scoped data restrictions are planned.
    * **Dependency & Functional Risk:** Flag any downstream impacts or modifications to shared systems.
    * **Mandatory Decision Sync:** If any user clarifications occurred in Phase 3, you **MUST** sync these resolved product decisions to the project's knowledge capture log (e.g., `17-knowledge-capture.md`) before completing this phase.
  * **Phase 6 (Senior Dev Hygiene Review):** Audit and harden the execution plan using the **Senior Full-Stack Architect Lens**:
    * **Active DRY Scan (Non-Negotiable):** Run `grep_search` and `list_dir` to actively hunt for duplicate components, utility hooks, type definitions, constant declarations, or state shapes in the codebase *before* accepting any "new" additions. Rewrite the plan to reuse existing assets where possible.
    * **Strict Secret Management:** Ensure that environment variable usage is planned for all keys/tokens, and check that `.env` files are in `.gitignore`.
    * **Explicit Data Security:** Ensure Row Level Security (RLS) policies are defined for any new/modified database schemas or tables.
    * **Endpoint Protection & Rate Limiting:** Mandate request throttling and `429 Too Many Requests` handling on all new/modified endpoints.
    * **Robust Error Handling:** Wrap all async operations in error catching, forbid silent failures/empty catch blocks, and plan graceful client-facing fallbacks.
    * **Zero-Knowledge Instruction Density:** Harder-proof the Phase 4 instructions so they contain absolute file paths, exact function/component names, and precise diff plans.
* **🛑 HALT POINT (Gate B):** Update State to `PHASE_6`. Present the design blueprints and review logs. **Stop execution immediately. Do NOT touch any codebase files or run commands yet. Wait for explicit user approval to execute.**

### 📌 GROUP C: Execution & Verification (Phases 7-8)
* **Goal:** Code features strictly to plan, run QA, prove stability.
* **Steps:**
  * **Phase 7 (Execute Changes):** In a clean context, read the approved plan and edit codebase files exactly as designed. Mark off items.
  * **Phase 8 (Verify Changes):** Run test suites, verify against plan specifications, and log status.
* **🛑 HALT POINT (Gate C):** Update State to `PHASE_8`. Present completed work and QA verification report. **Stop execution immediately and wait for user to test and sign off.**

### 📌 GROUP D: Delivery & Archival (Phases 9-10)
* **Goal:** Final sign-off and system-state wrap-up.
* **Steps:**
  * **Phase 9 (User Verification):** User performs testing and provides sign-off.
  * **Phase 10 (Wrap Up):** Set plan state to `COMPLETE`. Move/archive the plan to `docs/archive-plans/`. Extract and persist new architecture patterns, models, or configurations into the central docs library (`docs/library/` or `docs/core/`).
* **🛑 HALT POINT:** Log wrap-up to changelog. End session.

---

## 📊 Parcel Markdown Template

> [!IMPORTANT]
> **Canonical Template Reference:** Always base new plan files on this skill's bundled template:
> `references/template-plan.md` → [`template-plan.md`](file:///C:/Users/carso/.gemini/config/skills/pass-the-parcel/references/template-plan.md)
> Read this file with `view_file` before creating any plan to ensure you use the latest structure. The inline template below is a convenience copy — the `references/` file is the source of truth.

Create the plan at `docs/plans/[plan-name].md` using this exact structure:

```markdown
# 📦 Parcel Plan: [Plan Name]

## 📊 State Dashboard
| Metric | Value |
| :--- | :--- |
| **Status** | `[PHASE_1 ... PHASE_10 / COMPLETE]` |
| **Version** | `vX.Y.Z` |
| **Active Persona** | `[Scoper / Researcher / Planner / PO / Senior Dev / Executor / QA / Archivist]` |
| **Last Updated** | `YYYY-MM-DD HH:MM` |

---

## 1️⃣ Phase 1: Expansion & Scoping
* **Intent:** [Terse description of user's core goal]
* **In Scope:** 
  - [Item 1]
* **Out of Scope:**
  - [Item 1]

## 2️⃣ Phase 2: Requirements & Context
* **Relevant Docs Found:** 
  - `[doc.md]` (file:///path/to/doc.md) -> [Why it's relevant]
* **Relevant Code Found:** 
  - `[file.js]` (file:///path/to/file.js) -> [What needs to change]

## 3️⃣ Phase 3: User Clarification
* **Open Questions:**
  - `[ ]` [Question for user] -> **Answer:** [User's response]

## 4️⃣ Phase 4: Detailed Execution Plan
* **Architecture & Files to Touch:**
  - `[path/to/file]` (file:///path/to/file) -> [brief change description]
* **Code Snippets & Instructions:**
  - [Detailed, exact instructions with code snippets]
* **Test Verification Plan:**
  - `[Exact command to run tests]`
  - `[ ]` [Test Case 1]

## 5️⃣ Phase 5: Product Owner Review
* **Status:** `[PENDING / REJECTED / APPROVED]`
* **Findings:**
  - [✅/⚠️/🚫] **Vision & Scope** — [brief note]
  - [✅/⚠️/🚫] **Business Logic & Edge Cases** — [brief note]
  - [✅/⚠️/🚫] **Dependency & Functional Risk** — [brief note]
  - [✅/⚠️/🚫] **Completeness & User Intent** — [brief note]
* **Required Fixes:**
  - `[ ]` [Fix 1 — or mark "None"]

## 6️⃣ Phase 6: Senior Dev Hygiene Review
* **Status:** `[PENDING / REJECTED / APPROVED]`
* **Findings:**
  - [✅/⚠️/🚫] **DRY Scan** — [brief note on any duplicates found]
  - [✅/⚠️/🚫] **Abstraction & Architecture** — [brief note]
  - [✅/⚠️/🚫] **State Management & Data Flow** — [brief note]
  - [✅/⚠️/🚫] **Technical Debt & Deletion** — [brief note]
  - [✅/⚠️/🚫] **Secret Management** — [brief note]
  - [✅/⚠️/🚫] **Data Security (RLS)** — [brief note]
  - [✅/⚠️/🚫] **Rate Limiting** — [brief note]
  - [✅/⚠️/🚫] **Error Handling** — [brief note]
* **Required Fixes:**
  - `[ ]` [Fix 1 — or mark "None"]

## 7️⃣ Phase 7: Implementation Checklist (Execution)
- `[ ]` [Execution Step 1 from Phase 4]
- `[ ]` [Execution Step 2 from Phase 4]

## 8️⃣ Phase 8: Verification Dashboard
* **Verification Status:** `[PENDING / FAILED / PASSED]`
* **Report:**
  - `[🟢/🔴]` Test suite runs clean
  - `[🟢/🔴]` Code matches exact plan specifications
  - `[🟢/🔴]` No functional gaps identified

## 9️⃣ Phase 9: User Verification
* **Status:** `[PENDING / APPROVED]`
* **User Feedback:** [Notes from user sign-off]

## 🔟 Phase 10: Wrap Up & Archival
* **System Context Updates:** [Detail newly introduced patterns or boundaries to persist to core docs]
```
