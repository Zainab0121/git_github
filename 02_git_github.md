# My Developer Journal

## Day 2 – Branching, Merging & Pulling

---

### What I Learned Today

Today I went beyond saving code locally and learned how to work on separate ideas safely using **branches**, combine work back together with **merging**, and stay in sync with GitHub using **pulling**.

---

### Part 1 – What is a Branch?

A branch is a separate copy of my project history where I can make changes freely without touching `main`. Think of main as the published book and a branch as a draft notebook.

```bash
git branch              # list all branches (* = current)
git switch -c my-branch # create AND switch in one command
git switch main         # switch back to main
```

**Visual:**
```
main:    A --- B --- C
                      \
feature:               D --- E
```

Commits D and E only exist on the feature branch. Main is untouched.

---

### Part 2 – Working on a Branch

Once on a branch, everything works the same — edit, `git add`, `git commit`. Those commits only live on the branch until you merge them.

```bash
git switch -c day2-notes          # create & switch
echo "Day 2 notes" >> README.md   # make a change
git add README.md
git commit -m "Add Day 2 entry"   # commit on THIS branch only

git switch main
cat README.md   # Day 2 line is GONE — only lives on day2-notes
```

---

### Part 3 – Merging

Merging brings commits from a feature branch into another branch (usually main). The rule: **switch to the destination branch first, then merge.**

```bash
git switch main                # go to where you want to merge INTO
git merge day2-notes           # bring in the commits
git log --oneline              # confirm both sets of commits are here
```

---

### Part 4 – Deleting a Branch

Once merged, the branch label can be safely deleted. The commits are now part of main's history.

```bash
git branch -d day2-notes    # safe delete (only works if merged)
git branch -D branch-name   # force delete (even if not merged)
git branch                  # confirm it's gone
```

---

### Part 5 – Merge Conflicts

A conflict happens when two branches changed the **same line** of the **same file**. Git marks the file like this:

```
<<<<<<< HEAD
This is the version from main
=======
This is the version from my-feature
>>>>>>> my-feature
```

**How to fix:**
1. Open the file and edit it — keep what you want, delete the markers
2. `git add conflicted-file.txt`
3. `git commit -m "Resolve merge conflict"`

Conflicts are normal. Every developer deals with them.

---

### Part 6 – Pulling from GitHub

`git pull` downloads new commits from GitHub and merges them into your local branch. Use it when:
- You edited a file directly on the GitHub website
- A teammate pushed new work you need

```bash
git pull              # fetch + merge from GitHub
git pull origin main  # explicit version
```

---

### Part 7 – The Full Professional Workflow

This is how real developers work for every feature:

```bash
git switch main                      # 1. Start from main
git pull                             # 2. Get latest from GitHub
git switch -c feature/my-feature     # 3. Create a feature branch
# ... edit files ...                 # 4. Do your work
git add . && git commit -m "..."     # 5. Stage and commit
git switch main                      # 6. Go back to main
git merge feature/my-feature         # 7. Merge in your work
git push                             # 8. Push to GitHub
git branch -d feature/my-feature     # 9. Clean up the branch
```

Always pull before branching — ensures you start from the latest code.

---

### My Day 2 Cheat Sheet

| Command | What It Does |
|---|---|
| `git branch` | List all branches |
| `git switch -c name` | Create and switch to new branch |
| `git switch name` | Switch to existing branch |
| `git merge branch-name` | Merge branch into current |
| `git branch -d name` | Delete a merged branch |
| `git pull` | Download + merge changes from GitHub |

---

### What's Next (Day 3)

- Cloning — download any repo from GitHub
- Forking — copy someone else's project
- Pull Requests — the professional way to propose changes
- `.gitignore` — tell Git which files to never track

---

*Day 2 complete. I now know the full branching workflow: branch → work → merge → push.*
