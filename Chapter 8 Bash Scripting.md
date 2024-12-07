# [[Linux Basics for Hackers Getting Started with Networking, Scripting, and Security in Kali]]

### Writing Bash Scripts

When writing bash scripts, you need to specify which shell to use. This is done using the **shebang**, which consists of an octothorpe (#) followed by an exclamation mark (!) and the path to the shell, such as `/bin/bash`.

**Complete Shebang Command:**
```bash
#! /bin/bash
```

The `echo` statement in bash functions similarly to the `print` statement in Python.

### Example: Creating a Simple Bash Script

1. Open a new file in the `nano` editor:
   ```bash
   nano Hackersarise.sh
   ```
2. Add the shebang and an echo statement:
   ```bash
   #! /bin/bash
   echo "Hello, Hackers arise!"
   ```
3. Save the file with a `.sh` extension. To make it executable, use:
   ```bash
   chmod +x Hackersarise.sh
   ```
4. Run the script with:
   ```bash
   sudo ./Hackersarise.sh
   ```

### Taking User Input in Bash

Taking user input in bash is straightforward, but naming conventions differ from other programming languages like Python. Use the `read` command to capture input. Comments in bash scripts start with `#`.

**Example Bash Script:**
```bash
#! /bin/bash

# Ask the user their name
echo "Hello, What is your name?"

# Saving the user's input to variable 'name'
read name

echo "What chapter of Linux Basics for Hackers are you on?"

read chapter

# Calling the 'name' and 'chapter' variables
echo "Hello, $name! I am glad to see you are on chapter $chapter of your learning journey."
```

### Nmap Port Scan Script

You can use bash scripts to automate tasks like nmap port scans. This is similar to running subprocesses in Python.

**Example Bash Script for Nmap Scan:**
```bash
#! /bin/bash

# Get target domain
echo "What is the domain you wish to target?"
read target

echo "Enter the port number you wish to scan for"
read port

# Calling nmap scan on the target and writing output to a file
nmap -sV $target -p $port >/dev/null -oG scan_with_nmap

# Filtering nmap output for open ports and writing to another file
cat scan_with_nmap | grep open > scan_with_nmap_2

# Display the final output to see open ports
cat scan_with_nmap_2
```

### Commonly Used Bash Commands

Here is a list of commonly used bash commands:

- `ls`: Lists files and directories.
- `cd`: Changes the directory.
- `pwd`: Prints the current working directory.
- `touch`: Creates an empty file.
- `mkdir`: Creates a new directory.
- `rm`: Removes files or directories.
- `cp`: Copies files or directories.
- `mv`: Moves or renames files or directories.
- `echo`: Prints text to the terminal.
- `cat`: Concatenates and displays the content of files.
- `grep`: Searches for patterns in files.
- `chmod`: Changes file permissions.
- `chown`: Changes file ownership.
- `find`: Searches for files and directories.
- `nmap`: Network exploration tool and security/port scanner.
- `top`: Displays Linux tasks.
- `kill`: Terminates processes by PID.
- `ps`: Displays information about active processes.
- `df`: Reports file system disk space usage.
- `du`: Estimates file space usage.
- `tar`: Archives files.
- `sudo`: Executes a command as another user (typically root).

For a more comprehensive list of bash built-in commands, you can visit: [GNU Bash Built-ins](https://www.gnu.org/software/bash/manual/html_node/Bash-Builtins.html)