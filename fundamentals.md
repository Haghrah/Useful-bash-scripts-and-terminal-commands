## Bash scripting fundamentals
Let’s start with simple bash scripting fundamentals.

### What is a Bash Script?
A bash script is a file containing a sequence of commands that the terminal can execute. It's useful for automating tasks in Linux.

### First Script

1. **Create a file:**

``` bash
nano first_script.sh
```

2. **Add this content:**

``` bash
#!/bin/bash
echo "Hello, World!"
```

* #!/bin/bash: Tells the system to use the bash interpreter.
* echo: Prints text to the terminal.

3. **Save and exit:** Press CTRL+O, ENTER, then CTRL+X.
4. **Make it executable:**

``` bash
chmod +x first_script.sh
```

5. **Run the script:**

``` bash
./first_script.sh
```

### Using Variables
Variables store data to reuse it later in the script.

**Example**

``` bash
#!/bin/bash

name="Ubuntu User"
echo "Hello, $name!"
```

* **Steps:**
  * Save this as variables_script.sh.
  * Make it executable: chmod +x variables_script.sh.
  * Run it: ./variables_script.sh.

### Reading User Input
Use the read command to get input from the user.

**Example**

``` bash
#!/bin/bash

echo "What is your name?"
read user_name
echo "Welcome, $user_name!"
```

* **Explanation:**
  * read user_name: Reads input and stores it in the user_name variable.

### Run Conditional Logic
Add conditions to your script.

**Example:**

``` bash
#!/bin/bash

echo "Enter a number:"
read number

if [ "$number" -gt 10 ]; then
    echo "The number is greater than 10."
else
    echo "The number is 10 or less."
fi
```

**Syntax of elif:**

``` bash
if [ condition1 ]; then
    # commands if condition1 is true
elif [ condition2 ]; then
    # commands if condition2 is true
else
    # commands if none of the conditions are true
fi
```

**Example:**

``` bash
#!/bin/bash

echo "Enter a number:"
read number

if [ "$number" -lt 0 ]; then
    echo "The number is negative."
elif [ "$number" -eq 0 ]; then
    echo "The number is zero."
else
    echo "The number is positive."
fi
```

* **Explanation:**

  * -lt: Less than.
  * -eq: Equal to.

### The for Loop

The for loop iterates over a list of items.

**Example 1:** Iterating through a list

``` bash
#!/bin/bash

for item in Apple Banana Cherry; do
    echo "I like $item."
done
```

**Example 2:** Iterating through numbers

``` bash
#!/bin/bash

for number in {1..5}; do
    echo "Number: $number"
done
```

### The while Loop

The while loop runs as long as the condition is true.

**Example:** Counting down

``` bash
#!/bin/bash

count=5
while [ $count -gt 0 ]; do
    echo "Countdown: $count"
    count=$((count - 1))  # Decrement count
done
```

### The until Loop

The until loop runs until the condition becomes true.

**Example:** Counting up

``` bash
#!/bin/bash

count=1
until [ $count -gt 5 ]; do
    echo "Count: $count"
    count=$((count + 1))  # Increment count
done
```

### Breaking out of Loops

Use break to exit a loop early.

**Example:** Break on condition

``` bash
#!/bin/bash

for number in {1..10}; do
    if [ $number -eq 5 ]; then
        echo "Breaking the loop at $number."
        break
    fi
    echo "Number: $number"
done
```

### Skipping Iterations

Use continue to skip the current iteration.

**Example:** Skip a number

``` bash
#!/bin/bash

for number in {1..5}; do
    if [ $number -eq 3 ]; then
        echo "Skipping $number."
        continue
    fi
    echo "Number: $number"
done
```

### Understanding $((expression))
* $((expression)) is used for arithmetic operations in bash.
* It evaluates the expression inside the parentheses and returns the result.

**Examples of Arithmetic**

1. Basic Arithmetic

``` bash
result=$((5 + 3))
echo $result  # Outputs: 8
```

2. Incrementing a Variable

``` bash
count=1
count=$((count + 1))  # count becomes 2
echo $count
```

3. Shorthand Increment
Bash supports a shorthand for incrementing and decrementing:

``` bash
count=1
((count++))  # count becomes 2
echo $count
```

4. Decrementing a Variable

``` bash
count=5
count=$((count - 1))  # count becomes 4
echo $count
```

**Why Use $(( ))?**

Bash treats everything as strings by default, so $(( )) explicitly tells it to perform arithmetic. Without this, bash won't understand operations like addition or multiplication.

### What Are Functions in Bash?

Functions in bash are blocks of reusable code that you can call multiple times.

**Defining and Using a Function**

1. Basic Syntax

``` bash
function_name() {
    # Commands
}
```

**Example:** A Simple Function

``` bash
#!/bin/bash

greet() {
    echo "Hello, $1!"
}

greet "Ubuntu User"
```

* $1 refers to the first argument passed to the function.

**Returning Values**

Functions return values using return or by echoing the value.

**Example:** Using return

``` bash
#!/bin/bash

add() {
    return $(( $1 + $2 ))
}

add 3 5
echo "Result: $?"  # $? gets the return value
```

**Example:** Using echo

``` bash
#!/bin/bash

multiply() {
    echo $(( $1 * $2 ))
}

result=$(multiply 4 5)
echo "Result: $result"
```

**Functions with Conditional Logic**

``` bash
#!/bin/bash

check_even() {
    if [ $(( $1 % 2 )) -eq 0 ]; then
        echo "$1 is even."
    else
        echo "$1 is odd."
    fi
}

check_even 4
check_even 7
```

**Why Use Functions?**

Functions make scripts modular, easier to read, and maintain.

### File Operations

**Creating and Writing to Files**

``` bash
#!/bin/bash

echo "This is a sample text." > sample.txt  # Overwrites content
echo "Adding more text." >> sample.txt     # Appends content
```

**Reading a File Line by Line**

``` bash
#!/bin/bash

while IFS= read -r line; do
    echo "Line: $line"
done < sample.txt
```

**Checking if a File Exists**

``` bash
#!/bin/bash

if [ -e sample.txt ]; then
    echo "File exists."
else
    echo "File does not exist."
fi
```

**Deleting a File**

``` bash
#!/bin/bash

rm sample.txt
echo "File deleted."
```

### Debugging Bash Scripts

**Enable Debugging Mode**

Add -x after the shebang or use set -x.

``` bash
#!/bin/bash -x

echo "Debugging this script"
```

OR

``` bash
#!/bin/bash

set -x
echo "Debugging this script"
set +x
```

* set -x: Starts debugging mode.
* set +x: Stops debugging mode.

**Check for Syntax Errors**

Run the script with bash -n:

``` bash
bash -n script.sh
```


**Trace Execution**

Use bash -x to trace commands:

``` bash
bash -x script.sh
```

### Example Script: File Management

Here’s a complete example combining file operations and conditions:

``` bash
#!/bin/bash

echo "Enter the filename:"
read filename

if [ -e "$filename" ]; then
    echo "$filename exists. Contents are:"
    cat "$filename"
else
    echo "$filename does not exist. Creating it..."
    echo "Hello, this is a new file." > "$filename"
    echo "$filename created."
fi
```

### Using External Commands

Bash can call system utilities or external commands. Here are a few common ones:

**Listing Files**

``` bash
#!/bin/bash
ls -l
```

**Searching for Text in Files**

``` bash
#!/bin/bash
grep "text_to_search" filename.txt
```

**Downloading Files**

``` bash
#!/bin/bash
wget https://example.com/file.txt
```

**Disk Usage**

``` bash
#!/bin/bash
df -h
```

## Text Processing with awk and sed

**Using awk**

awk is great for parsing and processing text.

**Example:** Extract the second column of a file

``` bash
#!/bin/bash
awk '{print $2}' filename.txt
```

**Using sed**

sed is useful for text substitution.

**Example:** Replace "old" with "new" in a file

``` bash
#!/bin/bash
sed -i 's/old/new/g' filename.txt
```

## Functions with File Operations

**Example:** Counting Words in a File

``` bash
#!/bin/bash

count_words() {
    wc -w "$1" | awk '{print $1}'
}

echo "Enter filename:"
read filename

if [ -e "$filename" ]; then
    echo "Word count: $(count_words $filename)"
else
    echo "File does not exist."
fi
```

## Loops with System Commands

**Example:** Renaming Files in a Directory

``` bash
#!/bin/bash

for file in *.txt; do
    mv "$file" "${file%.txt}_backup.txt"
done
```

### Debugging and Error Handling

**Error Handling with set**

``` bash
#!/bin/bash

set -e  # Exit on any error
set -u  # Treat unset variables as errors
set -o pipefail  # Exit if any command in a pipeline fails

echo "Starting script..."
ls nonexistent_file.txt
echo "This will not run if the above command fails."
```

**Logging Errors**

Redirect errors to a log file.

``` bash
#!/bin/bash

command 2>> error.log
```

### Automation with Cron Jobs

Cron jobs automate running bash scripts at specific times.

Edit the crontab file:

``` bash
crontab -e
```

Add a line to run a script every day at 5 PM:

``` bash
0 17 * * * /path/to/your_script.sh
```

### Advanced Example: Backup Script

``` bash
#!/bin/bash

SOURCE_DIR="/path/to/source"
BACKUP_DIR="/path/to/backup"
DATE=$(date +%Y%m%d)

if [ -d "$SOURCE_DIR" ]; then
    tar -czf "$BACKUP_DIR/backup_$DATE.tar.gz" "$SOURCE_DIR"
    echo "Backup completed: $BACKUP_DIR/backup_$DATE.tar.gz"
else
    echo "Source directory does not exist."
fi
```










































