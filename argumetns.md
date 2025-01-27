# Bash Script Arguments

<<<<<<< HEAD
## What is arguments
=======
## What is arguments?
>>>>>>> b2e8afd5f3c75d5ee0b3a1f473c4688ba1d275b2
In Bash, arguments allow scripts to process input from the command line, making them dynamic and versatile. This guide will teach you how to create scripts and handle arguments effectively.

---

### 1. Creating a Bash Script
A Bash script is simply a text file containing commands. To create a script:

#### Steps:
1. Create a new file with the `.sh` extension.
2. Add the shebang line (`#!/bin/bash`) at the top to specify the script interpreter.
3. Write your script commands.
4. Make the script executable using `chmod`.

#### Example:
```bash
poridhi@ubuntu:~$ nano my_script.sh
```
Contents of `my_script.sh`:
```bash
#!/bin/bash

echo "Hello, Bash!"
```
Make the script executable:
```bash
poridhi@ubuntu:~$ chmod +x my_script.sh
```
Run the script:
```bash
poridhi@ubuntu:~$ ./my_script.sh
```
Output:
```
Hello, Bash!
```



### 2. Passing Arguments to a Script
You can pass arguments to a script by appending them after the script name during execution.

#### Example:
Contents of `args_example.sh`:
```bash
#!/bin/bash

# Accessing arguments
echo "Script Name: $0"
echo "First Argument: $1"
echo "Second Argument: $2"
echo "All Arguments: $@"
echo "Number of Arguments: $#"
```
Run the script:
```bash
poridhi@ubuntu:~$ ./args_example.sh arg1 arg2
```
Output:
```
Script Name: ./args_example.sh
First Argument: arg1
Second Argument: arg2
All Arguments: arg1 arg2
Number of Arguments: 2
```



### 3. Special Variables for Arguments
Bash provides several special variables to handle arguments:

| Variable | Description |
|----------|-------------|
| `$0`     | Name of the script |
| `$1, $2, ...` | Positional arguments |
| `$#`     | Number of arguments |
| `$@`     | All arguments (separately quoted) |
| `$*`     | All arguments (single quoted) |
| `$$`     | Process ID of the script |
| `$?`     | Exit status of the last command |
| `$_`     | Last argument of the previous command |



### 4. Best Practices for Argument Handling
1. Always validate the number of arguments using `$#`.
2. Use meaningful variable names to store arguments.

---

## Conclusion
Mastering argument handling in Bash scripting makes your scripts dynamic and robust. Practice these techniques to create more flexible and user-friendly scripts.
