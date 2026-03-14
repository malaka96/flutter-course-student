# Scaffold and Widget Layout – Quick Reference

Use this note when introducing **Scaffold**, **parameters**, and the **child vs children** pattern. Helps avoid mistakes like putting `children` on Scaffold or using `margin` as a function.

---

## 1. What is Scaffold?

**Scaffold** is the basic layout structure for a full screen. It gives you places to put an app bar, the main content, buttons, and drawers.

---

## 2. What can go inside Scaffold? (Parameters)

Scaffold has **named parameters**. You only use the ones you need.

| Parameter | Type | What it is |
|-----------|------|------------|
| **appBar** | `AppBar?` | Bar at the top (title, actions, back button). Optional. |
| **body** | `Widget` | The main content of the screen. **Required** if you don't use a different structure. Usually **one** widget (e.g. `Center`, `Column`, `ListView`). |
| **floatingActionButton** | `Widget?` | A floating button (e.g. "+" to add a task). Optional. |
| **bottomNavigationBar** | `Widget?` | Bar at the bottom (tabs, navigation). Optional. |
| **drawer** | `Widget?` | Slide-out menu from the left. Optional. |
| **backgroundColor** | `Color?` | Background color of the scaffold. Optional. |

**Example:**

```dart
Scaffold(
  appBar: AppBar(
    title: const Text('Task List'),
  ),
  body: Center(
    child: const Text('Hello'),
  ),
  floatingActionButton: FloatingActionButton(
    onPressed: () {},
    child: const Icon(Icons.add),
  ),
)
```

**Important:** **`body`** takes **exactly one** widget. It does **not** have a **`children`** parameter. To show multiple widgets, put them inside a **Column** or **ListView** and pass that as `body`.

---

## 3. Child vs children – the pattern

Many layout widgets follow one of two patterns:

### 3.1 Widgets with **one** child: `child:`

These wrap **a single** widget. Use **`child:`** (singular).

| Widget | Parameter | Use |
|--------|-----------|-----|
| **Padding** | `padding`, **`child`** | Space around one widget. |
| **Center** | **`child`** | Center one widget. |
| **Container** | `margin`, `padding`, **`child`** | Decoration, size, margin around one widget. |
| **Scaffold** | **`body`** (one widget) | The main area of the screen. |
| **ElevatedButton** | `onPressed`, **`child`** | Button with one label/icon. |

**Example:**

```dart
Center(
  child: Padding(
    padding: const EdgeInsets.all(16),
    child: Container(
      margin: const EdgeInsets.all(8),
      child: const Text('Hello'),
    ),
  ),
)
```

### 3.2 Widgets with **multiple** children: `children:`

These arrange **a list** of widgets. Use **`children:`** (plural) and a **list** `[ ... ]`.

| Widget | Parameter | Use |
|--------|-----------|-----|
| **Column** | **`children`** | Stack widgets **vertically**. |
| **Row** | **`children`** | Place widgets **horizontally**. |
| **ListView** | **`children`** | Scrollable list of widgets. |
| **Stack** | **`children`** | Overlay widgets on top of each other. |

**Example:**

```dart
Column(
  children: [
    const Text('First'),
    ElevatedButton(onPressed: () {}, child: const Text('Click')),
    const Text('Third'),
  ],
)
```

---

## 4. Combining: body has one widget, that widget can have children

**Scaffold** has **`body:`** (one widget). That one widget is often a **Column** or **ListView**, which **have** **`children:`**.

```
Scaffold
  body: Column          ← one widget for body
          children: [   ← list of widgets inside Column
            Text(...),
            ElevatedButton(...),
          ],
```

**Correct:**

```dart
Scaffold(
  body: Column(
    children: [
      const Text('Task List Page'),
      ElevatedButton(
        onPressed: () => Navigator.pop(context),
        child: const Text('Go Back'),
      ),
    ],
  ),
)
```

**Wrong:**

```dart
Scaffold(
  body: children: [ ... ]   // ❌ Scaffold has no "children". Use body: Column(children: [ ... ])
)
```

---

## 5. Quick rules

1. **Scaffold** → use **`body:`** with **one** widget (e.g. `Center`, `Column`, `ListView`).
2. **Single widget to wrap?** → use **`child:`** (Padding, Center, Container, etc.).
3. **Several widgets in a row or column?** → use **`children:`** inside **Column**, **Row**, or **ListView**.
4. **Margin** → use **`Container(margin: EdgeInsets.xxx, child: ...)`**, not a function called `margin`.
5. **Padding** → use **`Padding(padding: EdgeInsets.xxx, child: ...)`**.

---

See **STUDENT_DEVELOPMENT_GUIDE.md** (Section 2) for a full screen example and **NAVIGATOR_NOTES.md** for navigation.
