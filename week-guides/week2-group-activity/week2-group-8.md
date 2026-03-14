# Week 2 – Group 8 Task

**Branch to create:** `group-8/test-scaffold`

---

## Your goal

Add **one new assertion** in the widget test: check that the screen has a **Scaffold** (the main layout widget used by the home page).

---

## Steps

1. Make sure you are on `week-2` and up to date:
   ```bash
   git checkout week-2
   git pull origin week-2
   ```

2. Create and switch to your group branch:
   ```bash
   git checkout -b group-8/test-scaffold
   ```

3. Open `task_manager_app/test/widget_test.dart`. Add an assertion that finds a `Scaffold`:
   ```dart
   expect(find.byType(Scaffold), findsOneWidget);
   ```
   Add `import 'package:flutter/material.dart';` at the top if it is not already there.

4. Run tests:
   ```bash
   cd task_manager_app
   flutter pub get
   flutter test
   ```

5. Commit and push:
   ```bash
   cd ..
   git add task_manager_app/test/widget_test.dart
   git commit -m "Add test for Scaffold (Group 8)"
   git push -u origin group-8/test-scaffold
   ```

6. On GitHub, open a **Pull Request** from `group-8/test-scaffold` to `week-2`. Watch the **Actions** tab until CI finishes.

---

## Done when

- Your PR is open and CI has run (and passed).
- You can explain what a Scaffold is and why it is useful to test for it.
