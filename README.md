# typescript-formatter-demo

A minimal TypeScript project demonstrating automatic code formatting using Prettier and GitHub Actions.

This repository shows how formatting can be enforced and auto-fixed in CI, even when developers commit poorly formatted code, without needing to run the formatter manually.



## 📁 Project Structure

```

typescript-formatter-demo/
│
├── .github/
│   └── workflows/
│       └── format.yml          # GitHub Actions workflow for auto-formatting
│
├── src/
│   └── index.ts                # Demo TypeScript file with intentionally dramatic formatting
│
├── package.json                # Project metadata and scripts
├── tsconfig.json               # TypeScript compiler configuration
├── .prettierrc                 # Prettier configuration (use tabs for indentation)
├── .prettierignore             # Files/folders ignored by Prettier
└── package-lock.json           # Locked dependency versions

````



## 🚀 What This Project Demonstrates

- TypeScript setup
- Prettier configuration enforcing tab-based formatting
- GitHub Actions workflow that auto-formats code and commits changes
- Dramatic formatting changes on objects, arrays, and function calls to clearly show CI behavior



## 🧰 Tech Stack

- TypeScript
- Prettier
- GitHub Actions



## 📦 Setup Instructions

### 1️⃣ Install Dependencies

After cloning the repo:

```bash
npm install
````

This will generate and/or use `package-lock.json`.



### 2️⃣ Run the Formatter Locally

```bash
npm run format
```

This runs Prettier with auto-fix on all files.

To check formatting without modifying files:

```bash
npm run format:check
```



## 📝 Prettier Configuration

File: `.prettierrc`

```json
{
  "useTabs": true
}
```

### What This Means

* Indentation uses tabs
* Any file with spaces, single-line objects, long function calls, or messy arrays will be reformatted
* This makes formatting changes visually dramatic when the workflow runs


## 🚫 Ignored Files

File: `.prettierignore`

```
node_modules
dist
```

These folders are excluded from formatting because:

* `node_modules` contains external dependencies
* `dist` contains compiled output

## ⚙️ Purpose of Each Config File

| File                           | Purpose                                                        |
| ------------------------------ | -------------------------------------------------------------- |
| `package.json`                 | Defines project metadata, scripts, and dev dependencies        |
| `tsconfig.json`                | Configures the TypeScript compiler                             |
| `.prettierrc`                  | Configures Prettier formatting rules                           |
| `.prettierignore`              | Lists files/folders Prettier should ignore                     |
| `.github/workflows/format.yml` | Defines the CI workflow to auto-format code and commit changes |
| `.vscode/settings.json`        | Installed for this demo to override behavior of my IDE setup.  |



## 🔁 GitHub Actions Workflow

File: `.github/workflows/format.yml`

The workflow runs on:

* Every push to `dev`
* Every pull request

It performs the following steps:

1. Checks out the repository
2. Installs Node.js
3. Installs dependencies with `npm ci`
4. Runs Prettier with auto-fix
5. Commits and pushes changes if formatting was updated

This ensures:

* The repository remains consistently formatted
* Developers do not need to manually format code
* Formatting becomes part of the CI process



## 🧪 How to Observe the Formatter Behavior

1. Create or edit `src/index.ts` with dramatic formatting:

   * Single-line objects
   * Single-line arrays
   * Multi-parameter functions

2. Push the branch

3. Watch GitHub Actions run

4. Observe an automatic commit that fixes indentation, splits long lines, and formats objects/arrays



## 🛠 TypeScript Build

To compile the project:

```bash
npm run build
```

Compiled files go to:

```
dist/
```


## 🎯 Why This Pattern Is Useful

* Eliminates formatting debates
* Ensures consistency across contributors
* Reduces noisy formatting commits
* Automates enforcement via CI
* Demonstrates dramatic visual changes in code formatting

## 📌 Notes

* The workflow requires write permissions to commit formatting changes.
* Auto-formatting only pushes changes for branches in the same repository (not forks).
* Prettier formatting is enforced consistently in CI regardless of local editor settings.


## 🔮 Next Steps (Future Expansion)

This simple demo can be extended to:

* Add ESLint
* Split into frontend/backend
* Convert into a monorepo
* Add test workflows
* Add branch protection rules


## 🧠 Key Concept

Formatting is treated as automation, not a developer responsibility.

The CI pipeline enforces consistency so humans can focus on logic.
