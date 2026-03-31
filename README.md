---
marp: true
theme: "default"
paginate: true
backgroundColor: "#ffffff"
title: "SOP: The Nuclear Option (Selective Deletion)"
author: "@copilot"
date: 2026-03-31
tags: ["git", "tutorial", "workflow"]
---

# ☢️ Step 3: The Nuclear Option
**Goal:** Wipe the `main` branch clean while preserving `README.md` and `.git`.

---

## 💻 Option A: The Terminal (Using `git rm`)
The command `git rm -r` is used in your computer's terminal (like Git Bash, Terminal, or CMD).

### 1. Protect the `.git` folder
*   **Good news:** You don't need to do anything! The `.git` folder is "invisible" to standard git commands. `git rm` will **never** delete it.

### 2. Run the Selective Deletion
Instead of deleting everything and then "undoing" it, we tell Git to delete everything **except** your target files.
*   **Command:** 
    ```bash
    # This says: remove everything (-r .) 
    # BUT ignore (--cached) the README.md
    git rm -rf .
    git checkout HEAD -- README.md
    ```
*   **Alternative (The "Easy" Way):**
    1. Manually delete everything in the folder *except* `README.md`.
    2. Run `git add -A` (This tells Git: "I deleted these things, but kept the README").
    3. Run `git commit -m "Wiped site but kept README"`.

---

## 🌐 Option B: GitHub Web Interface (No Commands)
If you aren't comfortable with the terminal yet, you can do this directly on GitHub.com.

### 1. Delete Directories
*   Navigate to a folder (e.g., `_posts`).
*   Click the **three dots (...)** in the top right.
*   Select **Delete directory**.
*   **Why:** This is faster than deleting files one by one.

### 2. Delete Individual Files
*   Click on a file (e.g., `_config.yml`).
*   Click the **three dots (...)** or the **Trash Can icon**.
*   Select **Delete file**.

### 3. Keep what you want
*   Simply **do not click delete** on the `README.md` file. It will stay exactly where it is.

---

## 🛠️ Tools & Properties Summary

| Tool/Command | What it does | Why use it? |
| :--- | :--- | :--- |
| `git rm -r .` | Removes all tracked files recursively. | To clear the slate for a new Jekyll theme. |
| `.git` folder | The "Brain" of your repo. | **NEVER DELETE THIS.** If you do, it's no longer a GitHub repo. |
| `README.md` | Your project's front page. | Usually worth keeping so people know what the repo is. |

---

## ✅ Checklist for Step 3

- [ ] **Verify Branch:** Ensure the top-left dropdown says `main`.
- [ ] **Archive Check:** Ensure your messy version is safe on the `v1-archive` branch.
- [ ] **Delete Folders:** Remove `_posts`, `_layouts`, `assets`, etc.
- [ ] **Delete Files:** Remove `index.md`, `about.md`, etc.
- [ ] **Preserve:** Leave `README.md` and `.gitignore` untouched.
- [ ] **Commit:** Save the "Empty" state with a clear message.

---

## 💡 Pro-Tip: The "Hidden" .git
In your computer's file explorer, the `.git` folder is hidden by default. 
*   **On Windows:** View > Show > Hidden Items.
*   **On Mac:** `Cmd + Shift + .` (period).
**Rule:** As long as that folder exists, your "Sandbox" is still connected to GitHub!
