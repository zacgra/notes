# Conditionals

```sh
# if/elif/else
if test1
then
  command1
elif test2
then
  command2
else
  command3
fi
```

```sh
# case
case expression in
  match_1) statement ;;
  match_2) statement ;;
  match_n) statement ;;
  *)       statement ;;
esac
# use * as default
# terminate case with ;;
```

## If - Test & Square Brackets

Using `test`

```sh
  if test -f "$FILE";
```

Using square brackets

```sh
  if [ -f "$FILE" ];
```

or nested square brackets

```sh
if [[ -f "$FILE" ]];
```

## Example: Checking File Existence

Single Line with chaining:

```sh
FILE = ./my_file.txt
test -f $FILE && echo "$FILE exists."
# ./my_file.txt exists.
```

Multi-line with if:

```sh
FILE = ./my_file.txt
if test -f "$FILE"; then
    echo "$FILE exists."
fi
# ./my_file.txt exists.
```

If file doesn't exist, create file

```sh
[ ! -f $FILE ] && { echo "$FILE doesn't exist, creating file..."; touch $FILE; }
```

## Checking Directory Existence

```sh
  MY_DIR=./my_folder
  touch ./my_folder # create my_folder as a file rather than directory
  [ -d $MY_DIR ] || { echo "$MY_DIR doesn't exist. Creating..."; mkdir $MY_DIR;}\
   && { echo "Created."; }
```
