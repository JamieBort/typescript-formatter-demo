# typescript-formatter-demo

A minimal TypeScript project demonstrating automatic code formatting using Prettier and GitHub Actions.

This repository shows how formatting can be enforced and auto-fixed in CI without requiring developers to manually run the formatter.

## 📁 Project Structure

```
typescript-formatter-demo/
│
├── .github/
│ └── workflows/
│ └── format.yml
│
├── src/
│ └── index.ts
│
├── package.json
├── tsconfig.json
├── .prettierrc
├── .prettierignore
└── package-lock.json
```

## 🚀 What This Project Demonstrates

- TypeScript setup
- Prettier configuration
- GitHub Actions workflow
- Automatic formatting on push and pull request
- Auto-commit of formatting changes

## 🧰 Tech Stack

- TypeScript
- Prettier
- GitHub Actions

## 📦 Setup Instructions

### 1️⃣ Install Dependencies

After cloning the repo:

```bash
npm install
```

This will generate and/or use `package-lock.json`.

### 2️⃣ Run the Formatter Locally

```bash
npm run format
```

This runs:

```
prettier --write .
```

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

- Indentation must use tabs
- Any file using spaces for indentation will be rewritten
- Prettier applies this rule consistently across the project

## 🚫 Ignored Files

File: `.prettierignore`

```
node_modules
dist
```

These folders are excluded from formatting because:

- `node_modules` contains external dependencies
- `dist` contains compiled output

## 🔁 GitHub Actions Workflow

File: `.github/workflows/format.yml`

The workflow runs on:

- Every push to `main`
- Every pull request

It performs the following steps:

1. Checks out the repository
2. Installs Node.js
3. Installs dependencies with `npm ci`
4. Runs Prettier with auto-fix
5. Commits and pushes changes if formatting was updated

This ensures:

- The repository remains consistently formatted
- Developers do not need to remember to run the formatter manually
- Formatting becomes part of the CI process

## 🧪 How to Observe the Formatter Behavior

1. Modify `src/index.ts`
2. Intentionally use spaces instead of tabs
3. Push the branch
4. Watch GitHub Actions run
5. Observe an automatic commit that fixes indentation

## 🛠 TypeScript Build

To compile the project:

```bash
npm run build
```

This uses the configuration in `tsconfig.json` and outputs compiled files to:

```
dist/
```

## 🎯 Why This Pattern Is Useful

- Eliminates formatting debates
- Ensures consistency across contributors
- Reduces noisy formatting commits
- Automates enforcement via CI
- Scales cleanly to larger projects

## 📌 Notes

- The workflow requires write permissions to commit formatting changes.
- Auto-formatting will only push changes for branches within the same repository (not forks).
- The formatter runs in a fresh CI environment each time, ensuring reproducibility.

## 🔮 Next Steps (Future Expansion)

This simple demo can be extended to:

- Add ESLint
- Split into frontend/backend
- Convert into a monorepo
- Add test workflows
- Add branch protection rules

## 🧠 Key Concept

Formatting is treated as automation, not a developer responsibility.

The CI pipeline enforces consistency so humans can focus on logic.
