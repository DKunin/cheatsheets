# Unix Cheatsheet

## Create a file
```
:> filename.extension
```

## Get current Unix shell details

```
ps -p $$
```

Explaination: `$$` is the current pid.

## Find then kill process bound on port

```
fuser 5858/tcp
fuser -k 5858/tcp
```

Explaination: The `fuser` command is a very smart unix utility used to find which process is using a file, a directory or a socket. `-k` kills the process using the named file.

## Folders from list file
while read line; do mkdir -p "${line%/*}"; done < ./list

./list:
```
folderone
foldertwo
```

Runnig the command makes two folders