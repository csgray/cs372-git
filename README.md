# CS 372 - Homework 1: Git Example
1. Created a new repo on GitHub.
2. Created a new directory on my computer, launched PowerShell in it (already configured to support git), and ran “git init” then “git remote add origin https://github.com/csgray/cs372-git.git”.
3. Created “README.md” in that directory (this file) and committed it to the master branch using “git add” and “git commit -m ‘Add README.md’”
4. Pushed to remote repo using "git push -u origin master"
5. Forgot to save so I pushed an empty but new file. Saved, added, committed, pushed actual content.
6. Created a new branch called "merge" with "git checkout -b merge".
7. Added some fluff and committed it.
8. Pushed it to the repo, making a new branch, with "git push --set-upstream origin merge".
9. Switched to master branch and merged merge branch with "git merge merge". (Not the best choice of names). Clean fast-forward.
10. Added some more stuff to the master branch and committed it.
11. Switched back to merge, added some nonsense, and committed that.
12. Switched back to master and tried to merge "merge" back in. CONFLICT!

I am using Visual Studio Code to write this file, and it's built-in Git support is actually pretty nice. It not only automatically updated the content of this file with the merge conflict,but it highlighted and labeled the current change and incoming change accordingly. There were even buttons for "Accept Current Change | Accept Incoming Change | Accept Both Changes | Compare Changes" directly above the conflict. "Compare Changes" opens a second tab with two branches side-by-side and featuring only the conflicting code.

I decided to clean it up manually and add all this fluff.