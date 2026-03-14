# Contributing – Git workflow for this course

This guide explains the **Git workflow** you should follow when working on this repository. We use a simple **feature-branch + pull request** workflow so everyone’s work stays organized and reviewable.

## Workflow in short

- Update your local `main`
- Create a feature branch
- Make small commits with clear messages
- Push your branch
- Open a pull request (PR) to `main`
- Ensure CI is green, then merge

Avoid committing directly to `main` for shared work.

## Create a feature branch

Start from an up-to-date `main`:

```bash
git checkout main
git pull origin main
```

Create and switch to a new branch:

```bash
git checkout -b feature/add-login-screen
```

Branch naming ideas:

- `feature/...` for new features
- `fix/...` for bug fixes
- `docs/...` for documentation

## Commit message format

Write commit messages that are easy to understand.

**Format:**

```
Short summary (imperative, no period)

Optional details: what changed and why.
```

Examples:

- `Add login screen UI`
- `Fix validation on empty task title`
- `Add Flutter CI workflow`

## Open a pull request

Push your branch:

```bash
git push -u origin feature/add-login-screen
```

Then on GitHub:

- Open a **Pull Request** targeting `main`
- Add a clear title and short description
- Wait for **CI checks** to finish
- If something fails, fix it and push again (the PR updates automatically)

## What to do if CI fails

CI failures are normal while learning. Read the logs in the GitHub **Actions** tab (or in the PR checks), fix the issue locally, then commit and push again.

