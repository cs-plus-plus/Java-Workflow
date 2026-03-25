# CS++ Java — Assignment Workflow Guide

> Step-by-step instructions for completing and submitting Java assignments

This guide walks you through the complete workflow for every CS++ Java assignment — from accepting the GitHub Classroom link to checking your autograded score.

---

## Table of Contents

1. [Overview](#overview)
2. [Step 1: Accept the Assignment](#step-1-accept-the-assignment)
3. [Step 2: Open GitHub Codespaces](#step-2-open-github-codespaces)
4. [Step 3: Understand the Project Structure](#step-3-understand-the-project-structure)
5. [Step 4: Write Your Code](#step-4-write-your-code)
6. [Step 5: Run Tests Locally](#step-5-run-tests-locally)
7. [Step 6: Read Test Output](#step-6-read-test-output)
8. [Step 7: Commit and Push](#step-7-commit-and-push)
9. [Step 8: Check Your Autograded Score](#step-8-check-your-autograded-score)
10. [Practice Without Breaking Tests](#practice-without-breaking-tests)
11. [Common Code Patterns](#common-code-patterns)
12. [Troubleshooting](#troubleshooting)
13. [Tips for Success](#tips-for-success)
14. [FAQ](#faq)

---

## Overview

Every assignment follows the same workflow:

```
Accept link → Open Codespaces → Write code → Run tests → Commit & push → Check score
```

---

## Step 1: Accept the Assignment

1. Your teacher gives you a GitHub Classroom link
2. Click the link and sign in to GitHub
3. GitHub creates a personal copy of the assignment repository for you
4. You will see a page that says "Your assignment repository has been created"
5. Click the link to go to your new repository

---

## Step 2: Open GitHub Codespaces

1. On your repository page, click the green **Code** button
2. Select the **Codespaces** tab
3. Click **Create codespace on main**
4. Wait for the environment to load (this takes about 30 seconds the first time)
5. You now have a full VS Code editor in your browser with Java and Maven pre-installed

---

## Step 3: Understand the Project Structure

Every assignment follows this Maven project structure:

```
Assignment-Name/
├── pom.xml                          <-- Maven config (DO NOT MODIFY)
├── src/
│   ├── main/java/
│   │   └── package/
│   │       └── ClassName.java       <-- YOUR CODE GOES HERE
│   └── test/java/
│       └── package/
│           └── ClassNameTest.java   <-- Tests (DO NOT MODIFY)
└── .github/
    └── workflows/
        └── classroom.yml            <-- Autograding config (DO NOT MODIFY)
```

**You only edit the file in `src/main/java/`**. Everything else is pre-configured.

---

## Step 4: Write Your Code

1. In the Codespaces file explorer (left sidebar), navigate to `src/main/java/`
2. Open the Java file (e.g., `Unit1.java`)
3. You will see method stubs — empty methods with `// TODO` comments
4. Implement each method according to the assignment README
5. Save your file (`Ctrl+S` or `Cmd+S`)

**Example — a method stub before and after:**

Before (what you start with):
```java
public static int addIntegers(int a, int b) {
    // TODO: Return the sum of a and b
    return 0;
}
```

After (what you write):
```java
public static int addIntegers(int a, int b) {
    return a + b;
}
```

---

## Step 5: Run Tests Locally

Open the terminal in Codespaces (`Ctrl+`` ` or View → Terminal) and run:

```bash
mvn test
```

This compiles your code and runs all JUnit tests. You can run this as many times as you want — there is no limit.

---

## Step 6: Read Test Output

After running `mvn test`, you will see output like this:

**All tests pass:**
```
[INFO] Tests run: 5, Failures: 0, Errors: 0, Skipped: 0
[INFO] BUILD SUCCESS
```

**Some tests fail:**
```
[ERROR] testAddIntegers  Time elapsed: 0.003 s  <<< FAILURE!
AssertionError: expected:<5> but was:<0>
```

This tells you:
- The test `testAddIntegers` failed
- It expected the value `5`
- Your method returned `0`
- You need to fix your `addIntegers` method

**Code does not compile:**
```
[ERROR] COMPILATION ERROR
[ERROR] Unit1.java:[15,9] ';' expected
```

This tells you there is a syntax error on line 15 of Unit1.java. Fix the error and run `mvn test` again.

---

## Step 7: Commit and Push

Once you are happy with your code (or want to save your progress):

### Using the Source Control Panel (Recommended)

1. Click the **Source Control** icon in the left sidebar (branch icon) or press `Ctrl+Shift+G`
2. You will see your changed files listed under "Changes"
3. Click the **+** icon next to each file to stage it (or click **+** next to "Changes" to stage all)
4. Type a commit message in the text box (e.g., "completed unit 1 methods")
5. Click the **Commit** button
6. Click **Sync Changes** to push to GitHub

### Using the Terminal

```bash
git add -A
git commit -m "completed unit 1 methods"
git push
```

---

## Step 8: Check Your Autograded Score

1. Go to your repository on GitHub (not Codespaces)
2. Click the **Actions** tab at the top
3. Click the most recent workflow run
4. Look for the autograding step — your score appears there
5. The score is calculated from how many tests pass

---

## Practice Without Breaking Tests

Want to experiment with Java without affecting your assignment? Create a separate practice file:

1. Create `Practice.java` in the `src/main/java/` directory (same folder as the assignment file)
2. Add a `main` method:

```java
public class Practice {
    public static void main(String[] args) {
        // Your practice code here
        System.out.println("Hello from practice!");

        // Try out concepts
        int x = 10;
        int y = 3;
        System.out.println("Division: " + x / y);
        System.out.println("Remainder: " + x % y);
    }
}
```

3. Run it with:
```bash
javac src/main/java/*/Practice.java && java -cp src/main/java Practice
```

4. Delete `Practice.java` before your final push (it will not affect your tests, but keeps things clean)

---

## Common Code Patterns

### Return a calculated value
```java
public static int multiply(int a, int b) {
    return a * b;
}
```

### Use an if-else to return different values
```java
public static String getGrade(int score) {
    if (score >= 90) return "A";
    else if (score >= 80) return "B";
    else return "C";
}
```

### Loop through an array
```java
public static int sum(int[] arr) {
    int total = 0;
    for (int i = 0; i < arr.length; i++) {
        total += arr[i];
    }
    return total;
}
```

### Build a string in a loop
```java
public static String repeat(String s, int n) {
    String result = "";
    for (int i = 0; i < n; i++) {
        result += s;
    }
    return result;
}
```

### Use ArrayList methods
```java
public static void removeNegatives(ArrayList<Integer> list) {
    for (int i = list.size() - 1; i >= 0; i--) {
        if (list.get(i) < 0) {
            list.remove(i);
        }
    }
}
```

---

## Troubleshooting

| Problem | Cause | Solution |
|---------|-------|----------|
| "COMPILATION ERROR" | Syntax error in your code | Read the error message — it tells you the line number and what is wrong |
| "expected X but was Y" | Your method returned the wrong value | Check your logic. The test expected `X` but got `Y` |
| "NullPointerException" | You used a variable that is `null` | Make sure you initialized your variables before using them |
| "ArrayIndexOutOfBoundsException" | You accessed an invalid array index | Check your loop bounds — arrays are 0-indexed |
| Score did not update after push | You committed but did not push | Click "Sync Changes" in Source Control, or run `git push` |
| Codespace will not start | GitHub Codespaces quota reached | Delete old codespaces from github.com/codespaces |
| "package does not exist" | File is in the wrong directory | Make sure your file is in the correct `src/main/java/package/` folder |
| Tests pass locally but fail on GitHub | You modified the test file | Revert changes to test files — the autograder uses the originals |
| "cannot find symbol" | Typo in method name or wrong import | Check spelling matches the assignment exactly |
| Build takes too long | First run downloads dependencies | Wait for it to finish — subsequent runs are faster |
| Terminal says "mvn: command not found" | Terminal session reset | Close and reopen the terminal, or restart the Codespace |

---

## Tips for Success

1. Run `mvn test` after implementing each method — do not wait until the end
2. Read the error messages carefully — they tell you exactly what went wrong
3. Commit and push frequently so you never lose work
4. Do not modify test files, `pom.xml`, or anything in `.github/`
5. Method names, parameter types, and return types must match exactly
6. Start with the easiest methods first to build confidence
7. If you are stuck, re-read the assignment README — it has examples showing expected input and output
8. Use `System.out.println()` to debug — print variable values to see what your code is doing
9. Compare strings with `.equals()`, never with `==`
10. If your code does not compile, you score 0 on everything — fix compile errors first

---

## FAQ

**Q: Can I work on the assignment outside of Codespaces?**
Yes, if you have Java and Maven installed locally. But Codespaces is the easiest option since everything is pre-configured.

**Q: How many times can I push?**
Unlimited. Push as often as you want. Each push triggers the autograder, and your most recent score is what counts.

**Q: Can I see which tests passed and which failed?**
Yes. Run `mvn test` locally for detailed output, or check the Actions tab on GitHub for the autograder results.

**Q: What if I accidentally delete a file?**
If you have not pushed the deletion, you can restore it with `git checkout -- filename`. If you have pushed, ask your teacher to help reset the repository.

**Q: Do I need to write a `main` method?**
No. The JUnit tests call your methods directly. You do not need a `main` method unless you want one for your own testing.

**Q: My Codespace expired. Is my work lost?**
If you committed and pushed, your code is safe on GitHub. Create a new Codespace from your repository and your code will be there. If you did not push, the work in the expired Codespace may be lost.

**Q: Can I collaborate with other students?**
Each student has their own repository. You should write your own code. Ask your teacher about their collaboration policy.

**Q: The autograder shows a different score than `mvn test`. Why?**
Make sure you did not modify the test files. The autograder uses the original tests. If you changed them locally, your local results may differ.

**Q: How do I know which file to edit?**
The assignment README tells you. It is always in `src/main/java/` — look for the file with `// TODO` comments.

**Q: What does "BUILD FAILURE" mean?**
Either your code did not compile (check for syntax errors) or one or more tests failed (check the test output for details).

---

View all assignments and scoring breakdowns at [csplusplus.com/maven-tests](https://csplusplus.com/maven-tests)

*CS++ — AP Computer Science A — [csplusplus.com](https://csplusplus.com)*
