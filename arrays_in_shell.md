
## 1. What is an Array in Bash?

An array is a variable that can store multiple values in a single variable instead of storing only one value.
Example:
```bash
name="John"
```
Stores only one value.

#### But array:
```bash
names=("John" "Sam" "Ram")
```

Stores multiple values.

## 2. Creating Arrays

### Method 1 – Direct Initialization
```bash
#!/bin/bash

fruits=("Apple" "Banana" "Mango" "Orange")

echo ${fruits[0]}
echo ${fruits[1]}
echo ${fruits[2]}
echo ${fruits[3]}
```

#### Explanation
Array index starts from 0
```
${fruits[0]} :-> Apple
${fruits[1]} :-> Banana
```
### Method 2 – Assigning Values One by One
```Bash
#!/bin/bash

fruits[0]="Apple"
fruits[1]="Banana"
fruits[2]="Mango"

echo ${fruits[0]}
echo ${fruits[1]}
echo ${fruits[2]}
```
## 3. Print All Array Elements
```
Bash
#!/bin/bash

fruits=("Apple" "Banana" "Mango" "Orange")

echo ${fruits[@]}
```

#### Explanation

@ means all elements
This prints entire array

## 4. Length of Array
```Bash
#!/bin/bash

fruits=("Apple" "Banana" "Mango" "Orange")

echo ${#fruits[@]}
```
#### Output

`4`

#### Explanation
`#` is used to find length of array

## 5. Loop Through Array
```Bash
#!/bin/bash

fruits=("Apple" "Banana" "Mango" "Orange")

for fruit in ${fruits[@]}
do
    echo $fruit
done
```

#### Explanation
This loop prints each array element one by one.
## 6. Loop Using Index
```Bash
#!/bin/bash

fruits=("Apple" "Banana" "Mango")

for ((i=0; i<${#fruits[@]}; i++))
do
    echo ${fruits[$i]}
done
```

## 7. Add Element to Array
```Bash
#!/bin/bash

fruits=("Apple" "Banana")

fruits+=("Mango")
fruits+=("Orange")

echo ${fruits[@]}
```
## 8. Remove Element from Array
```Bash
#!/bin/bash

fruits=("Apple" "Banana" "Mango" "Orange")

unset fruits[1]

echo ${fruits[@]}
```
#### Explanation
Removes Banana

## 9. Get Array Indexes
```Bash
#!/bin/bash

fruits=("Apple" "Banana" "Mango")

echo ${!fruits[@]}
Output

0 1 2
10. Slice Array (Get Some Elements)
Bash
#!/bin/bash

fruits=("Apple" "Banana" "Mango" "Orange" "Grapes")

echo ${fruits[@]:1:3}
Explanation
Format:

${array[@]:start:length}
```
#### Output:

`Banana Mango Orange`

## 11. Replace Element in Array
```Bash
#!/bin/bash

fruits=("Apple" "Banana" "Mango")

fruits[1]="Orange"

echo ${fruits[@]}
```

## 12. Read Array from User Input
```Bash
#!/bin/bash

echo "Enter names:"
read -a names

echo "You entered:"
echo ${names[@]}
```

## 13. Read Array from File
If file list.txt contains:

host1
host2
host3
Script:
```Bash
#!/bin/bash

mapfile -t hosts < list.txt

echo ${hosts[@]}
```

## 14. Search Element in Array
```Bash
#!/bin/bash

fruits=("Apple" "Banana" "Mango")

search="Banana"

for fruit in ${fruits[@]}
do
    if [ "$fruit" == "$search" ]
    then
        echo "Found"
    fi
done
```

## 15. Useful Real-Life Example
Run `nmap` for list of targets stored in array:
```Bash
#!/bin/bash

targets=("192.168.1.1" "192.168.1.2" "192.168.1.3")

for ip in ${targets[@]}
do
    nmap $ip
done
```

# Most Common Bash Array Operations Summary

| Operation      | Command                  |
|----------------|--------------------------|
| Create array   | `arr=(a b c)`            |
| Access element | `${arr[0]}`             |
| All elements   | `${arr[@]}`             |
| Length         | `${#arr[@]}`            |
| Index list     | `${!arr[@]}`            |
| Add element    | `arr+=("new")`          |
| Remove element | `unset arr[1]`          |
| Slice          | `${arr[@]:1:2}`         |
| Loop           | `for i in ${arr[@]}`    |
| From file      | `mapfile -t arr < file` |
