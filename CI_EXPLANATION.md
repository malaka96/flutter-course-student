# CI (Continuous Integration) – Beginner Guide

This file explains what CI is and how it works in this repository.

## What is CI?

**Continuous Integration (CI)** means we automatically run checks every time code changes.

Instead of waiting until the end of the week (or the end of the project) to find problems, CI helps us find problems early.

## What is GitHub Actions?

**GitHub Actions** is a tool inside GitHub that runs automated workflows.

Workflows are defined in YAML files inside:

```
.github/workflows/
```

## What happens when you push code?

When you:

- push to `main`, or
- open/update a pull request (PR) targeting `main`

GitHub Actions runs our **Flutter CI** workflow.

In this repository, the workflow:

1. Checks out the code
2. Installs Flutter
3. Runs `flutter pub get`
4. Runs `flutter analyze`
5. Runs `flutter test`
6. Attempts to build the app

If all steps pass, the run is **green**. If any step fails, it is **red**.

## Why builds and tests matter in real teams

In real software teams:

- many people change the same codebase
- mistakes happen (even to experienced developers)

Automated tests and builds help teams:

- catch errors before merging code
- keep the `main` branch stable
- release software with more confidence

CI does not guarantee “no bugs”, but it catches many common problems early (broken builds, failed tests, analysis warnings/errors).

---

**For lecturers:** A longer teaching guide with the full CI/CD flow, CI vs CD, and live-demo tips is in **CICD_FOR_STUDENTS.md**.
