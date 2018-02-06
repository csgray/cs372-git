# CS 372 - Homework 1: working with Git

## Part A: Creating and Using a Repository
1. Created a new repo on GitHub.
2. Created a new directory on my computer, launched PowerShell in it (already configured to support git), and ran “git init” then “git remote add origin https://github.com/csgray/cs372-git.git”.
3. Created “README.md” in that directory (this file) and committed it to the master branch using “git add” and “git commit -m ‘Add README.md’”
4. Pushed to remote repo using "git push -u origin master"
5. Forgot to save after writing this stuff, so I pushed an empty but new file. Saved, added, committed, and pushed actual content.
6. Created a new branch called "merge" with "git checkout -b merge".
7. Added some fluff and committed it.
8. Pushed to the repo, making a new branch, with "git push --set-upstream origin merge".
9. Switched to master branch and merged merge branch with "git merge merge" (admittedly not the best choice of names). Clean fast-forward.
10. Added some more stuff to the master branch and committed it.
11. Switched back to merge, added some nonsense, and committed that.
12. Switched back to master and tried to merge "merge" back in. CONFLICT!

I am using Visual Studio Code to write this file, and its built-in Git support is actually pretty nice. It not only automatically updated the content of this file with the merge conflict, but it highlighted and labeled the current change and incoming change accordingly. There were even buttons for "Accept Current Change | Accept Incoming Change | Accept Both Changes | Compare Changes" directly above the conflict. "Compare Changes" opens a second tab with the two branches side-by-side and featuring only the conflicting code.

![Screenshot of Video Studio Code displaying a Git conflict](https://raw.githubusercontent.com/csgray/cs372-git/master/conflict.jpg "I honestly wasn't expecting something this nice.")

I decided to clean it up manually and add all this fluff.

13. Fixed the merge, committed it, and pushed it. Included a picture of how Visual Studio handles merging. 
14. Tried to delete the 'merge' branch with "git branch -d merge" but was told it wasn't fully merged yet. I had to checkout merge again, push it to GitHub, then switch back to master before I could delete merge without any complaints. I could have overriden the check with "git branch -D merge" but I wanted to see why it was erroring. That also updated merge's position on the network map.
15. Finished up this explanation, fixed the grammar and formatting, committed it, and pushed it! Done!

![Screenshot of the Git Network diagram showing the branch history](https://raw.githubusercontent.com/csgray/cs372-git/master/network.jpg "It's nothing special, but it does show what happened.")