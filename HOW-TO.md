# How-To: Agentic Development & Documentation Lifecycle

Welcome to this base-agnostic template library. This guide details the logical workflow and methodologies for building apps and managing documentation using the agentic skills provided in this workspace.

---

## 1. Bootstrapping & Core Setup

Every new project starts with aligning on the product context and establishing a solid, standardized documentation base.

```mermaid
graph TD
    A[Start New Project] --> B[Create Vision & North Star]
    B --> C[Run Documentation Bootstrap]
    C --> D[Standardized /Docs Library Structure]
```

### Phase A: Vision & North Star
*   **Skill:** `create-app-vision-north-star`
*   **Purpose:** Synthesizes the codebase and requirements into an actionable, high-level strategic roadmap (`01-vision-north-star.md`). It aligns product objectives with engineering tasks and establishes constraints.

### Phase B: Documentation Bootstrap
*   **Skill:** `documentation-architecture-bootstrap`
*   **Purpose:** Initializes a standardized folder structure under `/docs` or `/Docs` (e.g., core contexts, architectural logs, and indices) to serve as the single source of truth for the agent.

---

## 2. Dual Agent Development Methodologies

Depending on the task's complexity, team style, or token optimization constraints, you can choose or combine two primary agentic coding patterns:

### Method A: Pass the Parcel (Stateless / Planning Mode)
*   **Skill:** `pass-the-parcel`
*   **Execution:** Highly token-efficient and modular. A single markdown plan file (`docs/plans/...`) acts as the state carrier. Agents pass the file "parcel" to the next step, ensuring clean context boundaries, minimizing token bloat, and allowing stateless, independent review cycles.

### Method B: The Multi-Stage Code Pipeline
For deeply structured, robust feature implementation, use the sequential pipeline of specialized agent personas:

```mermaid
flowchart LR
    P[code-planning] --> PO[code-product-owner-assessment]
    PO --> H[code-hygiene-architecture-review]
    H --> E[code-execution]
```

1.  **`code-planning`**: Translates high-level requests into detailed Implementation Plans (`implementation_plan.md`).
2.  **`code-product-owner-assessment`**: Audits the plan to ensure business logic is fully honored and edge cases are handled.
3.  **`code-hygiene-architecture-review`**: Audits the design for DRY principles, security, and scalable architecture.
4.  **`code-execution`**: Executes the approved plan and writes clean, production-ready code while maintaining the `task.md` TODO list.

---

## 3. Knowledge Retention & Wrap-Up

As implementation concludes, the agent must document what it learned and clean up the workspace logs.

*   **Agent Log (`AGENT.md`)**: A running chronological journal of the agent's work, current objectives, and state.
*   **`knowledge-consolidation` (Knowledge Capture)**: Periodically structures, de-duplicates, and archives local developer knowledge into indexed snippets under the App Data knowledge base, ensuring long-term context isn't lost.
*   **`agent-wrap-up`**: Runs final workspace state synchronization. It reviews modified files, writes the walkthrough (`walkthrough.md`), updates logs, and closes the active loop.

---

## 4. Pre-Deployment Validation

Before any code is pushed to production or committed to the remote repository, it must pass a strict security and quality gateway:

```mermaid
graph TD
    A[Code Changes Completed] --> B[Pre-Deployment Vibe Auditor]
    B --> C[Test-and-Deploy Skill]
    C --> D[Safe Git Push / Deploy]
```

*   **`pre-deployment-vibe-auditor`**: Scans the codebase for "vibe-coded" anomalies, architectural drift, unoptimized queries, missing error handling, or security risks.
*   **`Test-and-Deploy`**: Automates running the local test suite, executing linter rules, and verifying configurations before executing a safe, pre-validated git push or deployment.

---

This framework ensures that any app built on top of this scaffold remains clean, well-documented, and safe to deploy.
