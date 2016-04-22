# Unix Cheatsheet

## Create a file
```bash
:> filename.extension
```

## Get current Unix shell details

```bash
ps -p $$
```

Explaination: `$$` is the current pid.

## Find then kill process bound on port

```bash
fuser 5858/tcp
fuser -k 5858/tcp
```

Explaination: The `fuser` command is a very smart unix utility used to find which process is using a file, a directory or a socket. `-k` kills the process using the named file.

## Folders from list file
while read line; do mkdir -p "${line%/*}"; done < ./list

./list:
```bash
folderone
foldertwo
```

Runnig the command makes two folders


## Find folders that are older than N (where N = days)

```bash
  find /path/to/folder/* -type d -ctime +3 | xargs echo
  find /path/to/folder/* -type d -ctime +N | xargs rm -rf
```

## Nice column views
```bash
 command | column -t
```