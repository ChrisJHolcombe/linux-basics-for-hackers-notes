# [[Linux Basics for Hackers Getting Started with Networking, Scripting, and Security in Kali]]

### Concepts to Be Clarified

- **Binaries**: This term refers to files that can be executed, similar to executable packages in Windows. Binaries are stored in the `/usr/bin` directory.
- **Case Sensitive**: Unlike Windows, Linux is case sensitive. This means that `File.txt` and `file.txt` are treated as two different files.
- **Directory**: Equivalent to a folder in Windows. It is used to organize files in the Linux file system.
- **Home**: The default directory for a user. It is similar to the "Users" folder in Windows.
- **Kali**: A popular penetration testing operating system. Note: I am using Parrot OS, which serves a similar purpose.
- **Root**: The superuser account that has administrative access to everything on the system. Root can perform any action, unrestricted by permissions.
- **Script**: A series of commands that are executed in an interpretive environment. The interpreter reads and executes each line of the script as source code.
- **Shell**: The environment and interpreter for running commands in Linux. Examples include Bash, Zsh, and Fish.
- **Terminal**: The command line interface used to interact with the Linux shell. It is where you input commands.

---

##### The Linux file system

![[Pasted image 20241108085359.png]]


---

### Important Directories in Linux

- **/root**: The home directory of the root user.
- **/etc**: This directory generally contains Linux configuration files.
- **/home**: The home directory for regular users. Each user has a subdirectory within `/home`.
- **/media**: The location where CDs, USB devices, and other removable media are typically mounted.
- **/bin**: Contains essential application binaries (executable files).
- **/lib**: Stores libraries used by programs, similar to Windows DLL files.

### Useful Commands

- **pwd**: Prints the current working directory.
- **whoami**: Displays the username of the current user.
- **cd**: Changes the current directory.
- **cd..**: Moves back one directory.
- **cd .. ..**: Moves back two directories.
- **cd .. .. ..**: Moves back three directories.
- **ls**: Lists all files in the current directory.
- **ls -l**: Lists all files with detailed information.
- **ls -a**: Lists all files, including hidden ones.
- **man**: Displays the manual for a given tool. Usage: `man <tool_name>`.
- **locate**: Searches for files on your system. Usage: `locate <tool_or_file_name>`.
- **whereis**: Finds the binary, source, and manual page files for a command. Usage: `whereis <tool_or_file_name>`.
- **which**: Returns the PATH of a binary. Usage: `which <tool_or_program_name>`.
- **find**: A powerful tool to search for files. Usage: `find <starting_directory> -type <file_type> -name <file_name>`.
  - Use the wildcard `*` if you are unsure of the file extension.

### Process Management and Filtering

- **ps aux**: Lists all processes currently running on the system.
- **grep**: Filters output to search for specific keywords. Useful in conjunction with other commands, like `ps aux | grep <process_name>`.

### File Management with `cat`

- **cat > `<filename>`**: Creates or overwrites a file. Remember to use `Control + C` to save and exit after adding information.
- **cat >> `<filename>`**: Appends information to an existing file.
- **cat `<filename>`**: Displays the contents of a file in the terminal.

### Creating and Managing Files and Directories

- **touch `<filename>`**: Creates a new file if it does not already exist.
- **mkdir `<directory_name>`**: Creates a new directory.
- **cp `<source_file>` `<destination>`**: Copies a file to a specified destination.
- **mv `<current_file_name>` `<new_file_name>`**: Renames a file or moves it to a new location.
- **rm `<filename>`**: Removes a file.
- **rmdir `<directory_name>`**: Removes an empty directory.

### Common Errors and Solutions

- **Error**: `/var/lib/plocate/plocate.db: No such file or directory`
  - **Cause**: The database needs to be updated.
  - **Solution**: Use `sudo updatedb.plocate` to update the database.
- **Creating Files with `cat`**: In Parrot OS, you must be the root user to create files using `cat > <filename>`. After entering information, press `Control + C` to save.


