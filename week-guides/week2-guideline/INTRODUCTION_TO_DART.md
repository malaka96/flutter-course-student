# Introduction to Dart – Basics for Flutter (Week 2)

Use this note **at the very beginning** of the Flutter part of the session. It covers just enough Dart to read and write simple Flutter code: variables, types, functions, classes, and `const`.

---

## 1. Variables and types

Dart is **statically typed**: every variable has a type (you can omit it and use **type inference**).

```dart
String name = 'Alice';
int count = 42;
bool isActive = true;
double price = 9.99;
```

**Type inference** (no type written – Dart infers it):

```dart
var message = 'Hello';   // Dart infers String
var number = 10;        // Dart infers int
```

**`final`** – assign once, then cannot change:

```dart
final title = 'Task Manager';
```

---

## 2. Strings

```dart
String a = 'Single quotes';
String b = "Double quotes";
String combined = 'Hello, $name';           // String interpolation
String expression = 'Result: ${1 + 2}';     // Any expression in ${ }
```

---

## 3. Functions

**With return type and parameters:**

```dart
int add(int a, int b) {
  return a + b;
}
```

**Short form (arrow function) when the body is one expression:**

```dart
int add(int a, int b) => a + b;
```

**No return value** – use **`void`**:

```dart
void printMessage(String msg) {
  print(msg);
}
```

**Named parameters** (very common in Flutter widgets):

```dart
void showDialog({required String title, String? message}) {
  // title is required; message is optional (can be null)
}
```

In Flutter you see this all the time: **`child: Text('Hi')`**, **`padding: EdgeInsets.all(16)`** – those are named parameters.

---

## 4. Classes – the basics

A **class** groups data and behaviour. **Constructor** names the class.

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

- **`required`** – caller must pass that argument.
- **`this.name`** – assigns the parameter to the field **name**.

**Creating an instance:**

```dart
var student = Student(name: 'Alice', id: 'S001', course: 'CS');
```

In Flutter, **widgets are classes**: **`Text('Hello')`**, **`ElevatedButton(...)`** create instances of the **Text** and **ElevatedButton** classes.

---

## 5. const – compile-time constants

**`const`** means: "fixed at compile time." Use it for values that never change.

```dart
const int maxItems = 100;
const String appTitle = 'Task Manager';
const padding = EdgeInsets.all(16);   // Same object reused
```

**`const`** constructors (Flutter widgets):

```dart
const Text('Home Page')
const EdgeInsets.all(16)
```

**Rule:** If a widget has **no callbacks** (no `onPressed`, no `onTap`) and all its arguments are constant, you can mark it **`const`**. If it has a callback or non-constant data, **don't** use **`const`** on that widget.

---

## 6. Null safety (brief)

By default, variables **cannot** be **null** unless you say so.

```dart
String name = 'Alice';
name = null;   // ❌ Error: String can't be null
```

**Nullable type** – add **`?`**:

```dart
String? nickname = null;   // OK
nickname = 'Al';          // OK
```

**Accessing nullable values:** use **`!`** only if you're sure it's not null, or **`?.`** for safe access:

```dart
int? length = nickname?.length;   // null if nickname is null
```

---

## 7. Collections – List and Map

**List** – ordered sequence:

```dart
List<String> names = ['Alice', 'Bob', 'Carol'];
names.add('Dave');
int count = names.length;
String first = names[0];
```

**Map** – key–value pairs:

```dart
Map<String, int> ages = {
  'Alice': 20,
  'Bob': 22,
};
int? aliceAge = ages['Alice'];
```

In Flutter, **`children: [ ... ]`** is a **List** of widgets.

---

## 8. What you'll see in Flutter code

| Dart concept    | Example in Flutter                    |
|-----------------|----------------------------------------|
| Class + constructor | `Scaffold(body: Column(...))`      |
| Named parameters| `padding: EdgeInsets.all(16)`          |
| const           | `const Text('Hello')`                 |
| final           | `final String title = 'App';`          |
| List            | `children: [Text('A'), Text('B')]`    |
| Function/callback | `onPressed: () { Navigator.pop(context); }` |
| void            | `void main() { ... }`                 |

---

## 9. Order in the session

Do this **Introduction to Dart** first (this note), then:

1. **NAVIGATOR_NOTES.md** – push, pop, stack  
2. **SCAFFOLD_AND_WIDGETS_NOTES.md** – Scaffold, child, children  
3. **STUDENT_DEVELOPMENT_GUIDE.md** – screens, form, ListView  

See **STUDENT_DEVELOPMENT_GUIDE.md** for more and ask your instructor for the full lesson plan.
