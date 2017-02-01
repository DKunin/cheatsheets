# Git Cheatsheet

## Eradicate branch
```console
git branch -D :localbranch
git push origin --delete :remote_branch
```
## Remove merged branches 

Remember to make backups!

```console
git branch --merged | grep -v \* | xargs git branch -D 
```

## Merge branch without merge commit

```console
git checkout master
git checkout -b feature/foo

# make some commits

git rebase master
git checkout master
git merge --ff-only feature/foo
```

[Source](http://stackoverflow.com/a/16358699/5147646)

# Blame line from file
```console
git blame -L $RANGE  $PATH_TO_FILE

$RANGE = 1,2
```
## Reset to commit

# Reset the index to the desired tree
```console
      git reset 56e05fced
```

# Move the branch pointer back to the previous HEAD
```console
      git reset --soft HEAD@{1}
      git commit -m "Revert to 56e05fced"
```

# Update working copy to reflect the new commit
```console
      git reset --hard
```

# Interactive add to commit
```console
      git add -p
```

# List of contributors
```console
      git shortlog -sn
```

# Lines of code written today
```console
      git diff --shortstat "@{1 day ago}"
```


# Remove local branches
```console
      git remote update --prune
```
Remove local branches that have been deleted from your remote (like GitHub). You can always run ```git remote prune origin --dry-run``` to see what will be deleted before going all in.

# Reset local changes
```console
      git reset
      git checkout .
```

# Reset only one file
```console
      git checkout [NAME_OF_ORIGINAL_BRANCH] -- [NAME_OF_THE FILE]
```

# Extract a file from another branch
```console
      git show some-branch:some-file.js
```

# Ignore the white space
```console
      git diff -w
```

# Only “add” some changes from a file
```console
      git add -p
```

# Stash only some files
```console
      git stash -p
```

[Source](http://ohshitgit.com/)

# Rename branch
```console
      git branch -m old_branch new_branch         # Rename branch locally    
      git push origin :old_branch                 # Delete the old branch    
      git push --set-upstream origin new_branch   # Push the new branch, set local branch to track the new remote
```

# Commit to right branch
```console
      git reset HEAD~ --soft # undo the last commit, but leave the changes available
      git add .
      git stash

      git checkout name-of-the-correct-branch # move to the correct branch
      git stash pop
      git add .
      git commit -m "your message here"
```

# No diff 
```console
      git diff --staged
```

# Get list of changed files, between commits
```console
      git diff --name-only HEAD HEAD~14
```

# Revert merge commit
```console
      git revert -m 1 [sha_of_commit]
```

# Get log dates
```console
      git log --pretty="%cd" --author="Dmitry Kunin" --since="2016-01-01" --before="2016-12-27" --no-merges > ../avito-log
```

# Sqaush commits
```console
      git rebase -i HEAD~3
```

Where 3 is number of commits you want to squash back