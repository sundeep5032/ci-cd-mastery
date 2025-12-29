🧱 PHASE 3 — GITHUB ACTIONS (CORE CI IMPLEMENTATION)
🎯 Phase 3 Goal

By the end of this phase, you will be able to:

✅ Write GitHub Actions workflows from scratch
✅ Explain every line in a workflow file
✅ Design PR-based CI pipelines
✅ Use jobs, steps, runners, secrets, caching
✅ Debug real CI failures confidently

If you master Phase 3, you can already pass junior → mid DevOps interviews.
0️⃣ Mental Model (DO NOT SKIP)

Always think like this:

Git event
   ↓
Workflow (.yml)
   ↓
Jobs (parallel)
   ↓
Steps (sequential)
   ↓
Actions / shell commands
   ↓
Runner (VM)


If this model is clear, GitHub Actions becomes easy.

1️⃣ Repo Preparation (VERY IMPORTANT)

Use the repo you created earlier:

ci-cd-mastery


Inside it, create this folder structure:

.github/
  workflows/


This folder is mandatory.
GitHub Actions will ignore everything else.

2️⃣ Your First Workflow (MINIMAL CI)

Create a file:

.github/workflows/ci.yml

🔹 Basic Workflow Skeleton
name: CI Pipeline

on:
  pull_request:
    branches: [ main ]

jobs:
  ci:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout code
        uses: actions/checkout@v4

      - name: Run CI
        run: echo "CI is running"

What Just Happened?

on → trigger (PR to main)

jobs.ci → one job

runs-on → GitHub-hosted runner

steps → tasks executed sequentially

📌 Industry Rule

CI should always run on Pull Requests.

3️⃣ Understanding Runners (CRITICAL)
What is ubuntu-latest?

Ephemeral VM

Fresh environment every run

Preinstalled tools

📌 Important:

Never rely on state from previous runs.

4️⃣ Checkout Step (MANDATORY)

Without this:
❌ No code
❌ CI fails

- uses: actions/checkout@v4


This clones your repo into the runner.

5️⃣ Adding a Real Build Step

Let’s assume a Node.js app (concept is same for any language).

Example Build Steps
- name: Setup Node
  uses: actions/setup-node@v4
  with:
    node-version: 18

- name: Install dependencies
  run: npm install

- name: Run build
  run: npm run build


📌 Key Idea:

Setup runtime → install deps → build

6️⃣ Adding Tests (QUALITY GATE)
- name: Run tests
  run: npm test


📌 CI Behavior:

If tests fail → pipeline fails

Merge blocked automatically

This is the core value of CI.

7️⃣ Full CI Workflow (Industry-Style)
name: CI Pipeline

on:
  pull_request:
    branches: [ main ]

jobs:
  ci:
    runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@v4

      - uses: actions/setup-node@v4
        with:
          node-version: 18

      - name: Install dependencies
        run: npm install

      - name: Build
        run: npm run build

      - name: Test
        run: npm test


This is real CI, not a demo.

8️⃣ Jobs & Dependencies (ADVANCED CI)

Split build and test:

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - run: npm install
      - run: npm run build

  test:
    runs-on: ubuntu-latest
    needs: build
    steps:
      - uses: actions/checkout@v4
      - run: npm test


📌 Best Practice:

Separate concerns, but don’t overcomplicate.

9️⃣ Caching Dependencies (PRO LEVEL)
- uses: actions/cache@v4
  with:
    path: ~/.npm
    key: ${{ runner.os }}-npm-${{ hashFiles('package-lock.json') }}


📌 Why?

Faster builds

Lower cost

Better developer experience

🔟 Debugging CI Failures (REAL SKILL)

When CI fails:

Read logs top → bottom

Identify failing step

Reproduce locally

Fix, push, rerun

📌 Interview Gold:

“I debug CI by reproducing failures locally.”

🧪 Phase 3 Mandatory Exercise

Do this now:

1️⃣ Add .github/workflows/ci.yml
2️⃣ Trigger CI via Pull Request
3️⃣ Break a test intentionally
4️⃣ Watch CI fail
5️⃣ Fix it and watch CI pass

If you can do this, you truly understand CI.

✅ Phase 3 Completion Checklist

✔ You understand workflows, jobs, steps
✔ You can write CI YAML from scratch
✔ You know how CI blocks merges
✔ You can debug CI failures
✔ You used caching