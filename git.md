# Git Cheatsheet

## Eradicate branch
```
git branch -D :localbranch
git push origin --delete :remote_branch
```

### Example
```
git branch -D AVPM-15319-email
git push origin --delete AVPM-15319-email
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

git blame -l $PATH_TO_FILE | grep 738