# Frontend Setup Guide

Step-by-step instructions for cloning the repo and getting the **frontend** running.

---

## 1. Prerequisites

You need two things installed before cloning:

- **Git** — to clone the repo
- **Node.js** (LTS version, e.g. 20.x) — includes `npm`

---

## 2. Windows Setup

### 2.1 Install Git

1. Download from [git-scm.com/download/win](https://git-scm.com/download/win)
2. Run the installer — default options are fine
3. Verify install by opening **PowerShell** or **Command Prompt**:

```powershell
git --version
```

### 2.2 Install Node.js

1. Download the **LTS** version from [nodejs.org](https://nodejs.org)
2. Run the installer — default options are fine (this also installs `npm`)
3. Verify install:

```powershell
node --version
npm --version
```

### 2.3 Clone the repo

1. Open PowerShell or Command Prompt
2. Navigate to where you want the project:

```powershell
cd C:\Users\<your-username>\Projects
```

3. Clone it:

```powershell
git clone <repo-url>
cd <repo-folder>
```

### 2.4 Set up the frontend

1. Move into the frontend folder:

```powershell
cd frontend
```

2. Install dependencies:

```powershell
npm install
```

3. Copy the environment file (if one exists):

```powershell
copy .env.example .env
```

4. Start the dev server:

```powershell
npm run dev
```

5. Open the URL shown in the terminal (usually `http://localhost:5173`) in your browser.

**Recommended:** Open the whole repo folder in VS Code (`code .` from the repo root). If a popup appears asking to install recommended extensions, accept it — this installs the correct tooling automatically (ESLint, Prettier, Tailwind IntelliSense, etc).

---

## 3. Linux Setup

### 3.1 Install Git

Most distros ship with Git, but if not:

```bash
# Arch
sudo pacman -S git

# Debian/Ubuntu
sudo apt install git

# Fedora
sudo dnf install git
```

Verify:

```bash
git --version
```

### 3.2 Install Node.js

Recommended: use **nvm** (Node Version Manager) instead of your distro's package manager, so you can match the project's Node version exactly (check for a `.nvmrc` file in `frontend/`).

```bash
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.1/install.sh | bash
```

Restart your terminal, then:

```bash
nvm install --lts
nvm use --lts
```

Verify:

```bash
node --version
npm --version
```

### 3.3 Clone the repo

```bash
cd ~/Projects   # or wherever you keep code
git clone <repo-url>
cd <repo-folder>
```

### 3.4 Set up the frontend

```bash
cd frontend
npm install
cp .env.example .env   # if this file exists
npm run dev
```

Open the URL shown in the terminal (usually `http://localhost:5173`) in your browser.

**Recommended:** Open the whole repo folder in VS Code (`code .` from the repo root). If a popup appears asking to install recommended extensions, accept it.

---

## 4. Common Issues

| Problem                                            | Fix                                                                                              |
| -------------------------------------------------- | ------------------------------------------------------------------------------------------------ |
| `npm install` fails with permission errors (Linux) | Don't use `sudo npm install`. Use nvm (above) so npm doesn't need root.                          |
| Wrong Node version                                 | Run `nvm use` in `frontend/` if a `.nvmrc` exists.                                               |
| Port 5173 already in use                           | Stop whatever's using it, or Vite will auto-pick the next free port — check the terminal output. |
| `.env` missing and app errors on start             | Copy `.env.example` to `.env` as shown above, then fill in required values.                      |

---

## 5. Recommended Extensions

If you open the repo root in VS Code, a popup will offer to install these automatically (via `.vscode/extensions.json`). Here's what each one does and why it's grouped the way it is.

### Core essentials

Without these, things will actively break or misbehave — mismatched formatting, no linting, no Tailwind autocomplete.

| Extension                                                                                                  | Why it's core                                                                                               |
| ---------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------- |
| [ESLint](https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint)                       | Runs the repo's ESLint config live in the editor — catches bugs and style issues before you even save.      |
| [Prettier](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode)                     | Auto-formats on save so everyone's code matches — no arguing about semicolons in PRs.                       |
| [Tailwind CSS IntelliSense](https://marketplace.visualstudio.com/items?itemName=bradlc.vscode-tailwindcss) | Autocomplete, hover previews, and lint warnings for Tailwind classes — hard to work efficiently without it. |

### Optional quality-of-life

Nice to have, nobody's blocked without them. Pick what fits your workflow.

| Extension                                                                                                                     | What it does                                                                                                                                                       |
| ----------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| [ES7+ React/Redux/React-Native snippets](https://marketplace.visualstudio.com/items?itemName=dsznajder.es7-react-js-snippets) | Shorthand snippets for React boilerplate (`rafce`, etc).                                                                                                           |
| [Auto Rename Tag](https://marketplace.visualstudio.com/items?itemName=formulahendry.auto-rename-tag)                          | Renaming an opening JSX/HTML tag auto-renames its matching closing tag.                                                                                            |
| [GitLens](https://marketplace.visualstudio.com/items?itemName=eamodio.gitlens)                                                | Inline git blame, commit history, and diffs without leaving the file.                                                                                              |
| [Headwind](https://marketplace.visualstudio.com/items?itemName=heybourn.headwind)                                             | Auto-sorts Tailwind classes into a consistent order. _(Skip if the repo's Prettier config already uses `prettier-plugin-tailwindcss` — same job, don't run both.)_ |
| [Tailwind Fold](https://marketplace.visualstudio.com/items?itemName=stivo.tailwind-fold)                                      | Folds long `className` strings so JSX stays readable.                                                                                                              |
| [Import Cost](https://marketplace.visualstudio.com/items?itemName=wix.vscode-import-cost)                                     | Shows the bundle size of each import inline — useful for catching bloated dependencies early.                                                                      |
| [npm Intellisense](https://marketplace.visualstudio.com/items?itemName=christian-kohler.npm-intellisense)                     | Autocompletes npm module names when importing.                                                                                                                     |
| [indent-rainbow](https://marketplace.visualstudio.com/items?itemName=oderwat.indent-rainbow)                                  | Colors indentation levels so deeply nested JSX is easier to scan.                                                                                                  |
| [Error Lens](https://marketplace.visualstudio.com/items?itemName=usernamehw.errorlens)                                        | Shows lint/type errors inline on the line itself instead of only in the Problems panel.                                                                            |
| [DotENV](https://marketplace.visualstudio.com/items?itemName=mikestead.dotenv)                                                | Syntax highlighting for `.env` files.                                                                                                                              |
| [Thunder Client](https://marketplace.visualstudio.com/items?itemName=rangav.vscode-thunder-client)                            | Lightweight REST client for testing API calls — most useful once `backend/` has endpoints to hit.                                                                  |

---

## Notes on Tooling

Using `@vitejs/plugin-react-swc` (SWC) for HMR.

React Compiler is not enabled by default — see the [installation docs](https://react.dev/learn/react-compiler/installation) if you want it.

### Expanding the ESLint configuration

If you are developing a production application, we recommend updating the configuration to enable type-aware lint rules:

```js
export default defineConfig([
    globalIgnores(["dist"]),
    {
        files: ["**/*.{ts,tsx}"],
        extends: [
            // Other configs...

            // Remove tseslint.configs.recommended and replace with this
            tseslint.configs.recommendedTypeChecked,
            // Alternatively, use this for stricter rules
            tseslint.configs.strictTypeChecked,
            // Optionally, add this for stylistic rules
            tseslint.configs.stylisticTypeChecked,

            // Other configs...
        ],
        languageOptions: {
            parserOptions: {
                project: ["./tsconfig.node.json", "./tsconfig.app.json"],
                tsconfigRootDir: import.meta.dirname,
            },
            // other options...
        },
    },
]);
```

You can also install [eslint-plugin-react-x](https://github.com/Rel1cx/eslint-react/tree/main/packages/plugins/eslint-plugin-react-x) and [eslint-plugin-react-dom](https://github.com/Rel1cx/eslint-react/tree/main/packages/plugins/eslint-plugin-react-dom) for React-specific lint rules:

```js
// eslint.config.js
import reactX from "eslint-plugin-react-x";
import reactDom from "eslint-plugin-react-dom";

export default defineConfig([
    globalIgnores(["dist"]),
    {
        files: ["**/*.{ts,tsx}"],
        extends: [
            // Other configs...
            // Enable lint rules for React
            reactX.configs["recommended-typescript"],
            // Enable lint rules for React DOM
            reactDom.configs.recommended,
        ],
        languageOptions: {
            parserOptions: {
                project: ["./tsconfig.node.json", "./tsconfig.app.json"],
                tsconfigRootDir: import.meta.dirname,
            },
            // other options...
        },
    },
]);
```
