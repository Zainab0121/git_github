# My Developer Journal

## Day 3 – Collaborating with Others

---

### What I Learned Today

Today was about working *with other people* — the real reason GitHub exists. I learned how to download existing projects, contribute to repos I don't own, propose changes professionally, and protect sensitive files.

---

### Part 1 – Cloning a Repository

Cloning downloads a complete copy of a GitHub repository — every file, every commit, every branch.

```bash
git clone https://github.com/username/repo-name.git
cd repo-name
git remote -v    # origin is already set up automatically
```

**Key point:** After cloning, you don't need `git remote add` — Git sets up `origin` for you.

---

### Part 2 – Forking a Repository

A fork is my own copy of someone else's repo, stored under *my* GitHub account.

| | Clone | Fork |
|---|---|---|
| Where | Local machine | My GitHub account |
| Can I push? | Only with permission | Yes — it's my copy |
| Used for | My own / team repos | Contributing to others' repos |

**Workflow:** Fork on GitHub → Clone my fork → Make changes → Open Pull Request

```bash
# After forking on GitHub, clone your fork:
git clone https://github.com/MY-USERNAME/repo-name.git
cd repo-name

# Add the original repo as "upstream" to stay in sync:
git remote add upstream https://github.com/ORIGINAL-OWNER/repo-name.git
git fetch upstream
git merge upstream/main

# "Remember the original repo's address → go check if it has anything new → bring those new things into my code."
```

---

### Part 3 – Pull Requests

A Pull Request (PR) is a formal proposal: *"I made changes — please review and merge them."*

**The PR workflow:**
1. Create a feature branch
2. Make and commit changes
3. Push the branch to GitHub
4. Open a Pull Request on GitHub
5. Review, discuss, adjust
6. Merge the PR

```bash
git switch -c feature/my-change
# ... make changes ...
git add . && git commit -m "Describe the change"
git push origin feature/my-change
# Then go to GitHub and click "Compare & pull request"
```

**After the PR is merged:**
```bash
git switch main
git pull                           # get the merged changes
git branch -d feature/my-change    # clean up
```

---

### Part 4 – .gitignore

`.gitignore` tells Git which files to completely ignore — they won't appear in `git status`, won't be staged, and won't be committed.

**Common things to ignore:**
```
# Secrets & credentials
secrets.txt
*.env

# OS files
.DS_Store
Thumbs.db

# Dependencies (installed packages)
node_modules/
__pycache__/

# Build output
dist/
*.log
logs/
```

```bash
touch .gitignore          # create the file
# add patterns inside it
git add .gitignore
git commit -m "Add .gitignore"
```

**Important:** The `.gitignore` file itself should be committed so everyone on the team shares the same rules.

---

### Part 5 – Exploring a New Repository

When I clone someone else's repo, these commands help me orient quickly:

```bash
ls -la                        # see all files including hidden
cat README.md                 # read the project description
git log --oneline | head -20  # see recent history
git branch -a                 # see all branches
git show abc1234              # inspect a specific commit
git blame filename.txt        # see who changed each line
```

---

### The Full Collaboration Workflow

```bash
# New team member:
git clone [repo URL]

# Daily loop:
git switch main && git pull         # start fresh
git switch -c feature/my-feature    # branch per feature
# ... do work, commit often ...
git push origin feature/my-feature  # push to GitHub
# Open Pull Request → get reviewed → merge

# After merge:
git switch main && git pull         # sync locally
git branch -d feature/my-feature    # clean up
```

---

### My Day 3 Cheat Sheet

| Command | What It Does |
|---|---|
| `git clone URL` | Download a full repo |
| `git remote add upstream URL` | Add original repo as upstream |
| `git fetch upstream` | Download upstream changes |
| `git merge upstream/main` | Apply upstream changes |
| `git push origin branch-name` | Push branch to GitHub |
| `git blame filename` | See who changed each line |
| `git show commit-hash` | Inspect a specific commit |

---

### The 3-Day Journey Complete

| Day | Topics |
|---|---|
| Day 1 | `init` · `add` · `commit` · `push` |
| Day 2 | `branch` · `merge` · `pull` |
| Day 3 | `clone` · `fork` · pull requests · `.gitignore` |

---

*From zero to open-source contributor in three days.* 🎉
