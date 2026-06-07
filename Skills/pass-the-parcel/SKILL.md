---
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

## 🧭 Linguistic Rules (Caveman Integration)

To maximize token-savings during interaction and within the plan updates, agents must adhere to strict **Linguistic Token Compression**:
* **Terse Communication:** Drop pleasantries ("sure", "happy to help"), articles ("a", "an", "the"), fillers ("just", "actually"), and hedging.
* **Fragments & Arrows:** Write in fragments and use arrows for causality (`X -> Y`). Keep sentences short.
* **Abbreviate:** Use standard shorthand (e.g., `impl`, `spec`, `req`, `fn`, `test`, `auth`, `DB`).
* **Brevity first:** Only include exact, necessary code blocks or errors. Let the plan file speak for itself.

---

## 🧭 Execution Steps

### Phase 1: Expansion & Scoping
* **Audit Goal:** Expand on the user's initial request. Detail the intention behind the request, define what is explicitly in-scope, and outline what is out-of-scope to prevent feature creep.
* **Target:** Create `docs/plans/[plan-name].md` (State: `PHASE_1`).
* **Fix:** Generate the plan file using the **Parcel Markdown Template** (see section below). Fill in the Phase 1 scoping details.

### Phase 2: Requirements Gathering
* **Audit Goal:** Ensure all necessary context is available before planning begins.
* **Target:** Workspace, Docs, Codebase, `docs/plans/[plan-name].md` (State: `PHASE_2`).
* **Fix:** Search the workspace for documentation and code relevant to the changes. Summarize findings and attach necessary context references into the parcel file.

### Phase 3: User Clarification
* **Audit Goal:** Resolve ambiguity before technical design.
* **Target:** User, `docs/plans/[plan-name].md` (State: `PHASE_3`).
* **Fix:** Formulate clear, concise questions for the user based on Phase 1 & 2 findings. Halt execution and wait for the user to provide answers. Update the parcel with the user's clarifications.

### Phase 4: Planning Agent (Detailed Execution Plan)
* **Audit Goal:** Architect the solution down to the file level.
* **Target:** `docs/plans/[plan-name].md` (State: `PHASE_4`).
* **Fix:** Identify all required changes. Write a comprehensive, step-by-step execution plan including relevant code snippets, file paths, and exact instructions. Leave nothing missing. Include links to all relevant `documentation.md` files.

### Phase 5: Product Owner Review
* **Audit Goal:** Ensure the technical plan aligns with the overall application vision, business requirements, and core docs.
* **Target:** `docs/plans/[plan-name].md` (State: `PHASE_5`).
* **Fix:** A persona acting as the Product Owner reviews Phase 4. If there are misalignments with the app vision or core docs, explicitly clarify them with the user. Update the plan and check off the PO review.

### Phase 6: Senior Dev Hygiene Review
* **Audit Goal:** Enforce strict coding standards and best practices before execution begins.
* **Target:** `docs/plans/[plan-name].md` (State: `PHASE_6`).
* **Fix:** A persona acting as a Senior Developer reviews the Phase 4 plan. Check against SOLID principles, DRY, complexity limits, and testability. Demand refactors to the plan if standards aren't met. Check off the Hygiene review.

### Phase 7: Execute Changes
* **Audit Goal:** Implement the approved plan exactly as written using a fast, low-weight model session.
* **Target:** Active codebase and `docs/plans/[plan-name].md` (State: `PHASE_7`).
* **Fix:** The executor reads the plan, runs any test-first suites, and implements the required code strictly "to the letter". Check off the execution tasks in the plan as they are completed. Do not deviate from the plan.

### Phase 8: Verify Changes
* **Audit Goal:** Ensure the execution strictly matches the plan and did not break existing functionality.
* **Target:** Codebase, Tests, `docs/plans/[plan-name].md` (State: `PHASE_8`).
* **Fix:** An agent verifies all changes against the Phase 4 instructions. Run the test suite. Check for any gaps that might break functionality or leave missing pieces. If gaps exist, kick back to Phase 7. Otherwise, mark Verification as Passed.

### Phase 9: User Verification
* **Audit Goal:** Final sign-off from the user that the deployed changes meet their needs.
* **Target:** User, `docs/plans/[plan-name].md` (State: `PHASE_9`).
* **Fix:** Present the completed, verified changes to the user. Ask them to test the feature or review the code. Wait for explicit user sign-off.

### Phase 10: Wrap Up
* **Audit Goal:** Persist architectural updates and close out the parcel.
* **Target:** `docs/plans/[plan-name].md` (State: `COMPLETE`), relevant library docs.
* **Fix:** Set the plan status to `COMPLETE` and archive it. Extract any permanent architectural changes, new patterns, or schema updates and write them into the central document library (e.g., `docs/library/CONTEXT.md`).

---

## 📊 Parcel Markdown Template

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
* **Feedback:** [Alignment with app vision, docs]
* **Required Fixes:**
  - `[ ]` [Fix 1]

## 6️⃣ Phase 6: Senior Dev Hygiene Review
* **Status:** `[PENDING / REJECTED / APPROVED]`
* **Feedback:** [Comments on DRY, SOLID, best practices]
* **Required Fixes:**
  - `[ ]` [Fix 1]

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
