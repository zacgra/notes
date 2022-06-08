Validating Input & "Returning" a value

There is a lot going on here, so lets take it one step at a time:

1. get_validated_input is called
2. we create a local variable of user_input so we can return our value
   after exiting the while loop.
3. we enter the while loop
4. we echo using `>&2` so that our output will get displayed which then enters a while loop.
5. we echo out

```sh
get_input() {
  read choice
  echo $choice
}

get_validated_input(){
  local user_input=""
  while true; do
    echo >&1 -n "Choose between spaces or tabs: "
    user_input=$( get_input )

    if [ "$user_input" = "tabs" ] || [ "$user_input" = "spaces" ]; then
      echo >&1 "Ah, $user_input. You have chosen wisely.\n"
      break
    fi
  done
  echo $user_input
}

validated_input=$( get_validated_input )
echo "The output is: $validated_input"

exit 1
```
