# Git Cheatsheet

## Eradicate branch
```
git branch -D :localbranch
git push origin --delete :remote_branch
```


## Merge branch without merge commit

```
git checkout master
git checkout -b feature/foo

# make some commits

git rebase master
git checkout master
git merge --ff-only feature/foo
```

[Source](http://stackoverflow.com/a/16358699/5147646)

# Blame line from file
```
git blame -L $RANGE  $PATH_TO_FILE

$RANGE = 1,2
```
## Reset to commit

# Reset the index to the desired tree
      git reset 56e05fced

# Move the branch pointer back to the previous HEAD

      git reset --soft HEAD@{1}
      git commit -m "Revert to 56e05fced"

# Update working copy to reflect the new commit
      git reset --hard

# Interactive add to commit
      git add -p

# List of contributors
      git shortlog -sn

# Lines of code written today
      git diff --shortstat "@{1 day ago}"


# Remove local branches
      git remote update --prune
Remove local branches that have been deleted from your remote (like GitHub). You can always run ```git remote prune origin --dry-run``` to see what will be deleted before going all in.

# Reset local changes
      git reset
      git checkout .

# Reset only one file
      git checkout [NAME_OF_ORIGINAL_BRANCH] -- [NAME_OF_THE FILE]
