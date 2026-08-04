# Project Title

This repository contains the source code for our full-stack application. To ensure a smooth workflow across our five-person development team, we strictly separate the frontend web environment from our core API.

## Tech Stack Overview

| Layer        | Technology           | Build Tools / Runtime   |
| :----------- | :------------------- | :---------------------- |
| **Frontend** | React & Tailwind CSS | Vite, Node.js (via NVM) |
| **Backend**  | .NET 10.0            | Visual Studio 2026      |

---

## 1. Frontend Prerequisites (Node.js)

The React frontend relies on Node.js for local development and bundling. To prevent system-wide dependency conflicts, we require Node Version Manager (NVM) across all environments.

> **Note:** NVM keeps our local environments completely isolated. Never install frontend dependencies using elevated privileges.

### Linux Setup

Run the following in your terminal:

1. `curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.7/install.sh | bash`
2. `source ~/.bashrc`
3. `nvm install --lts`
4. `nvm use --lts`

### Windows Setup

Run the following in an elevated PowerShell:

1. `winget install CoreyButler.NVMforWindows`
2. Restart your PowerShell window.
3. `nvm install lts`
4. `nvm use lts`

---

## 2. Running the Frontend Locally

Once your OS-specific NVM is installed, you can initialize and boot the React application.

1. `cd frontend`
2. `npm install`
3. `npm run dev`

---

## 3. Running the Backend Locally

Our API services run on a completely separate runtime and do not require Node.js.

1. Open Visual Studio 2026.
2. Load the `.sln` file located in the `backend` directory.
3. Restore any missing NuGet packages.
4. Press F5 to compile and launch the development server.

---

## 4. Repository Rules

- **Dependency Management:** Ensure your local `.gitignore` is active before pushing to avoid committing `node_modules`.
- **Environment Variables:** Do not commit `.env` files; all secrets and connection strings must remain strictly local.
- **Logging Standard:** Everything must log itself. Under no circumstances should logs or comments be deleted from generated code.
