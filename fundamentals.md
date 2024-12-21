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












