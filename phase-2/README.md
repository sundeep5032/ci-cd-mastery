# 🧱 Phase 2: Continuous Integration (CI) Design

## 🎯 Objective
Transitioning from manual Git usage to becoming a DevOps engineer. This document outlines the **tool-agnostic** design of our CI system.

> **The Core Mission:** "Is this change safe to merge?"

---

## 1️⃣ CI Strategy & Core Principles
CI is the automated process of validating code changes. We adhere to these golden rules:
* **Merge Safety:** Automation must prove code works before it hits `main`.
* **Fast Feedback:** CI must be fast (under 20 min). Slow CI is bypassed CI.
* **Deterministic:** Same input must always produce the same output.

### Trigger Points
| Event | Purpose |
| :--- | :--- |
| **Pull Request** | Validate code *before* it is merged. |
| **Push to Main** | Validate the final merged state. |

---

## 2️⃣ Pipeline Logical Flow
Regardless of whether we use GitHub Actions or Jenkins, the logic remains:



1. **Trigger:** PR or Push detection.
2. **Checkout:** Pulling code from the repository.
3. **Setup:** Preparing the runtime (Python/Node/Java).
4. **Dependencies:** Installing libraries (with caching enabled).
5. **Build:** Compiling and validating syntax.
6. **Test:** Running the automated suite.
7. **Package:** Creating the final artifact.
8. **Feedback:** Reporting results to the dev team.

---

## 🧪 Practical Exercise: CI Logic Definition
*This section fulfills the mandatory requirements for Phase 2.*

### Selected App: [Insert App Type - e.g., Python Flask API]

| Question | My CI Logic |
| :--- | :--- |
| **How is the app built?** | [e.g., Install requirements.txt and compile bytecode] |
| **How are tests run?** | [e.g., Running `pytest` on the /tests directory] |
| **What is the artifact?** | [e.g., A Docker Image or a ZIP file] |
| **How long should CI take?** | [e.g., Target: < 3 minutes] |
| **What should break CI?** | [e.g., Linting errors, failing unit tests, build errors] |

---

## 🏗 The Testing Pyramid
Our CI pipeline prioritizes the base of the pyramid for speed and reliability:



* **Unit Tests:** Mandatory (Runs in CI).
* **Integration Tests:** Fast checks only (Runs in CI).
* **End-to-End/Manual:** Excluded from CI to prevent slowness.

---

## ⚠️ Quality Gates (What Makes CI Fail)
A "Green" CI is a contract of quality. The pipeline **must fail** if:
* [ ] The code fails to compile or has syntax errors.
* [ ] Any unit test fails.
* [ ] Dependency vulnerabilities are found.
* [ ] Static analysis/Linting thresholds are not met.

---

## ✅ Phase 2 Completion Checklist
- [ ] I can design a CI pipeline without specific tools.
- [ ] I understand that CI builds artifacts, but does NOT deploy them.
- [ ] I have defined my "Quality Gates."
- [ ] My logic includes dependency caching.

---

**Next Phase:** Connect Git → CI → Automation via GitHub Actions.
**When ready, reply:** `"Start Phase 3"`
