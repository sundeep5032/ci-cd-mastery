# 🧱 PHASE 3: GitHub Actions (Core CI Implementation)

## 🎯 Phase 3 Goal
By the end of this phase, you will be able to:
* ✅ **Write** GitHub Actions workflows from scratch.
* ✅ **Explain** every line in a workflow file.
* ✅ **Design** PR-based CI pipelines.
* ✅ **Use** jobs, steps, runners, secrets, and caching.
* ✅ **Debug** real CI failures confidently.

> [!TIP]
> **Career Note:** If you master Phase 3, you are prepared to pass junior → mid-level DevOps interviews.

---

## 0️⃣ Mental Model (DO NOT SKIP)
Always visualize the flow of execution:

**Git Event** (e.g., Push/PR)  
&nbsp;&nbsp;&nbsp;&nbsp;↓  
**Workflow** (`.yml` file)  
&nbsp;&nbsp;&nbsp;&nbsp;↓  
**Jobs** (Run in parallel by default)  
&nbsp;&nbsp;&nbsp;&nbsp;↓  
**Steps** (Run sequentially)  
&nbsp;&nbsp;&nbsp;&nbsp;↓  
**Actions / Shell Commands** &nbsp;&nbsp;&nbsp;&nbsp;↓  
**Runner** (The VM where it all happens)

---

## 1️⃣ Repo Preparation
Inside your `ci-cd-mastery` repository, you must create the following structure. **GitHub Actions will ignore any workflows not in this specific folder.**

```bash
.github/
  workflows/
    ci.yml
