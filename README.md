# GitHub Workflow for Students

This guide walks you through the complete workflow for CS++ assignments: accepting an assignment, writing code, running tests, and submitting your work.

To learn more about the tools we use, head to the [Getting Started Repo](https://github.com/cs-plus-plus/Java-Getting-Started).

## 1. Creating a GitHub Account

1. Go to [GitHub](https://github.com/)
2. Click **Sign up** in the upper-right corner
3. Enter your email address, create a password, and choose a username
4. Follow the on-screen instructions to complete setup (you may need to verify your email)
5. Sign in to GitHub

## 2. Accepting an Assignment

1. Your instructor will post an assignment link in **Google Classroom**
2. Click the link to open it in your browser
3. If prompted, authorize GitHub Classroom to access your GitHub account
4. Click **Accept this assignment**
5. GitHub Classroom will create a personal repository for you with the assignment files
6. Click the link to your new repository to view it on GitHub

## 3. Opening Your Assignment (Recommended: GitHub Codespaces)

GitHub Codespaces gives you a full development environment in your browser — no installation required.

1. From your assignment repository on GitHub, click the green **"Code"** button
2. Select the **"Codespaces"** tab
3. Click **"Create codespace on main"**
4. Wait for the environment to load (this may take a few minutes the first time)
5. You now have a full VS Code editor in your browser with Java, Maven, and all extensions pre-installed

> **Note:** If the Java extension shows errors on first load, press `Cmd+Shift+P` (Mac) or `Ctrl+Shift+P` (Windows/Chromebook) and run **"Developer: Reload Window"**. This is a one-time setup step.

## 4. Writing Your Code

1. Open the main Java file (e.g., `src/main/java/.../ClassName.java`)
2. Look for methods marked with `// TODO: implement`
3. Read the **Javadoc comments** above each method — they describe what the method should do, provide examples, and give hints
4. Write your implementation below the TODO comment
5. You can test your code by running the `main` method, which includes an example call

### Tips for Writing Code
- **Read the Javadoc carefully** — it tells you the expected inputs, outputs, and edge cases
- **Start with the simplest methods** — build confidence before tackling harder ones
- **Use the `main` method** to test your code with `System.out.println` before running tests
- **Save your file** (`Cmd+S` or `Ctrl+S`) before running tests

## 5. Running Tests

Tests verify that your methods work correctly. Each test is worth a specific number of points.

### In Codespaces / VS Code
1. Click the **Testing** icon (flask/beaker) in the left sidebar
2. Click **Run All Tests** to run everything
3. Green checkmark = passing, red X = failing
4. Click on a failing test to see what went wrong

### From the Terminal
```bash
# Run all tests
mvn test

# Run a specific test
mvn -Dtest=TestClassName#testMethodName test
```

## 6. Saving Your Work (Committing and Pushing)

### In Codespaces / VS Code
1. Click the **Source Control** icon (branch icon) in the left sidebar
2. You'll see your changed files listed
3. Type a commit message (e.g., "Completed sumNumbers method")
4. Click the **Commit** button (checkmark)
5. Click **Sync Changes** to push your code to GitHub

### Using GitHub Desktop (if working locally)
1. Open GitHub Desktop — your changes will appear automatically
2. Write a short summary of what you changed in the **Summary** field
3. Click **Commit to main**
4. Click **Push origin** to send your changes to GitHub

## 7. Checking Your Score (Autograding)

When you push your code, GitHub automatically runs the tests and assigns points.

1. Go to your assignment repository on GitHub
2. Click the **Actions** tab at the top
3. Click on the most recent workflow run
4. Each test shows as a separate step with its point value
5. Green checkmarks = points earned, red X = points not earned
6. Your total score is the sum of all passing tests

> **Tip:** You can push as many times as you want! Each push triggers autograding, so keep improving your code until all tests pass.

## Alternative Setup: GitHub Desktop + Local IDE

If you prefer to work locally instead of using Codespaces:

1. Download and install [GitHub Desktop](https://desktop.github.com/)
2. Open GitHub Desktop and sign in with your GitHub account
3. Click **File** > **Clone Repository**
4. Select the **URL** tab and paste your assignment repository URL
5. Choose a local path and click **Clone**
6. Open the cloned folder in **VS Code** or **IntelliJ IDEA**

### Local Requirements
- Java 17 or newer ([Download](https://adoptium.net/))
- Maven 3.x ([Download](https://maven.apache.org/download.cgi))
- VS Code with Java extensions, or IntelliJ IDEA

## Troubleshooting

| Problem | Solution |
|---------|----------|
| Java errors on first Codespaces load | Press `Cmd+Shift+P` / `Ctrl+Shift+P` and run "Developer: Reload Window" |
| Tests won't run | Make sure your code compiles first — fix any red underlines |
| "File not found" errors | Check that your file is saved and in the correct directory |
| Can't push changes | Make sure you committed first, then click "Sync Changes" |
| GitHub Desktop doesn't show repo | Make sure you're signed into the correct GitHub account |
| Eclipse import issues | Use VS Code or Codespaces instead (recommended) |

## Need Help?

- Check the **Javadoc comments** in the source file for hints and examples
- Review the **test file** to understand expected inputs and outputs
- Ask a classmate or visit office hours
- Contact Mr. Hare at kevin@csplusplus.com
