# CI (Continuous Integration) – Quick Reference

A short pointer for students. Full explanation is in the repository root:

- **../../CI_EXPLANATION.md** – What is CI? What is GitHub Actions? What runs on push/PR?
- **../../CICD_FOR_STUDENTS.md** – Full teaching guide: CI/CD flow, CI vs CD, live demo tips.

In short: when you push code or open a Pull Request, GitHub Actions runs `flutter pub get`, `flutter analyze`, `flutter test`, and a build. Green = passed, red = fix and push again.
