# My Developer Journal

## Day 1 – Learning Git & GitHub from Scratch

---

### What I Learned Today

Today I started learning **Git** and **GitHub** — two of the most important tools every developer uses.

---

### What is Git?

Git is a **version control system**. It tracks every change I make to my code over time.
Instead of saving files like `essay_final_v2_ACTUALLY_final.docx`, Git keeps a clean history of every change automatically.

**GitHub** is the website where I store my Git projects online — like Google Drive, but for code.

> Key insight: Git is the tool. GitHub is the website.

---

### Part 1 – Setting Up Git

After installing Git, I told it who I am (only done once per computer):

```bash
git config --global user.name "Your Name"
git config --global user.email "you@example.com"
git config --list
```

---

### Part 2 – Creating a Repository

A **repository** is a folder that Git is watching.

```bash
mkdir my-project     # Create a new folder
cd my-project        # Move into the folder
git init             # Tell Git to start tracking this folder
ls -a                # Confirm the hidden .git folder was created
```

The hidden `.git` folder is where Git stores all history. I never need to touch it directly.

---

### Part 3 – Tracking Files

Git does not automatically track every file. I have to tell it which files to include using `git add`.

**Two important states:**
- **Untracked** – Git sees the file but isn't watching it
- **Staged** – The file is ready to be saved in the next commit

```bash
echo "Hello, Git!" > hello.txt   # Create a file
git status                        # See what Git notices
git add hello.txt                 # Stage the file
git status                        # Now it shows green (staged)
git add .                         # Add ALL files at once
```

---

### Part 4 – Saving Changes (Commits)

A **commit** is a permanent snapshot of my staged files. Every commit needs a message.

```bash
git commit -m "Add hello.txt file"
```

**Tips for good commit messages:**
- Use present tense: `"Add login page"` not `"Added login page"`
- Be specific: `"Fix broken link in navbar"` not `"Fix stuff"`
- Keep it under 72 characters

---

### Part 5 – Viewing History

Every commit is stored permanently. I can view the full history with:

```bash
git log             # Full history with author, date, and message
git log --oneline   # Compact view — one line per commit
```

---

### Part 6 – Pushing to GitHub

To store my project online, I:

1. Created a new repository on github.com (left it empty — no README)
2. Connected my local repo to GitHub:

```bash
git remote add origin https://github.com/your-username/my-project.git
git branch -M main
git push -u origin main
```

After the first push, future pushes are just:

```bash
git push
```

---

### My Git Cheat Sheet

| Command | What It Does |
|---|---|
| `git init` | Start tracking a folder |
| `git status` | See what has changed |
| `git add filename` | Stage a specific file |
| `git add .` | Stage all changed files |
| `git commit -m "msg"` | Save a snapshot with a message |
| `git log --oneline` | View compact commit history |
| `git remote add origin URL` | Connect to GitHub |
| `git branch -M main` | Rename branch to main |
| `git push -u origin main` | Push to GitHub (first time) |
| `git push` | Push to GitHub (after setup) |

---

### What's Next?

- Branching – work on features without touching main code
- Merging – combine branches back together
- Pulling – download changes from GitHub
- Cloning – copy someone else's repository
- Pull Requests – propose and review changes on GitHub

---

*Day 1 complete. I now know the core Git workflow: init → add → commit → push.*
