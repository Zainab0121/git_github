# My Git & GitHub Learning Journal

This repo documents my journey learning Git and GitHub from scratch over 3 days.
It is both a reference I can come back to and a live example of the workflow in action —
every commit, branch, and merge here was made as part of the course.

---

## Repo Structure

```
my-dev-journal/
├── 01_git_github.md      # Day 1 — Solo workflow
├── 02_git_github.md      # Day 2 — Branching & merging
├── 03_git_github.md      # Day 3 — Collaboration
├── .gitignore            # Ignores secrets, logs, OS files
└── README.md             # This file
```

---

## What I Learned

### Day 1 — Solo Workflow `01_git_github.md`
Setting up Git, creating a repository, staging and committing files,
and pushing to GitHub for the first time.
```
git init → git add → git commit → git push
```

### Day 2 — Branching & Merging `02_git_github.md`
Working on separate ideas without touching `main`, merging branches back together,
resolving conflicts, and pulling changes from GitHub.
```
git switch -c → commit → git merge → git pull
```

### Day 3 — Collaboration `03_git_github.md`
Cloning and forking repositories, opening Pull Requests, syncing with upstream,
and protecting sensitive files with `.gitignore`.
```
git clone → fork → pull request → .gitignore
```

---

## Branches

| Branch | Purpose |
|---|---|
| `main` | Stable — all completed work lives here |
| `branching` | Practice branch created during Day 2 to demonstrate the feature branch workflow |

---

## The Core Workflow

The daily loop I now use for every change, no matter how small:

```bash
git switch main && git pull           # start from the latest
git switch -c feature/name            # one branch per feature
git add . && git commit -m "msg"      # commit often, keep messages clear
git push -u origin feature/name       # push the branch to GitHub
# open Pull Request → review → merge → delete branch
git switch main && git pull           # sync back and repeat
```

---

## Rules Worth Remembering

- **Never commit directly to `main`** — always branch, even for small changes
- **Pull before branching** — start every feature from the latest code
- **Commit small and often** — easier to understand, easier to reverse
- **`.gitignore` before your first commit** — much harder to undo than to prevent
- **Merge conflicts are normal** — Git is just asking you to make a decision

---

*Built from scratch, one commit at a time.*
