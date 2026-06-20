# Daily Git Workflow for Keeping Your Branch Updated with Main

## 1. Commit Your Work First

Before pulling changes from `main`, save your work:

```bash
git add .
git commit -m "Complete dayX exercises"
```

## 2. Get the Latest Changes from Remote

```bash
git fetch origin
```

## 3. Switch to Your Branch

```bash
git checkout anuj-solutions
```

## 4. Merge the Latest Main Branch

```bash
git merge origin/main
```

## 5. If There Are Conflicts

Check the status:

```bash
git status
```

For each conflicted file:

### Keep Your Version

```bash
git checkout --ours <file>
```

### Keep Main's Version

```bash
git checkout --theirs <file>
```

### Or Manually Merge

Open the file, combine the changes, then save it.

Mark the conflict as resolved:

```bash
git add <file>
```

When all conflicts are resolved:

```bash
git commit
```

---

# Working with Jupyter Notebook Conflicts (`.ipynb`)

Notebook files are JSON files, so conflicts can be difficult to resolve manually.

### If You Worked on the Notebook Today

Usually keep your version:

```bash
git checkout --ours notebook.ipynb
git add notebook.ipynb
```

### If the Owner Added New Content and You Don't Have Important Changes

Take the main branch version:

```bash
git checkout --theirs notebook.ipynb
git add notebook.ipynb
```

### If Both Versions Contain Important Changes

Compare both versions and manually merge the notebook contents.

---

# Useful Commands

## See All Conflicted Files

```bash
git diff --name-only --diff-filter=U
```

## Abort a Merge

```bash
git merge --abort
```

## See Changes Available in Main

```bash
git log --oneline HEAD..origin/main
```

---

# Recommended Daily Routine

```bash
git add .
git commit -m "WIP"

git fetch origin

git checkout anuj-solutions

git merge origin/main
```

### Why?

Merging daily keeps conflicts small and easy to resolve. Waiting several days often results in larger and more difficult merge conflicts, especially for Jupyter notebooks.
