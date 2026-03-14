# Student Development Guide

**Mobile Development Industry Course**

This guide helps students implement features for the **Student Management System App**.  
If you get stuck, follow the guidelines below.

**Week 2 reference notes (in this folder):**

- **INTRODUCTION_TO_DART.md** – Dart basics (variables, types, functions, classes, `const`) – do this first.
- **NAVIGATOR_NOTES.md** – Navigation: stack, push, pop, and wiring in `main.dart`.
- **SCAFFOLD_AND_WIDGETS_NOTES.md** – Scaffold parameters, `child` vs `children`, layout pattern.

---

## 1. Basic Flutter Project Structure

Inside your project you will typically see:

```
lib/
├── main.dart
├── screens/
├── widgets/
└── models/
```

**Explanation:**

- **screens** → pages of the application  
- **widgets** → reusable UI components  
- **models** → data structures  

**Example:** `lib/screens/student_list_screen.dart`

---

## 2. Creating a Simple UI Screen

Example structure for a page:

```
Scaffold
├── AppBar
└── Body
```

**Example Flutter code:**

```dart
import 'package:flutter/material.dart';

class StudentListScreen extends StatelessWidget {
  const StudentListScreen({super.key});

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: const Text("Students"),
      ),
      body: const Center(
        child: Text("Student List Screen"),
      ),
    );
  }
}
```

---

## 3. Creating a ListView

A **ListView** is used to display a list of items.

**Example:**

```dart
ListView.builder(
  itemCount: students.length,
  itemBuilder: (context, index) {
    return ListTile(
      title: Text(students[index].name),
      subtitle: Text(students[index].course),
    );
  },
)
```

This will generate a scrollable list.

---

## 4. Example Student Model

**Example data model:**

```dart
class Student {
  final String name;
  final String id;
  final String course;

  Student({
    required this.name,
    required this.id,
    required this.course,
  });
}
```

**Example data:**

```dart
final students = [
  Student(name: "John Doe", id: "S001", course: "CS"),
  Student(name: "Jane Smith", id: "S002", course: "IT"),
];
```

---

## 5. Creating a Form (Add Student)

**Example input fields:**

```dart
TextField(
  decoration: InputDecoration(
    labelText: "Student Name",
  ),
)
```

**Example layout:**

```dart
Column(
  children: [
    TextField(...),
    TextField(...),
    ElevatedButton(
      onPressed: () {},
      child: const Text("Add Student"),
    ),
  ],
)
```

---

## 6. Mock UI Example – Student Dashboard Screen

```
┌─────────────────────────────────────┐
│   Student Management System         │
├─────────────────────────────────────┤
│                                     │
│         [ Add Student ]             │
│                                     │
│  (List of students or empty state)  │
│                                     │
└─────────────────────────────────────┘
```

Students should aim to build something similar to this layout.

---

## 7. Navigation Between Screens

**Example navigation:**

```dart
Navigator.push(
  context,
  MaterialPageRoute(
    builder: (context) => const StudentListScreen(),
  ),
);
```

This will move to another page.

---

## 8. Git Workflow (Important)

Each group must work in a **feature branch**.

**Example:**

```bash
git checkout -b feature/student-list
```

**Commit changes:**

```bash
git add .
git commit -m "feat: implement student list UI"
```

**Push to GitHub:**

```bash
git push origin feature/student-list
```

Then create a **Pull Request** to merge into `main` (or `week-2`).

---

## 9. What To Do If You Get Stuck

Try the following:

1. Check the **Flutter documentation**  
2. Ask your **teammates**  
3. **Search** the error message  
4. Ask the **lecturer** for guidance  

**Remember:** Learning to solve problems is part of becoming a developer.

---

## 10. Final Goal

By completing this project you will learn:

- Flutter UI development  
- Git workflow  
- Branching strategy  
- Pull Requests  
- Continuous Integration with GitHub Actions  

Your final output should be a **working Student Management App**.

---

## How This Helps You During the Lecture

If a group struggles you can simply say:

> **“Check the Student Development Guide section for ListView.”**

This avoids stopping the entire class.
