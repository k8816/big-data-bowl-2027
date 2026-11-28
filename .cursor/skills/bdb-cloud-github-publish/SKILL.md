---
name: bdb-cloud-github-publish
description: Standardize how cloud agents publish Big Data Bowl 2027 changes to GitHub — branch naming, discretionary commits/PRs, targeting kevin_branch1 never main, and what to tell Kevin at each step. Use when a cloud/VM agent may commit, push, or open a PR for this repo.
---

# BDB 2027 cloud agent GitHub publish

Aligned with `.cursor/rules/personal-bdb2027.mdc`. Applies when work runs on a **virtual machine / remote checkout** and may land on GitHub. Local-only Mac edits skip this skill unless Kevin asks to publish.

## Hard rules

- Never commit, push, or open a PR that targets **`main`**.
- Day-to-day integration branch is **`kevin_branch1`**.
- When publishing, use a branch named **`kevin_cursor_agent_branch_<short-slug>`**.
- Pull request **base = `kevin_branch1`** (never `main`) — only when a PR is warranted (see below).
- State clearly after each publish step that work happened on the **VM / remote checkout**, not Kevin’s Mac, unless that step was local.

## Discretion (do not automate by default)

### Commits

- Commits are **discretionary**. Use judgment: commit when changes should be saved on the agent branch; leave temporary/exploratory work **uncommitted** when a commit would add noise or Kevin has not asked to keep it.
- Asking for a code change is **not** by itself an order to commit.

### Pull requests

- PRs are **not automatic**. Asking for a change does **not** mean open a PR.
- Open a PR only when it is clearly warranted (e.g. Kevin asks to publish/review/merge, or the change is ready for him to merge onto `kevin_branch1` and he expects a PR).
- Prefer reporting the branch (and offering a PR) over opening one unprompted.

## Steps (when publishing from the cloud)

### 1. Branch (when saving work toward GitHub)

1. Start from up-to-date `kevin_branch1`.
2. Create/switch to `kevin_cursor_agent_branch_<short-slug>`.
3. Tell Kevin: branch name, that it was created on the **VM / remote checkout**, base will be `kevin_branch1`.

### 2. Commit (only when discernment says save)

1. Stage only intentional files (never `Data/`, `DerivedData/`, or competition CSVs).
2. Commit with a clear message.
3. Tell Kevin: short hash, message summary, **VM / remote checkout**, agent branch. If leaving uncommitted, say that plainly too.

### 3. Push (when the branch should be on GitHub)

1. Push only the agent branch (`git push -u origin HEAD` or the explicit name).
2. Never push to `main` or force-push `kevin_branch1` unless Kevin explicitly asks.
3. Tell Kevin: remote branch name/URL, push was from the **VM / remote checkout**.

### 4. Pull request (only when warranted)

1. Open a PR with **base `kevin_branch1`** and head = agent branch — **only if** discernment (or Kevin) says a PR is needed.
2. PR body: what changed, how to verify, risks; note Data/DerivedData were not committed.
3. Tell Kevin: PR URL, base/head, merge is on `kevin_branch1` when he is ready. If no PR, say so and give the branch name instead.

### 5. After a PR exists

1. Do not merge unless Kevin asks.
2. If he declines a PR, follow his direction; never retarget to `main`.

## What to tell Kevin (checklist)

- **Where:** “This was on the **virtual machine / remote checkout**, not your Mac.”
- **Branch:** exact `kevin_cursor_agent_branch_*` name.
- **PR:** link + “base is `kevin_branch1`, not `main`” — only when a PR exists.
- **Commit status:** committed vs still uncommitted, in plain language.

## Out of scope

- Local Mac-only writes Kevin does not want on GitHub.
- Pasting competition CSV rows into chats.
- Reading ignored paths (`Data/`, `DerivedData/`, `notebooks/user_dev/`, `notebooks/cursor_user_run/`).
