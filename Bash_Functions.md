# Bash Functions

## What are Functions?
In Bash, functions are reusable blocks of code that help organize and simplify scripts. They make scripts modular, readable, and easier to debug. This guide will teach you how to create and use functions effectively.

### 1. Defining a Function
A function is defined using the `function` keyword or by simply naming it followed by `()`.

#### Syntax:
```bash
function function_name {
  commands
}

# Or

function_name() {
  commands
}
```

#### Example:
```bash
hello() {
  echo "Hello, Bash Functions!"
}

# Call the function
hello
```
Output:
```
Hello, Bash Functions!
```

### 2. Passing Arguments to Functions
Functions can accept arguments, which are accessed using positional parameters `$1`, `$2`, etc., within the function.

#### Example:
```bash
greet() {
  echo "Hello, $1!"
  echo "The year is $2."
}

# Call the function with arguments
greet "poridhi" 2025
```
Output:
```
Hello, poridhi!
The year is 2025.
```

### 3. Returning Values from Functions
Functions can return values using the `return` statement or by echoing the result.

#### Example 1: Using `return` (Integer Values Only):
```bash
add_numbers() {
  return $(( $1 + $2 ))
}

add_numbers 3 5
result=$?
echo "Sum: $result"
```
Output:
```
Sum: 8
```

#### Example 2: Using `echo` (Any Type):
```bash
add_numbers() {
  echo $(( $1 + $2 ))
}

result=$(add_numbers 3 5)
echo "Sum: $result"
```
Output:
```
Sum: 8
```

### 4. Using Local Variables
By default, all variables in Bash are global. To restrict a variable's scope to a function, use the `local` keyword.

#### Example:
```bash
calculate_area() {
  local length=$1
  local width=$2
  echo $(( length * width ))
}

area=$(calculate_area 5 10)
echo "Area: $area"
```
Output:
```
Area: 50
```

### 5. Using Functions in Scripts
Functions can be defined and used within Bash scripts to organize and simplify the code.

#### Example:
```bash
#!/bin/bash

deploy_app() {
  echo "Deploying $1..."
}

deploy_app "MyApplication"
```
Run the script:
```bash
poridhi@ubuntu:~$ ./deploy_script.sh
```
Output:
```
Deploying MyApplication...
```

### 6. Recursion in Functions
Bash supports recursive function calls. Use with caution to avoid infinite loops.

#### Example:
```bash
factorial() {
  if [ $1 -le 1 ]; then
    echo 1
  else
    echo $(( $1 * $(factorial $(( $1 - 1 ))) ))
  fi
}

result=$(factorial 5)
echo "Factorial: $result"
```
Output:
```
Factorial: 120
```

### 8. Best Practices for Functions
1. Use descriptive names for functions to indicate their purpose.
2. Use `local` variables to prevent unexpected modifications.
3. Add comments to explain complex functions.
4. Keep functions short and focused on a single task.
5. Validate input arguments before using them.
6. Use return values or exit codes for error handling.

---

## Conclusion
Functions are a powerful feature in Bash that enable modular and maintainable scripts. By following these examples and best practices, you can enhance your Bash scripting skills and create efficient scripts.
