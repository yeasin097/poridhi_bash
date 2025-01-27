# Bash Scripting Loop

## What is a Loop?
Loops in Bash scripting allow you to execute a block of code repeatedly based on conditions. They are fundamental for automating repetitive tasks.

---
### 1. For Loop

#### Syntax:
```bash
for variable in list
do
  commands
done
```
#### Example:
```bash
#!/bin/bash
for CHAR in P O R I D H I
do
  echo  ${CHAR}
done
```
Output:
```
P
O
R
I
D
H
I
```
### 2. While Loop

#### Syntax:
```bash
while condition
do
  commands
done
```
#### Example:
```bash
#!/bin/bash
COUNT=1
while [ $COUNT -le 5 ] #-le=less than or equal
do
  echo "Count: $COUNT"
  COUNT=$((COUNT + 1)) #assignmenet operation
done
```
Output:
```
Count: 1
Count: 2
Count: 3
Count: 4
Count: 5
```
### 3. Until Loop

#### Syntax:
```bash
until condition
do
  commands
done
```
#### Example:
```bash
#!/bin/bash
COUNT=1
until [ $COUNT -gt 5 ] #-gt=greater than
do
  echo "Count: $COUNT"
  COUNT=$((COUNT + 1))
done
```
Output:
```
Count: 1
Count: 2
Count: 3
Count: 4
Count: 5
```
### 4. Loop Control Statements
## break
Exits the loop immediately.
#### Example:
```bash
#!/bin/bash
for NUM in {1..10}
do
  if [ $NUM -eq 5 ]; then #-eq=equal to
    break
  fi
  echo "Number: $NUM"
done
```
Output:
```
Number: 1
Number: 2
Number: 3
Number: 4
```
## continue
Skips the rest of the loop for the current iteration and moves to the next iteration.
#### Example:
```bash
#!/bin/bash
for NUM in {1..5}
do
  if [ $NUM -eq 3 ]; then
    continue
  fi
  echo "Number: $NUM"
done
```
Output:
```
Number: 1
Number: 2
Number: 4
Number: 5
```
### 5. Nested Loop
Loops can be nested inside each other.
#### Example:
```bash
#!/bin/bash
for i in {1..3}
do
  for j in {1..3}
  do
    echo "i=$i, j=$j"
  done
done
```
Output:
```
i=1, j=1
i=1, j=2
i=1, j=3
i=2, j=1
i=2, j=2
i=2, j=3
i=3, j=1
i=3, j=2
i=3, j=3
```
## Conclusion
Loops in Bash provide powerful ways to automate repetitive tasks. Practice these loop types and control statements to enhance your scripting skills.




