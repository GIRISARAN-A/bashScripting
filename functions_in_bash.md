
# Bash Functions 


# 1. What is a Function in Bash?

A function is a **named block of commands** that can be reused multiple times in a script.

Instead of writing the same logic again and again, we place it inside a function and call it whenever required.

This makes scripts:
- Reusablea
- Cleaner

## Simple Example
```bash
#!/bin/bash

hello() {
    echo "Hello World"
}

hello
```

### Output
```bash
Hello World
```

### Explanation
- `hello` → function name
- `()` → tells Bash this is a function
- `{}` → body of the function
- `hello` → calling the function

---

# 2. Why Functions are Important

Without functions:
```bash
echo "Scanning target..."
nmap 192.168.1.1

echo "Scanning target..."
nmap 192.168.1.2
```

With functions:
```bash
scan() {
    echo "Scanning target..."
    nmap $1
}

scan 192.168.1.1
scan 192.168.1.2
```

# 3. Different Ways to Create Functions

## Method 1 – Standard
```bash
greet() {
    echo "Welcome"
}
```

## Method 2 – Using `function`
```bash
function greet {
    echo "Welcome"
}
```

Both are valid.

Best practice:
```bash
greet() {
}
```

---

# 4. Function Calling

A function runs only when called.

```bash
greet() {
    echo "Hi"
}

greet
```

You can call it multiple times:

```bash
greet
greet
greet
```

# 5. Function Parameters (Arguments)

Functions can receive inputs.

```bash
show_name() {
    echo "Name: $1"
}

show_name John
```

### Output
```bash
Name: John
```

---

## Positional Parameters
| Variable | Meaning |
|---|---|
| `$1` | First argument |
| `$2` | Second argument |
| `$3` | Third argument |
| `$@` | All arguments |
| `$#` | Number of arguments |

---

# 6. Multiple Parameters

```bash
user_details() {
    echo "Name: $1"
    echo "Age: $2"
    echo "Role: $3"
}

user_details John 21 Student
```

---

# 7. All Arguments Using `$@`

```bash
show_all() {
    echo $@
}

show_all apple banana mango
```

### Output
```bash
apple banana mango
```

---

# 8. Number of Arguments Using `$#`

```bash
count_args() {
    echo "Total args: $#"
}

count_args one two three
```

### Output
```bash
Total args: 3
```

# 9. Return Values in Bash Functions

Bash does not return strings directly like Python.

Usually we use:
```bash
echo
```

```bash
add() {
    echo $(( $1 + $2 ))
}

sum=$(add 10 20)
echo $sum
```

---

# 10. `return` Keyword

`return` is mainly for **exit status codes**.

```bash
is_even() {
    if (( $1 % 2 == 0 ))
    then
        return 0
    else
        return 1
    fi
}

is_even 4
echo $?
```

### Output
```bash
0
```
After any command runs, Bash stores whether it **succeeded or failed**.

You can check that result using:
```shell
echo $?
```

# 11. Exit Status Meaning

| Code | Meaning |
|---|---|
| `0` | Success |
| `1` | Failure |
| Other | Custom error |

This is heavily used in Linux automation.

---

# 12. Local Variables

```bash
demo() {
    local name="Sam"
    echo $name
}

demo
```

## Why local is important
Without local:
```bash
name="Global"

demo() {
    name="Changed"
}
```

Global variable changes accidentally.

So use:
```bash
local
```

for safe scripting.


# 13. Global Variables

Variables created outside function are global.

```bash
target="192.168.1.1"

scan() {
    echo $target
}
```

# 14. Function Inside Function Flow

```bash
prepare() {
    echo "Preparing..."
}

scan() {
    prepare
    echo "Scanning..."
}

scan
```

Useful in:
- Recon tools
- File scanners
- Menu systems

# 15. Recursive Functions

A function calling itself.

```bash
countdown() {
    if [ $1 -eq 0 ]
    then
        return
    fi

    echo $1
    countdown $(( $1 - 1 ))
}

countdown 5
```

---

# 16. Default Values in Functions

```bash
greet() {
    local name=${1:-Guest}
    echo "Hello $name"
}

greet
```

### Output
```bash
Hello Guest
```

If no argument is passed, default value is used.

# 17. Function Output Redirection

```bash
log_message() {
    echo "Scan started"
}

log_message > log.txt
```

Stores function output in file.

# 18. Exporting Functions

Useful in subshells.

```bash
myfunc() {
    echo "Hello"
}

export -f myfunc
```

Used in advanced Bash scripting.


# 19. Debugging Functions

```bash
set -x
```

Example:
```bash
#!/bin/bash
set -x

demo() {
    echo "Debugging"
}

demo
```

Shows each executed command.

---

# 20. Real-Life Cybersecurity Example

```bash
#!/bin/bash

scan_target() {
    local ip=$1
    echo "Scanning $ip"
    nmap $ip
}

scan_target 192.168.1.1
```

---

# 21. Password Strength Checker Function

```bash
check_password() {
    local pass=$1
    if [ ${#pass} -ge 8 ]
    then
        echo "Strong"
    else
        echo "Weak"
    fi
}

check_password "mypassword123"
```

# 22. Reading Hosts File with Function

```bash
read_hosts() {
    while read host
    do
        echo "Checking $host"
    done < hosts.txt
}

read_hosts
```

# 23. Common Mistakes

## Wrong
```bash
hello ()
{
echo hi
}
```

## Better
```bash
hello() {
    echo "hi"
}
```

---

# Most Common Bash Function Operations Summary

| Operation | Command |
|---|---|
| Create function | `name(){}` |
| Call function | `name` |
| First arg | `$1` |
| All args | `$@` |
| Arg count | `$#` |
| Return code | `return 0` |
| Output capture | `x=$(func)` |
| Local variable | `local x=1` |
| Export function | `export -f func` |

