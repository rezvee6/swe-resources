# 🧠 Advanced Git Commands – Must-Know for Power Users

## 🔄 1. Interactive Rebase (Clean Up History)

```bash
git rebase -i HEAD~5
```

Lets you **edit, squash, or reorder** the last 5 commits.

Common options:

- `pick`: keep the commit
- `squash`: combine with previous commit
- `reword`: change commit message
- `drop`: remove commit

---

## 🍒 2. Cherry Pick a Commit

```bash
git cherry-pick <commit-hash>
```

Applies a commit from one branch onto your current branch.

---

## 🔍 3. View Commit Graph (Pretty Log)

```bash
git log --oneline --graph --all --decorate
```

Visualizes the commit history as a graph.

---

## 🚨 4. Reflog – Recover Lost Commits

```bash
git reflog
```

Shows a log of all recent HEAD movements (even those removed from `git log`).

> 💡 Useful when you accidentally `reset --hard` or delete a branch.

---

## 🧹 5. Clean Untracked Files

```bash
git clean -fd
```

Deletes untracked files (`-f`) and directories (`-d`).

> ⚠️ This is **destructive**, use with caution!

---

## 🔐 6. Amend Last Commit

```bash
git commit --amend
```

Modifies the last commit (message or staged content).

---

## 💥 7. Reset to a Specific Commit

```bash
git reset --hard <commit-hash>
```

Resets to a previous state and **deletes all changes** after that commit.

Soft reset (keeps changes staged):

```bash
git reset --soft <commit-hash>
```

Mixed reset (default, keeps changes unstaged):

```bash
git reset <commit-hash>
```

---

## ⏪ 8. Revert Multiple Commits (Without History Rewrite)

```bash
git revert HEAD~3..HEAD
```

Reverts the last 3 commits, one by one.

---

## 🔀 9. Squash Commits (After Feature Work)

```bash
git rebase -i main
```

Squash all commits made on a feature branch before merging to `main`.

---

## ⚙️ 10. Patch Mode Add (Stage Part of a File)

```bash
git add -p
```

Stage only specific **hunks** (sections) of a file interactively.

---

## 📌 11. Create & Track a Remote Branch

```bash
git checkout -b feature-x
git push -u origin feature-x
```

Creates a new local branch and sets it to track a remote branch.

---

## 📂 12. Rename a Branch

```bash
git branch -m old-name new-name
```

If already pushed:

```bash
git push origin :old-name new-name
git push -u origin new-name
```

---

## 🚧 13. Abort Merge or Rebase

```bash
git merge --abort
```

```bash
git rebase --abort
```

---

## 📥 14. Fetch and Rebase Instead of Merge

```bash
git pull --rebase origin main
```

Pulls changes and **rebases your commits on top** instead of merging (cleaner history).

---

## 🔄 15. Set Upstream Branch (If Forgot `-u`)

```bash
git branch --set-upstream-to=origin/main main
```
