# Unix Cheatsheet

[Source](http://ricostacruz.com/cheatsheets/sh.html)

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

## Basic for loop
```bash
for i in /etc/rc.*; do
  echo $i
done
```

## Ranges
```bash
for i in {1..5}; do
    echo "Welcome $i"
done
```

## Reading lines
```bash
cat file.txt | while read line; do
  echo $line
done
```

#Defining functions
```bash
myfunc() { ... }
fuction myfunc { ... }
fuction myfunc() { ... }
```

## Returning strings
```bash
myfunc() {
    local myresult='some value'
    echo $myresult
}

result=$(myfunc)
```

## Arguments
```bash
$#                          # Number of arguments
$*                          # All args
$1                          # First argument
```

## Ifs

```bash
# File conditions

if [ -a FILE ]; then        # -e exists         -d directory        -f file
fi                          # -r readable       -w writeable        -x executable
                            # -h symlink        -s size > 0
# File comparisons
if [ FILE1 -nt FILE2 ]      # -nt   1 more recent than 2
                            # -ot   2 more recent than 1
                            # -ef   same files
# String
if [ -z STRING ]            # empty?
if [ -n STRING ]            # not empty?

# Numeric
if [ $? -eq 0 ]             # -eq -ne -lt -le -gt -ge
                            # $? is exit status by the way

# Etc
if [ -o noclobber ]         # if OPTIONNAME is enabled
if [ ! EXPR ]               # not
if [ ONE -a TWO ]           # and
if [ ONE -o TWO ]           # or

# Regex
if [[ "A" =~ "." ]]

```

## Numeric comparisons

```bash
if (( $a < $b ))
```

## Arrays

```bash
# Declaring using declare -a
declare -a Fruits=('Apple' 'Banana' 'Orange')

Fruits[0]="Apple"
Fruits[1]="Banana"
Fruits[2]="Orange"

echo ${Fruits[0]}           # Element #0
echo ${Fruits[@]}           # All elements, space-separated
echo ${#Fruits[@]}          # Number of elements
echo ${#Fruits}             # String length of the 1st element
echo ${#Fruits[3]}          # String length of the Nth element
echo ${Fruits[@]:3:2}       # Range (from position 3, length 2)

# Operations

Fruits=("${Fruits[@]}" "Watermelon")    # Push
Fruits=( ${Fruits[@]/Ap*/} )            # Remove by regex match
unset Fruits[2]                         # Remove one item
Fruits=("${Fruits[@]}")                 # Duplicate
Fruits=("${Fruits[@]}" "${Veggies[@]}") # Concatenate
lines=(`cat "logfile"`)

# Iteration

for i in "${arrayName[@]}"; do
  echo $i
done

```
