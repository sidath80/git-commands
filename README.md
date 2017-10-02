# git-commands

Part 1 - Routine Git Commands Cheatsheet

Clone a Remote Git Repository

git clone git@github.com:ebuilderCCO/service-entry-worker-mi.git
git branch -a
git status
Create a custom branch (e.g. wimal), Switch to Custom Branch

git branch -a
git checkout -b wimal
git branch -a
git status
Add and Commit to Local GIT Repo Branch

git add index.js public/myscripts.js
git commit -m "Adding changes"
Switch to a different branch

git branch -a
git checkout develop
Update origin pointer of Local Repo from Remote Git Repo

git branch -a
git fetch
Delete Temporary Branch (e.g. wimal)

git branch -d wimal

Upload a New Branch to Remote Git Repo

git push --set-upstream origin workflow

Revert a change for done for a file

git checkout myfiletorevert.js

Create a new Repo in GitHub

Create a git repository in the github website (e.g. my-mi in organization tech-magic).
Prompt into the folder you want to associate the remote git repository.
echo "# my-mi" >> README.md
git init
git add README.md
git commit -m "first commit"
git remote add origin git@github.com:tech-magic/my-mi.git
git push -u origin master
git branch -a
Remove files added accidentally

git rm -f logstash-mi-appender/pom.xml~
git commit -m "Removing unwanted files"
Resolve conflict using my files

git status
The conflicted files will be listed as both modified
Select a conflicted file
Browse the file contents. Find places with <<<<<< and >>>>> marks. The marks indicate which changes come from foreign or local branch. Resolve the conflicts manually.
git add path_to_conflicted_file
git commit -m 'Resolved Conflict'
git push
Resolve conflict using their files

git status
The conflicted files will be listed as both modified
Select a conflicted file
git checkout --theirs path_to_conflicted_file
git add path_to_conflicted_file
git commit -m 'Resolved Conflict'
git push
Merge Committed files in custom branch (e.g. wimal) to local develop branch and push it to remote develop branch

git branch -a
git pull (update the local develop from remote develop branch)
git merge wimal (then resolve conflicts)
git status
git add changed_file1.html changed_file2.js
git commit -m "Adding merged changes"
git push
Part 2 - Migrate from an old GIT repo to a new GIT repo while saving revision history

Let's assume we call "old repo" the repository you wish to move, and "new repo" the one you wish to move to.

Make sure you have a local copy of all "old repo" branches and tags.

Fetch all of the remote branches and tags: git fetch origin

View all "old repo" local and remote branches: git branch -a

If some of the remotes/ branches doesn't have a local copy, checkout to create a local copy of the missing ones: git checkout -b <branch> origin/<branch>

Now we have to have all remote branches locally.

Add a "new repo" as a new remote origin:

git remote add new-origin git@github.com:user/repo.git

Step 3. Push all local branches and tags to a "new repo".

Push all local branches (note we're pushing to new-origin): git push --all new-origin

Push all tags: git push --tags new-origin

Remove "old repo" origin and its dependencies.

View existing remotes (you'll see 2 remotes for both fetch and push) git remote -v

Remove "old repo" remote: git remote rm origin

Rename "new repo" remote into just 'origin': git remote rename new-origin origin

Done! Now your local git repo is connected to "new repo" remote which has all the branches, tags and commits history.
