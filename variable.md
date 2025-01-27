# Bash Scripting Variables

## What is a Variable?
A variable is a named storage location that holds data. In shell scripting, variables are used to store and manipulate data such as strings, numbers, and file paths.

---

### 1. Declaring Variables

#### Syntax:
```bash
VARIABLE_NAME=value
```
- No spaces around the `=` sign.
- Variable names are case-sensitive and typically use uppercase by convention.
- Do not start variable names with numbers or special characters.

#### Example:
```bash
poridhi@ubuntu:~$ NAME="poridhi.io"
poridhi@ubuntu:~$ YEAR=2025
```


### 2. Accessing Variables
To use a variable, prefix its name with a `$`.

#### Syntax:
```bash
$VARIABLE_NAME
```

#### Example:
```bash
poridhi@ubuntu:~$ echo $NAME
poridhi.io
poridhi@ubuntu:~$ echo "I am learning from $NAME."
I am learning from poridhi.io.
poridhi@ubuntu:~$ echo "I started learning from $YEAR"
I started learning from 2025.
```

### 3. Types of Variables

#### a. Local Variables
- Defined and used within a script or function.
- Not accessible outside their scope.

#### Example:
```bash
function local_example {
  LOCAL_VAR="Local Value"
  echo $LOCAL_VAR
}
local_example
# This will not work outside the function
echo $LOCAL_VAR
```
#### Ouput:


#### b. Environment Variables
- Available to the script and its child processes.
- Set using the `export` command.

#### Example:
```bash
poridhi@ubuntu:~$ export ENV_VAR="Environment Value"
poridhi@ubuntu:~$ echo $ENV_VAR
Environment Value
```

#### c. Special Variables
Bash provides special variables with predefined meanings:

| Variable | Description |
--|
| `$0`     | Name of the script |
| `$1, $2, ...` | Positional arguments passed to the script |
| `$#`     | Number of positional arguments |
| `$@`     | All arguments as a single string |
| `$$`     | Process ID of the script |
| `$?`     | Exit status of the last executed command |
| `$_`     | Last argument of the previous command |

#### Example:
```bash
#!/bin/bash
echo "Script Name: $0"
echo "First Argument: $1"
echo "Number of Arguments: $#"
```
Run with:
```bash
bash script.sh arg1 arg2
```
Output:
```
Script Name: script.sh
First Argument: arg1
Number of Arguments: 2
```


### 4. Assigning Command Output to Variables
You can store the output of a command in a variable using command substitution.

#### Syntax:
```bash
VARIABLE=$(command)
```

#### Example:
```bash
CURRENT_DATE=$(date)
echo "Today is $CURRENT_DATE"
```
Output:
```
Today is Mon Jan 27 12:34:56 UTC 2025
```


### 5. Read-Only Variables
To make a variable immutable, use the `readonly` keyword.

#### Example:
```bash
readonly PI=3.14159
PI=3.14 # This will throw an error
```


### 6. Unsetting Variables
You can remove a variable using the `unset` command. Note that readonly variables cannot be unset.

#### Syntax:
```bash
unset VARIABLE_NAME
```

#### Example:
```bash
poridhi@ubuntu:~$ NAME="Temporary"
poridhi@ubuntu:~$ echo $NAME
Temporary
poridhi@ubuntu:~$ unset NAME
poridhi@ubuntu:~$ echo $NAME # This will be empty

```


### 7. Arrays in Bash Variables
Bash supports arrays to store multiple values.

#### Declaring an Array:
```bash
poridhi@ubuntu:~$ ARRAY_NAME=(value1 value2 value3)
```

#### Accessing Array Elements:
```bash
poridhi@ubuntu:~$ echo ${ARRAY_NAME[0]} # First element
poridhi@ubuntu:~$ echo ${ARRAY_NAME[@]} # All elements
```

#### Example:
```bash
poridhi@ubuntu:~$ COLORS=(red green blue)
poridhi@ubuntu:~$ echo ${COLORS[0]}
red
poridhi@ubuntu:~$ echo "First color: ${COLORS[0]}"
First color: red
poridhi@ubuntu:~$ echo "All colors: ${COLORS[@]}"
red green blue
poridhi@ubuntu:~$ COLORS[3]=yellow
poridhi@ubuntu:~$ echo "Updated colors: ${COLORS[@]}"
Updated colors: red green blue yellow
```


### 8. Variable Scope

#### Global Variables
- Default scope for variables defined outside functions.

#### Local Variables
- Use `local` keyword within functions.

#### Example:
```bash
function scope_example {
  local LOCAL_VAR="I am local"
  GLOBAL_VAR="I am global"
  echo $LOCAL_VAR
}
scope_example
echo $GLOBAL_VAR # Accessible
echo $LOCAL_VAR  # Not accessible
```


### 9. Best Practices

1. Use descriptive and meaningful names (e.g., `USERNAME`, `FILE_PATH`).
2. Always quote variables to prevent unexpected word splitting:
   ```bash
   echo "Variable: $VARIABLE"
   ```
3. Initialize variables before using them.
4. Use uppercase for constants or environment variables.
5. Use `local` for function-specific variables to avoid side effects.

---

## Conclusion
Variables are fundamental to Bash scripting, enabling flexibility and dynamic behavior. Practice these concepts to build more robust scripts.
