# Git Merge Conflict Practice

## Introduction
This repository demonstrates how to create and resolve merge conflicts in Git. Merge conflicts occur when two branches modify the same file in different ways, and Git cannot automatically determine which changes to keep.

## Setup
To practice resolving a merge conflict, follow these steps:

### 1. Clone the Repository (If Not Created Yet)
```sh
git clone https://github.com/your-username/your-repo.git
cd your-repo
```
Or initialize a new one:
```sh
mkdir merge-conflict-practice && cd merge-conflict-practice
git init
echo "Hello, Git!" > conflict.txt
git add conflict.txt
git commit -m "Initial commit"
```

### 2. Create and Switch to a New Branch
```sh
git checkout -b feature-branch
```
Modify `conflict.txt`:
```sh
echo "This is a change from feature-branch." > conflict.txt
```
Commit the change:
```sh
git commit -am "Update from feature-branch"
```

### 3. Switch Back to `main` Branch and Edit the Same File
```sh
git checkout main
```
Modify `conflict.txt` **differently**:
```sh
echo "This is a change from the main branch." > conflict.txt
```
Commit the change:
```sh
git commit -am "Update from main branch"
```

### 4. Merge `feature-branch` Into `main`
```sh
git merge feature-branch
```

**Merge Conflict Occurs:**
Git will show:
```
both modified: conflict.txt
```

### 5. Resolve the Merge Conflict
Open `conflict.txt`, and you will see:
```txt
<<<<<<< HEAD
This is a change from the main branch.
=======
This is a change from feature-branch.
>>>>>>> feature-branch
```
Modify it to:
```txt
This is a merged version keeping the best of both changes.
```
Save the file, then **stage and commit the resolution**:
```sh
git add conflict.txt
git commit -m "Resolved merge conflict in conflict.txt"
```

### 6. Push Changes to Remote
```sh
git push origin main
```

## Conclusion
Merge conflicts are a common part of collaborative Git workflows. Knowing how to resolve them efficiently is a crucial skill for developers. Happy coding! 🚀

