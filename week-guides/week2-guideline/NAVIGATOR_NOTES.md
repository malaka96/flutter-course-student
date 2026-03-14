# Navigator – Teaching Notes (Week 2)

Use this document to **teach navigation first**, before building the Add Student UI. Students need to understand **push** and **pop** so that the "Add Student" button behaviour (going back) makes sense.

---

## 1. Core idea: the stack

Flutter keeps screens in a **stack** (like a stack of cards):

- **Bottom** = first screen (e.g. Dashboard / Home).
- **Top** = current screen the user sees.

```
     ┌─────────────────┐
     │  Add Student    │  ← TOP (visible)
     ├─────────────────┤
     │  Dashboard      │  ← BOTTOM
     └─────────────────┘
```

- **Navigator.push** → put a **new** screen **on top** (user goes "forward").
- **Navigator.pop** → **remove** the **top** screen (user goes "back").

---

## 2. Going to a new screen (push)

To open another screen, use **`Navigator.push`** with a **`MaterialPageRoute`**:

```dart
Navigator.push(
  context,
  MaterialPageRoute(
    builder: (context) => const SecondScreen(),
  ),
);
```

- **`context`** – needed so Flutter knows where we are in the app.
- **`MaterialPageRoute`** – builds the new screen and gives the default slide-from-right animation.
- **`builder`** – returns the widget (screen) to show.

**Where to use this:** In the **onPressed** of a button on the **current** screen (e.g. "Add Student" on the Dashboard).

---

## 3. Going back (pop)

To close the **current** screen and show the previous one:

```dart
Navigator.pop(context);
```

- Removes the **top** screen from the stack.
- The screen below becomes visible again.

**Where to use this:** In the **onPressed** of a "Back" or "Add Student" or "Cancel" button on the **new** screen.

---

## 4. Flow summary

| Action | Code | Stack change |
|--------|------|--------------|
| User taps "Add Student" on Dashboard | `Navigator.push(context, MaterialPageRoute(...))` | [Dashboard] → [Dashboard, Add Student] |
| User taps "Add Student" (submit) or "Back" on Add Student screen | `Navigator.pop(context)` | [Dashboard, Add Student] → [Dashboard] |

---

## 5. Demo: minimal Navigator on Week 2 app (copy-paste)

Use this **before** introducing the full Student Management app. It uses the existing **week-2** project (Task Manager with `HomePage`).

### Step A: Create a second screen

Create file **`lib/second_screen.dart`** and paste:

```dart
import 'package:flutter/material.dart';

class SecondScreen extends StatelessWidget {
  const SecondScreen({super.key});

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: const Text('Second Screen'),
      ),
      body: Center(
        child: Column(
          mainAxisAlignment: MainAxisAlignment.center,
          children: [
            const Text('You pushed to this screen.'),
            const SizedBox(height: 24),
            ElevatedButton(
              onPressed: () {
                Navigator.pop(context);
              },
              child: const Text('Go Back'),
            ),
          ],
        ),
      ),
    );
  }
}
```

### Step B: Add a button on HomePage that pushes

In **`lib/home_page.dart`**:

1. Add the import at the top:

```dart
import 'second_screen.dart';
```

2. Add a button inside the `Column` (e.g. after the existing `Text` widgets, before the closing `],` of `children`):

```dart
const SizedBox(height: 24),
ElevatedButton(
  onPressed: () {
    Navigator.push(
      context,
      MaterialPageRoute(
        builder: (context) => const SecondScreen(),
      ),
    );
  },
  child: const Text('Go to Second Screen'),
),
```

Run the app: tap "Go to Second Screen" → new screen appears (push). Tap "Go Back" → returns to HomePage (pop).

---

## 6. Wiring in main.dart: initial screen and (optional) named routes

The **main.dart** file configures the app's **first screen** and, if you use them, **named routes**. Both live on **MaterialApp**.

### 6.1 First screen only: use `home`

For a single starting screen (e.g. Week 2 Task Manager), set **`home`**:

```dart
MaterialApp(
  title: 'Task Manager',
  theme: ThemeData(
    colorScheme: ColorScheme.fromSeed(seedColor: Colors.blue),
    useMaterial3: true,
  ),
  home: const HomePage(),   // First screen the user sees
);
```

- **`home`** – The widget shown when the app starts (bottom of the stack).
- You still use **Navigator.push** / **Navigator.pop** from that screen to go to others.

### 6.2 Named routes: use `initialRoute` and `routes`

When you have several screens and want to refer to them by **name** (e.g. `/`, `/add`, `/students`), use **`initialRoute`** and **`routes`** instead of **`home`**:

```dart
MaterialApp(
  title: 'Student Management System',
  theme: ThemeData(
    colorScheme: ColorScheme.fromSeed(seedColor: Colors.blue),
    useMaterial3: true,
  ),
  initialRoute: '/',       // Which route is the first screen
  routes: {
    '/': (context) => const StudentDashboardScreen(),
    '/students': (context) => const StudentListScreen(),
    '/add': (context) => const AddStudentScreen(),
  },
);
```

- **`initialRoute`** – The **name** of the first route (e.g. `'/'` = dashboard).
- **`routes`** – Map of **route name → screen**. When you push a named route, Flutter looks up the name here and builds that screen.

**Important:** If you use **`routes`**, do **not** set **`home`**. Use **either** `home` **or** `initialRoute` + `routes`, not both.

### 6.3 Going to a screen by name: pushNamed

With named routes you can push by **name** instead of building the widget yourself:

```dart
// Instead of:
Navigator.push(
  context,
  MaterialPageRoute(builder: (context) => const AddStudentScreen()),
);

// You can write:
Navigator.pushNamed(context, '/add');
```

**Pop** is the same: **`Navigator.pop(context)`** (no name needed).

### 6.4 Summary

| Approach        | Use when                         | In main.dart                          |
|----------------|-----------------------------------|---------------------------------------|
| **`home`**     | One starting screen, push others  | `home: const HomePage()`              |
| **Named routes** | Multiple "entry" screens by name | `initialRoute: '/'` and `routes: { ... }` |

For the **minimal demo** (Section 5), **`home: const HomePage()`** is enough. For the **full Student Management app**, you can switch to **`initialRoute`** and **`routes`** and use **pushNamed** when you wire the dashboard and Add Student screen.

---

## 7. After this: Add Student UI

Once students understand push and pop:

- **Dashboard** will **push** to **Add Student** when they tap "Add Student".
- **Add Student** screen will have a form (name, ID, course) and a button that **pops** to go back (and later can also save the student).

The same Navigator concepts apply; the Add Student screen is just a more useful "second screen" with a form.

See **STUDENT_DEVELOPMENT_GUIDE.md** (Section 7) for navigation in the Student Management app.
