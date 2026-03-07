# Bash if Condition 
<br></br>
<p align="center">
  <img src="images/shell_transparent.png" width="150">
</p>
<br></br>

 #### What is if Condition?
`if ` is used to make decisions in Bash.
Example:
“Do this only if the condition is true.”

In Bash, conditions return:
```
0 → TRUE
Non-zero → FALSE
```

This is opposite to some programming languages where 1 means true.

### 1️⃣ Basic if Statement
🔹 Syntax
```Bash
if [ condition ]
then
    commands
fi
```
🔹 Example
```Bash
#!/bin/bash

num=10

if [ $num -eq 10 ]
then
    echo "Number is 10"
fi
```
#### How condition works internally?

When you write:
```bash
if [ $num -eq 10 ]
```
    $ `[  ]` is actually a command called test

    $ It checks the condition

    $ If condition is true → exit status = 0

    $ If false → exit status ≠ 0

Then if checks the exit status.

#### Important Rules

    $  Space is mandatory after [ and before ]

    $  Always close with fi

> Use indentation for readability

### 2️⃣ if-else Statement

Used when we want two possibilities.
🔹 Syntax
```Bash
if [ condition ]
then
    commands
else
    commands
fi
```
🔹 Example
```Bash
#!/bin/bash

num=5

if [ $num -gt 10 ]
then
    echo "Greater than 10"
else
    echo "Less than or equal to 10"
fi
```
#### Why use if-else?

    $  `if-else` is used when a condition has two possible outcomes.

#### It ensures:

    $  One block runs if true

    $  Another block runs if false

    $  This improves:

    $  Script clarity

    $  Logical flow
 
    $  Error handling

`-gt` → greater than
If condition false → else block runs

### 3️⃣ if-elif-else (Multiple Conditions)

Used when checking multiple cases.
🔹 Syntax
```Bash
if [ condition ]
then
    commands
elif [ condition ]
then
    commands
else
    commands
fi
```
🔹 Example
```Bash
#!/bin/bash

num=0

if [ $num -gt 0 ]
then
    echo "Positive"
elif [ $num -lt 0 ]
then
    echo "Negative"
else
    echo "Zero"
fi
```

#### Why use multiple conditions?

When there are more than two possibilities, `elif` helps avoid multiple separate `if` blocks.

#### How it works

    $  Bash checks conditions top to bottom:

    $  First true condition runs

Remaining conditions are skipped

> If none true → else runs

### 4️⃣ Numeric Comparison Operators
| Operator | Meaning |
|----------|----------|
| `-eq` | Equal |
| `-ne` | Not equal |
| `-gt` | Greater than |
| `-lt` | Less than |
| `-ge` | Greater than or equal |
| `-le` | Less than or equal |
### 5️⃣ String Comparison
🔹 Example
```Bash
#!/bin/bash

name="Giri"

if [ "$name" = "Giri" ]
then
    echo "Name matched"
fi
```
⬛ Important
Always use quotes " " with strings.
### 6️⃣ File Checking Conditions
🔹 Check File Exists
```Bash
#!/bin/bash

if [ -f "file.txt" ]
then
    echo "File exists"
else
    echo "File not found"
fi
```
🔹 Useful File Conditions
| Option | Meaning |
|--------|----------|
| `-f` | File exists (regular file) |
| `-d` | Directory exists |
| `-s` | File exists and is not empty |
### 7️⃣ AND / OR Condition
🔹 AND (Both must be true)
```Bash
#!/bin/bash

num=8

if [ $num -gt 5 ] && [ $num -lt 10 ]
then
    echo "Number is between 5 and 10"
fi
```
🔹 OR (Any one true)
```Bash
#!/bin/bash

num=3

if [ $num -lt 5 ] || [ $num -gt 10 ]
then
    echo "Condition satisfied"
fi
```
#### $  How AND works

Both conditions must return TRUE.

#### $  How OR works

At least one must return TRUE.
### 8️⃣ User Input + If Condition
```Bash
#!/bin/bash

echo "Enter a number:"
read num

if [ $num -gt 0 ]
then
    echo "Positive number"
else
    echo "Zero or Negative"
fi
```
### 9️⃣ Nested If (If inside If)
```Bash
#!/bin/bash

num=15

if [ $num -gt 10 ]
then
    if [ $num -lt 20 ]
    then
        echo "Number is between 10 and 20"
    fi
fi
```
## Bash If Condition - Reference Table

| Concept | Syntax | What It Does | Example |
|----------|--------|--------------|----------|
| Basic If | `if [ condition ]; then ... fi` | Runs code if condition is true | `if [ $a -eq 5 ]` |
| If-Else | `if [ condition ]; then ... else ... fi` | Runs one block if true, another if false | `if [ $a -gt 5 ]` |
| If-Elif-Else | `if ... elif ... else ... fi` | Multiple condition checking | `elif [ $a -lt 5 ]` |
| Numeric Equal | `-eq` | Equal to | `[ $a -eq 10 ]` |
| Not Equal | `-ne` | Not equal | `[ $a -ne 5 ]` |
| Greater Than | `-gt` | Greater than | `[ $a -gt 10 ]` |
| Less Than | `-lt` | Less than | `[ $a -lt 10 ]` |
| Greater or Equal | `-ge` | Greater than or equal | `[ $a -ge 10 ]` |
| Less or Equal | `-le` | Less than or equal | `[ $a -le 10 ]` |
| String Equal | `=` | Strings are equal | `[ "$a" = "hello" ]` |
| String Not Equal | `!=` | Strings not equal | `[ "$a" != "hi" ]` |
| Check File Exists | `-f filename` | True if file exists | `[ -f file.txt ]` |
| Check Directory | `-d dirname` | True if directory exists | `[ -d folder ]` |
| Check Empty File | `-s filename` | True if file not empty | `[ -s file.txt ]` |
| AND Condition | `&&` or `-a` | Both conditions must be true | `[ $a -gt 5 ] && [ $a -lt 10 ]` |
| OR Condition | `||` or `-o` | One condition must be true | `[ $a -lt 5 ] || [ $a -gt 10 ]` |
| NOT Condition | `!` | Reverses condition | `[ ! -f file.txt ]` |
| User Input Check | `read var` + if | Check user input value | `if [ $num -gt 0 ]` |
| Nested If | `if inside if` | Condition inside another condition | `if [ $a -gt 0 ]; then if [ $a -lt 10 ]` |

---
