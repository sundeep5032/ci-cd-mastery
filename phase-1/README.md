# 🧱 PHASE 1 — GIT + CI/CD WORKFLOWS
> **Status:** Industry-grade · DevOps mindset · Zero → Pro

## 🎯 Phase 1 Goal
By the end of this phase, I will be able to:
- ✅ Design a production-grade Git workflow.
- ✅ Explain why a branching strategy exists.
- ✅ Use PRs, checks, and protections correctly.
- ✅ Understand where CI/CD hooks into Git.

---

## 1️⃣ Why Git Workflow Matters for CI/CD
CI/CD pipelines are triggered by specific Git events: `push`, `pull_request`, `merge`, and `tag`. 

If Git workflow is messy, pipelines trigger randomly, production breaks, and rollbacks become impossible. 
> 📌 **Industry Truth:** "CI/CD automates your chaos if Git is chaotic."

---

## 2️⃣ Branching Strategies
### 🔹 Trunk-Based Development (Modern Standard)
*Used by Google, Netflix, and modern SaaS teams.*
- **Structure:** `main` branch is the source of truth. Features are built on short-lived `feature/*` branches.
- **Rules:** `main` is always deployable. Feature branches live for hours/days, not weeks.
- **Benefits:** Faster delivery, fewer merge conflicts, CI/CD friendly.

### 🔹 GitFlow (Legacy/Structured)
- **Structure:** `main`, `develop`, `feature/*`, `release/*`, `hotfix/*`.
- **Context:** Good for structured, scheduled releases, but often too slow for modern CI/CD.

---

## 3️⃣ Pull Requests (PR) — The Heart of CI/CD
In DevOps, a PR is a **Quality Gate**. Before a merge is allowed:
- [ ] **Build** must pass.
- [ ] **Tests** must pass.
- [ ] **Security scans** must pass.
- [ ] **At least 1 approval** from a peer.

---

## 4️⃣ Protected Branches (Non-Negotiable)
The `main` branch must be locked down in every professional environment:
1. **No direct pushes:** All changes must come through a PR.
2. **Status Checks:** CI must be green before the "Merge" button unlocks.
3. **Review Required:** A human must look at the code.

---

## 5️⃣ Commit Message Standards
We follow **Conventional Commits** to ensure automated versioning and clean history.

| Type | Description | Example |
| :--- | :--- | :--- |
| `feat` | A new feature | `feat: add user login API` |
| `fix` | A bug fix | `fix: resolve build failure` |
| `chore` | Maintenance | `chore: update dependencies` |

---

## 6️⃣ Where CI/CD Hooks In
| Git Event | Pipeline Action |
| :--- | :--- |
| **Push to Feature** | Optional CI (Linting) |
| **PR Opened** | Full CI (Build + Test) |
| **PR Merged** | CD to Dev/Staging |
| **Tag Created (v1.0)** | CD to Production |

---

## 🧪 Phase 1 Practical Exercise
- [x] Create repository: `ci-cd-mastery`
- [x] Enable Branch Protection on `main`
- [x] Practice Feature Branching: `feature/test-pipeline`
- [x] Use Conventional Commits for every change

---

## 🏁 Phase 1 Completion Checklist
- [ ] I understand why trunk-based is preferred for CI/CD.
- [ ] I know how PRs act as checkpoints for automation.
- [ ] I can explain the difference between a `push` trigger and a `tag` trigger.

---
**Next Step:** [Phase 2 — CI Fundamentals (Build & Test Automation)](#)
