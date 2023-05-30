# Git Cheat Sheet

## Getting started and configuration:
- To create an empty repository: ` git init . `
- To set your name to be used in the commit history: `git config --global user.name “Your Name”`
- To set your email to be used in the commit history: `git config --global user.email “you@example.com”`
- To replace your name `git config --global --replace-all user.name "Your Name"`
- To replace your email to be used in the commit history: `git config --global --replace-all user.email “you@example.com”`
- To unset your name: `git config --global --unset user.name`
- To unset yout email: `git config --global --unset user.email`
- To list current glabal configration: `git config -l` or `git config --list`
- To solve “fatal: unsafe repository” error : `git config --global --add safe.directory "*"`

## Frequently used commands 

- To show status of the working tree ( git directory) status ( e.g shows changed, added or deleted files): `git status`
- To show all remote and local branches: `git branch -a`
- To show remote branches:  `git branch -r`
- To show local branches: `git branch -l`
- To delete an unneeded branch: `git branch -d <branch_name>`
- To checkout an existing branch `git checkout <branch_name>`
- To create and checkout a new branch: `git branch -b <branch_name>`
- To reset or discard all changes: `git reset --hard`
- To stop tracking a file and remove it: `git rm <path/to/file>`
- To restore a single file `git restore -- <path/to/file>`
- To undo last commit: `git reset --soft HEAD~1`
- To add a file `git add <path/to/file>` 
- To fetch and merge commits from remote repo or a bundle: `git pull`
- To push local changes to remote repo (updates remote refs along with associated objects) `git push`
- To push all local branches to resmote `git push --all origin`
- To merge a branch into the current working branch: `git merge <branch_name>` e.g `git merge master`
- To solve "fatal: cannot do a partial commit during a merge": `git add <path/to/file>` and then `git commit -m "fixed a merge conflict"`
- To create a zip file with all changed, added files etc (ignore deleted) ```git archive --format=zip HEAD `git diff --diff-filter=d HEAD~1 HEAD --name-only` -o paa-patch.zip``` ( this command requires bash - special thanks to V.G. for sharing.)
- To fix "fatal: refusing to merge unrelated histories" `git pull --allow-unrelated-histories`

## Git rebase
- Git rebase is an alternative command to the git merge commands, commits are copied from branch into another branch with out creating a new log entry which happens with the git merge. For example: `Merge branch "master" into "dev"`
- To copy commits from master to dev branch `git checkout dev` and then `git rebase master`
## Git rebase - Scenario 1
- A dev branch is created based on the master branch. `git checkout -b dev`. The dev branch contains new changes that are specific to development environment and not ready to be deploed yet. In the mean time a new branch "hot_fix" is created out of the "dev" branch to fix a production issue and to be tested in the dev environment first `git checkout -b hot_fix`. The hot fix is finally ready to be deployed in production and needs to be merged into the master branch while all 'development' specific changes must be skipped. 
- To rebase commits from hot fix branch into master 
    - figure out the patches since it diverged from the dev `git rebase --onto master dev hot_fix` 
    - followed by `git checkout master`
    - then merge hot fix into master `git merge hot_fix`

## Git merge conflict resolve - Scenario 1
- `git pull` or `git merge <branch_name>`
- `git checkout --their README.md`
- `git add README.md`
- `git commit -m "Fixed README.md merge conflict"`
- `git push `


## Git merge conflict resolve - Scenario 2
- `git pull` or `git merge <branch_name>`
- `git checkout --ours README.md`
- `git add README.md`
- `git commit -m "Fixed README.md merge conflict"`
- `git push`

## Git merge conflict resolve - Scenario 3
- `git pull` or `git merge <branch_name>`
- Identify changes manually, usually separates by "=======". In this example master branch has a text "master+" in the README.md file while "fix" branch has a similar change in the file and line: "master+fix". Merging master into the "fix" branch fails with an error "Automatic merge failed; fix conflicts and then commit the result"
```<<<<<<< HEAD
master+fix
=======
master+
>>>>>>> master
master+fix
```
- `git add README.md`
- `git commit -m "Fixed README.md merge conflict"`
- `git push `

## Viewing the commit history
- To see ASCII graph of branch and merge history [2](#references) : `git log --pretty=format:"%h %s" --graph`
- To see each commit on a single line: `git log --pretty=oneline` or `git log --oneline` or `git log --oneline --graph --decorate`

## Compare two branches:
- git log <original_branch_name>..<work_branch_name> --oneline --graph --decorate --no-merges


## References:
- [1] (https://git-scm.com/book/en/v2)
- [2] (https://git-scm.com/book/en/v2/Git-Basics-Viewing-the-Commit-History)
- [2] (https://git-scm.com/book/en/v2/Git-Branching-Rebasing)