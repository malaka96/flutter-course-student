# Simple CI/CD Flow – For Teaching (Mobile App Development)

This document explains the CI/CD pipeline in a way you can use directly with students. Use it as a lecture guide or share it with them as a handout.

---

## 1. The Five-Step Flow (Explain It Like This)

### 1️⃣ Developer Writes Code

A developer writes code on their machine.

**Examples:**

- Add a new feature  
- Fix a bug  
- Improve the UI  

Then they **commit** the code.

---

### 2️⃣ Code Is Pushed to the Repository

The developer runs:

```bash
git push
```

The code goes to a **remote repository** (e.g. GitHub).

---

### 3️⃣ CI Pipeline Starts Automatically

When code is pushed:

1. **GitHub** detects the change  
2. The **GitHub Actions** workflow starts  

This happens because of the file:

```
.github/workflows/flutter-ci.yml
```

No one has to click “Run” — it starts automatically.

---

### 4️⃣ Automated Steps Run

The pipeline runs steps like:

- Install dependencies  
- Run static analysis  
- Run tests  
- Build the app  

For our Flutter project that means:

- `flutter pub get`  
- `flutter analyze`  
- `flutter test`  
- `flutter build`  

**No human intervention required.**

---

### 5️⃣ Results Are Reported

The system shows:

- ✅ **Build passed**  
- ❌ **Build failed**  

If something breaks, developers see it immediately (e.g. in the GitHub **Actions** tab or on the pull request).

---

## 2. CI vs CD (Explain This Clearly)

Students often confuse these. Keep the distinction simple:

### CI — Continuous Integration

- **Means:** Automatically **build** and **test** code whenever developers push changes.  
- **Purpose:**  
  - Detect bugs early  
  - Make sure the code always builds  

### CD — Continuous Delivery / Deployment

- **Means:** Automatically **deliver** or **deploy** the application.  
- **Examples:**  
  - Build APK / IPA  
  - Upload to a testing environment  
  - Release to the store  

For mobile apps, CD might use tools like **Fastlane**, **Expo EAS**, or store deployment pipelines.

**In this course we focus on CI** (build + test). CD is the next step in real-world teams.

---

## 3. One-Sentence Explanation (Students Remember This)

You can tell students:

> **“CI/CD is like a robot developer that checks our code every time we push changes.”**

That analogy usually makes the idea click.

---

## 4. Example Flow in This Course

Use this in your lecture:

1. **Student writes code** (e.g. a small change in the app or a test).  
2. **Commit** the change.  
3. **Push** to GitHub.  
4. **GitHub Actions** runs our CI workflow.  
5. **Tests** run.  
6. **Build** is verified.  
7. **Result** is shown in the **Actions** tab.

---

## 5. Live Demo (Students Love This)

During the lecture:

1. Make a **small commit** (e.g. `docs: update README` or change one line in the app).  
2. **Push** it.  
3. Open the **Actions** tab on GitHub.  
4. Show the pipeline running **live**.  

That moment usually makes CI/CD click instantly.

---

## 6. Optional: What Big Companies Do (If Students Ask)

Explain that in industry, pipelines often include:

- **Build**  
- **Test**  
- **Security scan**  
- **Code quality checks**  
- **Deployment**  
- **Monitoring**  

So CI/CD becomes the **backbone** of modern software engineering. Our course pipeline is a simplified version of the same idea.

---

## Quick Reference

| Term        | Meaning in one line                                      |
|------------|-----------------------------------------------------------|
| **CI**     | Automatically build and test when code is pushed.         |
| **CD**     | Automatically deliver or deploy the app.                 |
| **Workflow** | The set of steps defined in `.github/workflows/`.     |
| **Actions tab** | Where you see runs and results on GitHub.           |

For more detail on what runs in *this* repo, see **CI_EXPLANATION.md**.
