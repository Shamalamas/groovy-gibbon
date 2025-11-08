---

# 🐒 Groovy Gibbon — How to Fix Your Setup After the Rename

Hey team 👋

We recently renamed the frontend project folder from **`careercompass-ai`** → **`frontend-gibbon`**.
Some of you might still have the old version locally, which can cause errors when running `npm install` or `npm run dev`.

Follow this guide to fix your setup **safely and cleanly** without breaking anything.

---

### 🧱 Step 1: Rename or remove the old folder

If you still have the old folder on your computer, delete or rename it before pulling the latest code.

#### 📁 Using File Explorer (easiest)

1. Open your project folder (e.g. `C:\Users\<yourname>\Documents\GitHub\groovy-gibbon`).
2. Right-click the folder named **careercompass-ai** → choose **Delete** → confirm.

#### 💻 Using Command Prompt (for advanced users)

Open Command Prompt and run:

```bash
cd C:\Users\<yourname>\Documents\GitHub\groovy-gibbon
rmdir /s /q careercompass-ai
```

That permanently deletes the old folder.

---

### ⚙️ Step 2: Pull the latest project

Now pull the updated code from GitHub.
Open **VS Code** or **Command Prompt**, and run:

```bash
git pull
```

You should now see a new folder called **frontend-gibbon**.

If it’s your first time cloning, you can skip the old folder cleanup and just clone fresh:

```bash
git clone https://github.com/<your-org-or-user>/groovy-gibbon.git
cd groovy-gibbon/frontend-gibbon
```

---

### 🧩 Step 3: Open the project in VS Code

In your terminal:

```bash
cd frontend-gibbon
code .
```

Or just open the `frontend-gibbon` folder manually in VS Code.

---

### 🧾 Step 4: Check and update project files (we already did this — just verify)

Inside `frontend-gibbon`, make sure these files look right.
You don’t need to edit anything unless it’s missing.

#### ✅ 1️⃣ `package.json`

At the top, it should say:

```json
{
  "name": "frontend-gibbon",
  ...
}
```

#### ✅ 2️⃣ `README.md`

Should now mention **frontend-gibbon**, not **careercompass-ai**.

#### ✅ 3️⃣ `vite.config.ts`

This file should look like this (no paths or folder names referencing the old one):

```ts
import { defineConfig } from 'vite'
import react from '@vitejs/plugin-react-swc'

export default defineConfig({
  plugins: [react()],
})
```

---

### 🚀 Step 5: Clean and reinstall dependencies

Because the folder changed, we’ll clear out any old packages or build files before reinstalling.

#### 💻 Using Command Prompt / PowerShell:

```bash
cd C:\Users\<yourname>\Documents\GitHub\groovy-gibbon\frontend-gibbon
rmdir /s /q node_modules
rmdir /s /q dist
rmdir /s /q .vite
npm install
```

#### 🖱 Or using File Explorer:

1. Inside `frontend-gibbon`, delete the folders named **node_modules**, **dist**, and **.vite** (if you see them).
2. Then in VS Code’s terminal, run:

   ```bash
   npm install
   ```

This installs everything fresh.

---

### ⚡ Step 6: Start the development server

After it installs successfully, start the app:

```bash
npm run dev
```

Then open your browser and go to:
👉 **[http://localhost:5173](http://localhost:5173)**

If it loads the **Groovy Gibbon** site — everything’s fixed! 🎉

---

### ✅ Final Structure

Your folder should now look like this:

```
groovy-gibbon/
├── frontend-gibbon/
│   ├── public/
│   ├── src/
│   ├── package.json
│   ├── vite.config.ts
│   ├── tailwind.config.js
│   └── ...
└── README.md
```

Everything inside **frontend-gibbon** is now the correct, working version.

---

### 💬 Common Issues & Fixes

| Problem                            | Cause                                   | Fix                                                   |
| ---------------------------------- | --------------------------------------- | ----------------------------------------------------- |
| `npm install` fails                | Old cached `node_modules` or lock files | Delete `node_modules` and run `npm install` again     |
| `npm run dev` shows missing module | You’re still inside the old folder      | Make sure you’re in `frontend-gibbon/`                |
| Browser doesn’t load               | Old dev server still running            | Stop the old one (`Ctrl + C`) and rerun `npm run dev` |

---

### TL;DR

For the quick readers:

```bash
git pull
rmdir /s /q careercompass-ai
cd frontend-gibbon
rmdir /s /q node_modules dist .vite
npm install
npm run dev
```

---

Now everyone’s environment will be clean, synced, and running on **frontend-gibbon** — no more broken paths or missing configs.

---

