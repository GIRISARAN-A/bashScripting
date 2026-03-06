<br></br>
<p align="center">
  <img src="images/shell_transparent.png" width="150">
</p>
<br></br>

##  What is Bash?
Bash (Bourne Again SHell) is the default command-line interpreter in most Linux systems like Ubuntu.
##### It allows users to:
• Run commands
• Automate tasks
• Manage files and processes
• Interact with the Linux kernel
• When you type commands like:

<p align="center">
  
```bash
ls
cd
mkdir
```
</p>

Bash reads and executes them.
A Bash Script is a file containing multiple commands that run automatically.

---
##  Creating Your First Bash Script

#### Step 1: Create a file
<p align="center">
  
```Bash
nano hello.sh
```
</p>
Opening file with nano text editor
#### Step 2: Add the following code
<p align="center">
  
```Bash
#!/bin/bash
echo "Hello World"
```
</p>
The first line ```#!/bin/bash``` is called a shebang. It tells Linux to use the Bash interpreter to run the script.
The echo command prints text to the terminal.

#### Step 3: Save and exit
`CTRL + X → Y → Enter`

#### Step 4: Make it executable
<p align="center">
  
```Bash
chmod +x hello.sh
```
</p>

#### Step 5: Run the script
<p align="center">
  
```Bash
./hello.sh
```
</p>

#### Output:
`Hello World`

> The echo command prints text or variable values to the terminal output.

#####  Understanding the Shebang
<p align="center">
  
```Bash
#!/bin/bash
```
</p>
This line tells Linux:
“Use the Bash interpreter to run this script.”
Without it, the system may not know which interpreter to use.

###  Variables in Bash

<p align="center">
  
```Bash
#!/bin/bash

name="Giri"
echo "My name is $name"
```
</p>
Important Rules:
No spaces around =
Use $ to access variable values

###  Taking User Input
<p align="center">
  
```Bash
#!/bin/bash

echo "Enter your name:"
read name
echo "Welcome $name"
```
</p>
read allows the user to enter data from the keyboard.

###  Conditional Statements (If-Else)
<p align="center">
  
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
</p>
---


| Operator | Meaning           |
|----------|-----------------|
| -eq      | equal           |
| -ne      | not equal       |
| -gt      | greater than    |
| -lt      | less than       |
| -ge      | greater or equal|
| -le      | less or equal   |

###  Loops in Bash
For Loop
<p align="center">
  
```Bash
#!/bin/bash

for i in 1 2 3 4 5
do
    echo "Number: $i"
done
```
</p>

  
While Loop
<p align="center">
  
```Bash
#!/bin/bash

count=1

while [ $count -le 5 ]
do
    echo "Count: $count"
    count=$((count+1))
done
```
</p>

$(( )) is used for arithmetic operations.

### 📎 Script Arguments
Run:
<p align="center">
  
```Bash
./myscript.sh Giri 11
```
</p>

Script:
<p align="center">
  
```Bash
#!/bin/bash

echo "Name: $1"
echo "Age: $2"
```
</p>

----

##### Special Variables:
| Variable | Meaning       |
|----------|---------------|
| $0       | Script name   |
| $1       | First argument|
| $2       | Second argument|
----
##  File Condition Checks
<p align="center">
  
```Bash
#!/bin/bash

if [ -f test.txt ]
then
    echo "File exists"
else
    echo "File not found"
fi
```
</p>

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

###  How Bash Executes a Script
• You run ./script.sh
• The Linux kernel loads /bin/bash
• Bash reads the script line by line
• Each command is executed
• Output is displayed in terminal

#### Conclusion
##### Bash scripting is powerful for:
• System administration
• Automation
• Cybersecurity tasks
• DevOps workflows
• Linux system management
Mastering Bash helps you understand how Linux interacts with users and the kernel.
