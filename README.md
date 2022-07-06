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
- To restore a single file `git restore -- <path/to/file>`'
- To undo last commit: `git reset --soft HEAD~1`
- To add a file `git add <path/to/file>` 
- To fetch and merge commits from remote repo or a bundle: `git pull`
- To push local changes to remote repo (updates remote refs along with associated objects) `git push`
- To merge a branch into the current working branch: `git merge <branch_name>` e.g `git merge master`
- To solve "fatal: cannot do a partial commit during a merge": `git add <path/to/file>` and then `git commit -m "fixed a merge conflict"`
- To create a zip file with all changed, added files etc (ignore deleted) `git archive --format=zip HEAD `git diff --diff-filter=d HEAD~1 HEAD --name-only` -o paa-patch.zip` ( this command requires bash - special thanks to V.G. for sharing.)

## Viewing the commit history
- To see ASCII graph of branch and merge history [2](#references) : `git log --pretty=format:"%h %s" --graph`
- To see each commit on a single line: `git log --pretty=oneline` or `git log --oneline` or `git log --oneline --graph --decorate`


## References:
- [1] (https://git-scm.com/book/en/v2)
- [2] (https://git-scm.com/book/en/v2/Git-Basics-Viewing-the-Commit-History)