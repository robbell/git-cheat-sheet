# Git Cheat Sheet

## Commands

### Identifying differences

Unstaged differences:

`git diff`

Staged differences:

`git diff --staged`

Differences between two specific versions:

`git diff versionA versionB`

Differences in a range of versions:

`git diff version1..version2`

`git diff branchA..branchB`

Only show affected files:

`git diff --name-only version1..version2`

### Viewing history

View all changes to a specific file:

`git log -p filename`

Using `-p` generates a patch of the differences. Removing this will show the commit messages:

`git log -p --follow filename`

`--follow` will show changes to a file across renames

View all files under source control:

`git ls-files`

### Branching

Remove local pointers to remote branches which no longer exist:

`git remote prune origin`

Get all branches which have been merged into a named branch:

`git branch --merged branchname`

Or all branches _not_ merged:

`git branch --no-merged branchname`

Deleting a remote branch:

`git push origin --delete branchname`

Use `-D` if the branch hasn't been merged as a shortcut to `--delete --force`

## Common problems

### Accidentally commiting to develop locally

Create new branch at the same point:

`git checkout -b feature/branch-i-meant-to-create`

Point develop back to the same commit as origin/develop:

`git branch -f develop origin/develop`

## Configuration

Add the following to your .gitconfig file (located in C:\Users\[username]):

```
[alias]
    co=checkout
    ci=commit
    st=status
    br=branch
    hist=log --pretty=format:'%h %ad | %s%d [%an]' --graph --date=short
    la=log --all --graph --oneline --decorate
    unstage=reset HEAD --
[diff]
	tool = p4merge
[difftool "p4merge"]
	cmd = p4merge $LOCAL $REMOTE
[merge]
	tool = p4merge
[mergetool "p4merge"]
	cmd = p4merge $BASE $LOCAL $REMOTE $MERGED
[core]
	editor = code --wait
[mergetool]
	keepBackup = false
```
#### Adding aliases at the command line

    git config --global alias.[Name] [Definition]
    git config --global alias.la 'log --all --graph --oneline --decorate'
