# 📋 AkiraFlex Kanban Board

This Kanban board organizes the technical deliverables of AkiraFlex, a modular business management platform. It focuses exclusively on development, architecture, and technical documentation tasks.

## 🧩 Board Structure

The board consists of the following columns:

### Notes

- Internal documentation, rules, and team references (e.g., this file).

### Backlog

- Unprioritized ideas, future features, or exploratory tasks.

- Only moved to **To Do** when ready for execution.

### To Do

- Prioritized tasks grouped by domain.

- Must include English technical labels and internal notes.

### In Progress

- Actively developed tasks.

- One active task per contributor unless justified.

### Blocked

- Tasks that cannot progress due to external or internal dependencies.

- Must be explicitly marked and linked to the blocking issue.

### Review / QA

- Tasks pending validation or testing.

- Must include evidence (commits, screenshots, links) and a completed checklist.

### Done

- Approved and validated tasks.

- Cannot be moved here without prior review.

### Parking Lot

- Deferred features or items outside the MVP scope.

- Reviewed during planning sessions.

## 🛠️ Task Requirements

All technical variables and internal notes must be in English.

Each task must include:

- Clear, concise title

- Contextual description and objective

- Labels for module, task type, and priority

- Assigned contributor

Additional rules:

- Tasks must be modular and deliverable, not generic.

- Avoid moving tasks without updating their content.

- If a task blocks another, it must be explicitly indicated.

## 🚦 Workflow Rules

### ✅ To Do

- Max 3 tasks per domain

- Total board limit: 9 tasks

- Tasks must be well-defined and ready for execution

### 🚧 In Progress

- Max 2–3 tasks per developer

- Max 5–6 active tasks in total

- Blocked tasks must be moved to the **Blocked** column

### 🧪 Review / QA

- Tasks must include validation or testing criteria

- Peer review or self-assessment required before moving to **Done**

### 🔄 General Flow

- Tasks must be updated at least once per working day

- Status changes must reflect actual progress, not intent

- Reviews must be objective and based on evidence

- Any major change must be documented within the task

## 🏷️ Labeling Conventions

Use GitHub labels to categorize tasks clearly.

- Module examples: `module:auth`, `module:dashboard`, `module:company`, `module:shared-lib`, etc.

- Type examples: `type:feature`, `type:bug`, `type:refactor`, `type:doc`, `type:infra`

- Priority examples: `priority:high`, `priority:medium`, `priority:low`

- Status examples: `status:blocked`, `status:needs-review`, `status:ready-for-dev`

## 🏷️ Technical Tags

| Tag     | Scope / Usage                                                | Example Use Case                              |
|---------|--------------------------------------------------------------|-----------------------------------------------|
| Gateway | External service integrations or module bridges              | Auth proxy to external identity provider      |
| DB      | Database modeling, queries, and business rules               | Create tenant-aware table with RLS            |
| API     | Controllers, endpoints, and backend logic                    | Implement company registration endpoint       |
| UI      | Frontend components and user experience                      | Build dashboard layout with charts            |
| Core    | Reusable system logic across modules                         | Shared validation service for DTOs            |
| Test    | Unit, integration, or functional testing                     | Write Jest tests for auth flow                |
| Docs    | Technical, architectural, or functional documentation        | Update README with Kanban rules               |

## 📁 Naming Conventions

- All task titles and descriptions must be written in English.

- Use clear, action-oriented names (e.g., _Create role table_, _Implement RLS for tenant isolation_).

- Avoid vague titles like _Fix bug_ or _Update stuff_.

## ✅ Commit Convention

Use a simple, readable format: `TYPE: KEY - short message`

Examples:

- `feat: AF-101 - add company registration form`

- `fix: AF-087 - resolve login redirect issue`

- `refactor: AF-112 - simplify dashboard layout logic`

- `docs: AF-000 - add kanban board rules to Notes column`

## 👥 Team Info

This section provides the core information the team needs to collaborate effectively on the Kanban board and in the repository.

### Team Roster & Roles

- Product Owner / Coordinator: defines priorities and accepts scope decisions.
- Tech Lead / Architect: approves designs, enforces architecture decisions and reviews complex PRs.
- Backend Developers: implement APIs, DB models and business logic.
- Frontend Developers: UI components, user flows and integration with APIs.
- QA / Testers: write and run test plans, verify acceptance criteria.
- DevOps / Infra: CI/CD, packages publishing, environment management.

> Each task should include the assigned contributor (GitHub handle) and a reviewer tag.

### Contacts & Channels

- Primary chat: Slack / Teams channel (e.g., `#akira-flex-dev`)
- Email: `team@akira.example.com` (for formal notifications)
- Urgent ops: use the on-call paging channel and tag the DevOps owner.

### Working Hours & Standups

- Core overlap window: 09:00 — 16:00 (local timezone) — keep at least 4 hours overlap for handoffs.
- Daily standup: 10:00 (15 min) — update Kanban card status before the standup.
- Weekly planning: Mon 09:30 — backlog grooming and To Do shaping.

### Onboarding Checklist (new contributors)

- Read this Kanban file and project README
- Setup local dev environment (see README / CONTRIBUTING)
- Run tests and build locally
- Add yourself to the Team Roster in this file (GitHub handle + role)
- Ask a Tech Lead for a 1:1 walkthrough of the architecture

### Pull Request & Code Review Rules

- PR title format: `TYPE: AF-<id> - short message` (see Commit Convention)
- PR must reference the Kanban card (ID or link) and include a short testing checklist
- Add at least one reviewer from the owning module (module:label)
- Small, focused PRs preferred (max ~300 lines of changes when possible)
- Review turnaround: aim for <48 hours during working days
- Include screenshots or recordings for UI changes

### Branching & Release

- Branches: `main` (production), `develop` (optional integration), `feature/AF-xxx-description`
- Semantic-release manages tags and package publishing from `main` after CI passes
- For urgent fixes target `main` with a hotfix branch and include justification in the PR

### Escalation & Support

- If a task is blocked for >48 hours, move it to **Blocked** and tag the blocking party
- For critical blocker (production or release), escalate to Tech Lead and DevOps, and update the Kanban card with a clear impact statement

---

_Last updated: keep this file updated when team composition or rules change._
