# Git Cheat Sheet

## Getting started:
- To create an empty repository: ` git init . `
- To set your name to be used in the commit history: `git config --global user.name “Your Name”`
- To set your email to be used in the commit history: `git config --global user.email “you@example.com”`
- To replace your name `git config --global --replace-all user.name "Your Name"`
- To replace your email to be used in the commit history: `git config --global --replace-all user.email “you@example.com”`
- To unset your name: `git config --global --unset user.name`
- To unset yout email: `git config --global --unset user.email`
- To solve “fatal: unsafe repository” error : `git config --global --add safe.directory "*"`

## Frequently used commands 

- To show status of the working tree ( git directory) status: `git status`
- To show all remote and local branches: `git branch -a`
- To show remote branches:  `git branch -r`
- To show local branches: `git branch -l`
- To delete an unneeded branch: `git branch -d <branch_name>`
- To checkout an existing branch `git checkout <branch_name>`
- To create and checkout a new branch: `git branch -b <branch_name>`
- To reset or discard all changes: `git reset --hard`
- To stop tracking a file and remove it: `git rm <path/to/file>`
- To restore a single file `git restore <path/to/file>`'
- To undo last commit: `git reset --soft HEAD~1`
- To merge a branch into the current working branch `git merge <branch_name>` e.g `git merge master'`
- 
#### References:
[1] (https://git-scm.com/book/en/v2)
