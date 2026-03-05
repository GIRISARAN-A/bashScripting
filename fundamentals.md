<br></br>
<p align="center">
  <img src="images/shell_transparent.png" width="150">
</p>
<br></br>

## 📌 What is Bash?
Bash (Bourne Again SHell) is the default command-line interpreter in most Linux systems like Ubuntu.
##### It allows users to:
• Run commands
• Automate tasks
• Manage files and processes
• Interact with the Linux kernel
• When you type commands like:
```bash
ls
cd
mkdir
```
Bash reads and executes them.
A Bash Script is a file containing multiple commands that run automatically.
---
📝 Creating Your First Bash Script
#### Step 1: Create a file
```Bash
nano hello.sh
```
Opening file with nano text editor
#### Step 2: Add the following code
```Bash
#!/bin/bash
echo "Hello World"
```
The first line ```#!/bin/bash``` is called a shebang. It tells Linux to use the Bash interpreter to run the script.
The echo command prints text to the terminal.
#### Step 3: Save and exit
`CTRL + X → Y → Enter`

#### Step 4: Make it executable
```Bash
chmod +x hello.sh
```
#### Step 5: Run the script
```Bash
./hello.sh
```
#### Output:
`Hello World`

> The echo command prints text or variable values to the terminal output.

🔍 Understanding the Shebang
```Bash
#!/bin/bash
```
This line tells Linux:
“Use the Bash interpreter to run this script.”
Without it, the system may not know which interpreter to use.

### 📦 Variables in Bash
```Bash
#!/bin/bash

name="Giri"
echo "My name is $name"
```
Important Rules:
No spaces around =
Use $ to access variable values

### 📥 Taking User Input
```Bash
#!/bin/bash

echo "Enter your name:"
read name
echo "Welcome $name"
```
read allows the user to enter data from the keyboard.

### 🔀 Conditional Statements (If-Else)
```Bash
#!/bin/bash

echo "Enter a number:"
read num

if [ $num -gt 10 ]
then
    echo "Number is greater than 10"
else
    echo "Number is 10 or less"
fi
```
---


| Operator | Meaning           |
|----------|-----------------|
| -eq      | equal           |
| -ne      | not equal       |
| -gt      | greater than    |
| -lt      | less than       |
| -ge      | greater or equal|
| -le      | less or equal   |

### 🔁 Loops in Bash
For Loop
```Bash
#!/bin/bash

for i in 1 2 3 4 5
do
    echo "Number: $i"
done
```
While Loop
```Bash
#!/bin/bash

count=1

while [ $count -le 5 ]
do
    echo "Count: $count"
    count=$((count+1))
done
```
$(( )) is used for arithmetic operations.

### 📎 Script Arguments
Run:
```Bash
./myscript.sh Giri 11
```
Script:
```Bash
#!/bin/bash

echo "Name: $1"
echo "Age: $2"
```
----
##### Special Variables:
| Variable | Meaning       |
|----------|---------------|
| $0       | Script name   |
| $1       | First argument|
| $2       | Second argument|
----
## 📁 File Condition Checks
```Bash
#!/bin/bash

if [ -f test.txt ]
then
    echo "File exists"
else
    echo "File not found"
fi
```
---
Useful File Tests
| Option | Meaning       |
|--------|---------------|
| -f     | Regular file  |
| -d     | Directory     |
| -r     | Readable      |
| -w     | Writable      |
| -x     | Executable    |
---
### 🧠 How Bash Executes a Script
• You run ./script.sh
• The Linux kernel loads /bin/bash
• Bash reads the script line by line
• Each command is executed
• Output is displayed in terminal

#### 📚 Conclusion
##### Bash scripting is powerful for:
• System administration
• Automation
• Cybersecurity tasks
• DevOps workflows
• Linux system management
Mastering Bash helps you understand how Linux interacts with users and the kernel.
