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

Only show affected files

`git diff --name-only version1..version2`

## Configuration

### Useful aliases

    alias.co=checkout
    alias.ci=commit
    alias.st=status
    alias.br=branch
    alias.hist=log --pretty=format:'%h %ad | %s%d [%an]' --graph --date=short
    alias.unstage=reset HEAD --

### Configuring P4Merge

`git config --global merge.tool p4merge`

`git config --global mergetool.p4merge.cmd 'p4merge $BASE $LOCAL $REMOTE $MERGED'`
