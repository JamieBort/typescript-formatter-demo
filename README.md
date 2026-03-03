# typescript-formatter-demo

A minimal TypeScript project demonstrating an automated workflow using GitHub Actions.

This repository shows how a repeatable process can be enforced and executed in CI, even when developers do not manually run it before committing code.

For the purposes of this demonstration, we're using formatting as the repeatable process. Other options include

- linting
- automated testing
- build verification
- security scanning
- and more




## 📁 Project Structure

```
typescript-formatter-demo/
│
├── .github/
│   └── workflows/
│       └── format.yml          # GitHub Actions workflow definition
├── .vscode/
│   └── settings.json           # Used for this demo to disable format-on-save
├── src/
│   └── index.ts                # Demo TypeScript file
│
├── package.json                # Project metadata and scripts
├── tsconfig.json               # TypeScript compiler configuration
├── .prettierrc                 # Prettier configuration
├── .prettierignore             # Files and directories excluded from the formatting process
└── package-lock.json           # Locked dependency versions
```



## 🚀 What This Project Demonstrates

- Setting up a GitHub Actions workflow that runs on push
- Defining a repeatable automated process
- Validating the process locally before relying on CI
- Executing the process automatically in CI
- Automatically committing updates if changes are required



## 🧰 Tech Stack

- TypeScript
- Prettier
- GitHub Actions



## 📦 Setup Instructions

The recommended order of operations:

1. Install dependencies
2. Verify the process works locally
3. Commit and push
4. Confirm the workflow runs remotely



### 1️⃣ Install Dependencies

After cloning the repository:

```bash
npm install
```

This installs all required development dependencies and generates the `package-lock.json` file.



### 2️⃣ Verify the Process Works Locally (Important)

Clean install dependencies:

```bash
npm ci
```


Before relying on GitHub Actions, confirm that the defined process executes correctly on your local machine.


To that end, rather than `npm install`, use `npm ci` instead. It is the command that GitHub Actions uses _every_ time the workflow is executed.


#### Check the process without modifying files

For this tutorial specifically, run the following:

```bash
npm run format:check
```

This validates whether changes would be required.



#### Execute the process locally

For this tutorial specifically, run the following:

```bash
npm run format:write
```

This runs the configured automation according to the project settings.

You should confirm this works locally before testing the workflow remotely.



### 3️⃣ Create and Commit the Workflow File

Ensure the workflow .yml file exists at:

```
.github/workflows/<workflow_file>.yml
```

If creating it for the first time:

```bash
git add .
git commit -m "Add workflow definition"
git push origin main
```

The workflow in this project is configured to run on:

- Pushes to the `main` branch
- Pull requests



### 4️⃣ Verify the Workflow Runs Remotely

After pushing to the `main` branch:

1. Open your repository on GitHub
2. Navigate to the **Actions** tab
3. Confirm the workflow executes
4. If changes were required, confirm that an automated commit is created



## 📝 Tool Configuration

File: `.prettierrc`

```json
{
	"useTabs": true
}
```

This defines how the automated process behaves when it runs.



## 🚫 Ignored Files

File: `.prettierignore`

```
node_modules
dist
```

These folders are excluded from the automated process because they contain dependencies or generated output.



## 🔁 GitHub Actions Workflow

File: `.github/workflows/format.yml`

The workflow:

1. Checks out the repository
2. Installs Node.js
3. Installs dependencies with `npm ci`
4. Runs the configured process
5. Commits changes if updates were made

This ensures:

- The repository remains consistent
- The process is enforced automatically
- Manual execution is optional but validated



## 🎯 Why This Pattern Is Useful

- Encourages automation over manual enforcement
- Ensures consistent behavior across contributors
- Reduces process drift
- Moves repeatable tasks into CI



## 📌 Notes

- The workflow requires write permissions to commit changes.
- Automated commits only occur for branches within the same repository (not forks).
- The CI process runs independently of local editor settings.



## 🧠 Key Concept

Treat repeatable processes as automation.

Validate locally.
Enforce remotely.
Keep the repository consistent.

