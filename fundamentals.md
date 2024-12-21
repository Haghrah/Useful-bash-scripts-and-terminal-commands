## Bash scripting fundamentals
Let’s start with simple bash scripting fundamentals.

### What is a Bash Script?
A bash script is a file containing a sequence of commands that the terminal can execute. It's useful for automating tasks in Linux.

### First Script

1. **Create a file:**

```
nano first_script.sh
```

2. **Add this content:**

```
#!/bin/bash
echo "Hello, World!"
```

* #!/bin/bash: Tells the system to use the bash interpreter.
* echo: Prints text to the terminal.

3. **Save and exit:** Press CTRL+O, ENTER, then CTRL+X.
4. **Make it executable:**

```
chmod +x first_script.sh
```

5. **Run the script:**

```
./first_script.sh
```

### Using Variables
Variables store data to reuse it later in the script.

**Example**

```
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

```
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

```
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

```
if [ condition1 ]; then
    # commands if condition1 is true
elif [ condition2 ]; then
    # commands if condition2 is true
else
    # commands if none of the conditions are true
fi
```

**Example:**

```
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

```
#!/bin/bash

for item in Apple Banana Cherry; do
    echo "I like $item."
done
```

**Example 2:** Iterating through numbers

```
#!/bin/bash

for number in {1..5}; do
    echo "Number: $number"
done
```

### The while Loop

The while loop runs as long as the condition is true.

**Example:** Counting down

```
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

```
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

```
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

```
#!/bin/bash

for number in {1..5}; do
    if [ $number -eq 3 ]; then
        echo "Skipping $number."
        continue
    fi
    echo "Number: $number"
done
```



































