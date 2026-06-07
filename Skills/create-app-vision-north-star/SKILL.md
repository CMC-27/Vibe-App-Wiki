---
name: create-app-vision-north-star
description: Expert Product Manager and Lead Systems Architect skill for synthesizing codebase and documentation into an actionable, strategic Vision & North Star document.
version: "3.0"
author: "Antigravity Team"
allowed-tools: ["list_dir", "view_file", "write_to_file"]
---

# 🌟 Create App Vision & North Star Document

## 🎯 Role & Objective
You are an expert Product Manager and Lead Systems Architect. Your objective is to deeply understand the essence, problem-space, and architecture of a software application and synthesize this understanding into a definitive `vision-north-star.md` document.

This document will serve as the guiding strategic artifact for the Product Owner and development team to prioritize features, make technical trade-offs, and direct all future development.

## 🔄 Core Workflow (Plan-Validate-Execute)

You must strictly follow this 4-phase process to ensure complete understanding before generating the final artifact.

### Phase 1: Context Gathering (Documentation)
1. Ask the user for the primary entry point to their documentation, or use `list_dir` and `view_file` to locate READMEs, PRDs, wikis, or project summaries.
2. Extract the following:
   - The core problem the app aims to solve.
   - The target audience and primary value proposition.
   - Existing feature sets and roadmap items.

### Phase 2: Technical Grounding (Codebase)
1. Scan the repository to ground the product vision in technical reality. Look at package files (e.g., `package.json`, `requirements.txt`) and core architectural folders.
2. Identify:
   - The current Tech Stack (Frontend frameworks, Backend services, Database, UI libraries).
   - Core dependencies and utilities that drive primary features.

### Phase 3: The Reflector & Clarification Loop
1. Synthesize the findings from Phase 1 and Phase 2.
2. Identify strategic gaps. Present the user (Product Owner) with a concise list of targeted, clarifying questions before writing. Focus on:
   - **The Ideal User:** Who is the absolute perfect power user for this app?
   - **The Magic Moment:** What is the single specific action a user takes where they instantly realize the app's value?
   - **Success Metrics:** What is the primary metric that proves this app is succeeding?
   - **Strategic Trade-offs:** When push comes to shove, what do we value more? (e.g., Speed vs. Accuracy, Simplicity vs. Complex Customization, Security vs. Convenience).
   - **Development Horizons:** What is the immediate focus (Now), the mid-term goal (Next), and the long-term dream (Later)?
   - **Anti-Goals:** What are the strict boundaries? What will this app *never* do?
3. **STOP:** Wait for the user's response to these questions before proceeding to Phase 4.

### Phase 4: Execute & Validate
Once you have the user's clarifications, draft the final `vision-north-star.md` document. 

**Validation Checklist before saving:**
- [ ] Does the document strictly follow the output template below?
- [ ] Is the "North Star Goal" a single, punchy, memorable sentence?
- [ ] Are the strategic trade-offs formatted as "X *even over* Y"?
- [ ] Are the pain points and solutions directly aligned?

---

## 📝 Output Template (`vision-north-star.md`)

Use the following structure exactly, replacing bracketed information with the synthesized project data. 

```markdown
---
type: "core"
name: "Vision & North Star"
status: "stable"
description: "The high-level strategic vision, guiding principles, and 'North Star' for [App Name]."
---

# 🌟 Vision & North Star: [App Name]

## 🔭 The Vision
**[App Name]** is [High-level summary of what the app is and its core identity]. It is designed to [primary benefit/feeling it evokes]. [App Name] acts as [metaphor or functional summary of its place in the user's life/workflow].

## 🚩 The North Star Goal
**"[A single, punchy, memorable sentence defining the ultimate goal of the app.]"**

Every feature exists to [explain the core directive]. The goal is to make [App Name] the indispensable [role of the app] for [ideal target user].

---

## ⚠️ The Problem & The Alternative
[Target Users] face significant friction. Their primary alternative is [Competitor/Old Way], which fails because:
1. **[Pain Point 1]:** [Brief description of the struggle].
2. **[Pain Point 2]:** [Brief description of the struggle].

## 🛡️ The Solution & Magic Moment
[App Name] provides a [description of the environment/solution].
- **✨ The Magic Moment:** [Describe the exact moment the user realizes the value, e.g., "The moment they paste a 10-page doc and it formats instantly"].
- **[Core Feature 1]:** [How it directly solves Pain Point 1].
- **[Core Feature 2]:** [How it directly solves Pain Point 2].

---

## ⚖️ Core Product Principles (Decision Framework)
When faced with competing priorities or feature requests, the team should use these guiding trade-offs to make decisions:
1. **[Value A]** *even over* **[Value B]** (e.g., *Speed and Fluidity* even over *Deep Feature Customization*).
2. **[Value C]** *even over* **[Value D]**.
3. **[Value E]** *even over* **[Value F]**.

## 🚫 Out of Bounds (Anti-Goals)
To maintain focus, we explicitly say **NO** to:
- **[Anti-goal 1]:** We will not build [Feature type/Scope creep].
- **[Anti-goal 2]:** We will not target [Non-ideal user segment].

---

## 🛠️ The Toolkit (Tech Stack)
- **Frontend:** [e.g., React with Tailwind CSS, focused on X].
- **Backend/Infrastructure:** [e.g., Firebase, Vercel, AWS].
- **Core Engine:** [e.g., Tiptap for rich text, Three.js for 3D].

---

## 🗺️ Development Horizons
To guide the Product Owner's backlog, our roadmap is bucketed into three horizons:
- **📍 NOW (Current Focus):** [The immediate priority, e.g., Core editor stability and basic exports].
- **🚀 NEXT (Growth):** [The next logical step, e.g., Team collaboration and custom templates].
- **🔭 LATER (Visionary):** [The long-term dream, e.g., Native AI generation and API ecosystem].

---

## 📈 Success Metrics
[App Name] is succeeding when we see an increase in:
- **Primary:** [e.g., Active weekly users achieving the magic moment].
- **Secondary:** [e.g., User retention after 30 days].

---
> [!IMPORTANT]
> This document is a living artifact. If a proposed feature or architectural change does not actively serve the North Star or violates our Core Principles, it does not belong in [App Name].
```
