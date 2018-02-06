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

## Part C: Three Git Commands
### git reset --hard \<commit ID>
This _kind of_ defeats the purpose of Git, so it isn't officially recommended - but there's been times when I've needed to destroy stuff. This command does it. It irrevocably rolls your repository, meaning all the files in your local directory, back to whatever state it had at that commit ID (which you get from examining git log). The changes are gone. The commits are gone. It's like everything that happened after that commit never happened.

If you use "git reset --hard HEAD" it blows away all the changes to your files since your last commit. Which is still kind of scary but nice for when your code has gone pear-shaped and you want a fresh start with something that worked.

### git clean
This command gets rid of everything in your repository that shouldn't be there, meaning everything that shows up under "untracked files" when you check "git status". Stuff deleted by Git doesn't go to the Recycle Bin, so make sure you really want to delete it. This command has some useful flags.

**-d** will delete untracked directories in addition to files. 

**-f** means "force" or "Yes, really, delete all the things. I mean it." You'll probably have to use this if you haven't modified your configuration file to change "clean.requireFalse" to false.

**-i** starts "interactive mode" where instead of deleting things automatically Git will present you with options to delete them all, ask for each file, delete according to a filter, select multiple files to delete, quit, or displayhelp.

**-n** shows you what will be deleted if you run that command again without "-n" but doesn't actually delete anything.

**-q** means "quiet" so Git won't tell you which files you just deleted. Otherwise it displays a list of "Removing..."

**-e /<pattern>** means "exclude" and lets you specify additional files to ignore according to some pattern. Usually, the only files Git spares are those you tell it to in .gitignore. This lets you tell it to ignore a bunch of other files as well.

**-x** means "delete everything untracked" including all the things on .gitignore. No files are spared.

**-X** only deletes the stuff that is on .gitignore.

If you really hate all of the stuff cluttering up your repository, try "git clean -xdf" which deletes all ignored files, all untracked directories, really, no second chances.

### git cherry-pick \<commit ID>
This command lets you be very selective about what you merge into your code. Rather than do an entire branch all at once, it lets you merge individual commits. Each commit that is added to your code also gets its own commit on your branch, instead of one large merge commit, so you can even progressively roll things back. 

This command has a _lot_ of options, so you should check them all out at https://git-scm.com/docs/git-cherry-pick