Simulating a Real-Time Merge Conflict in Git
A merge conflict happens when two different branches have changes in the same file, and Git doesn’t know which change to keep.

Let’s create a merge conflict scenario for practice.

🛠 Steps to Create and Resolve a Merge Conflict
1. Create a Repository (If Not Cloned Yet)

git clone https://github.com/your-username/your-repo.git
cd your-repo
or

mkdir merge-conflict-practice && cd merge-conflict-practice
git init
echo "Hello, Git!" > conflict.txt
git add conflict.txt
git commit -m "Initial commit"
2. Create and Switch to a New Branch

git checkout -b feature-branch
Modify the conflict.txt file:


echo "This is a change from feature-branch." > conflict.txt
Save and commit the change:


git commit -am "Update from feature-branch"
3. Switch Back to main Branch and Edit the Same File

git checkout main
Modify the conflict.txt file differently:


echo "This is a change from the main branch." > conflict.txt
Save and commit the change:


git commit -am "Update from main branch"
4. Merge feature-branch Into main


git merge feature-branch
🔴 You will see a merge conflict because both branches modified conflict.txt differently.

5. Resolve the Merge Conflict
Run:

git status
Git will show:

both modified: conflict.txt
Edit conflict.txt manually. You will see something like:

vi conflict.txt:

<<<<<<< HEAD
This is a change from the main branch.
=======
This is a change from feature-branch.
>>>>>>> feature-branch
Resolve it by choosing the correct content:


This is a merged version keeping the best of both changes.
Save the file, then stage and commit the resolution:


git add conflict.txt
git commit -m "Resolved merge conflict in conflict.txt"
6. Push Changes to Remote

git push origin main
