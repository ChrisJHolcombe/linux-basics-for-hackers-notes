# [[Linux Basics for Hackers Getting Started with Networking, Scripting, and Security in Kali]]

### Environment Variables vs. Shell Variables

- **Environment Variables**: 
  - These are system-wide variables, available to all processes and denoted in **UPPER CASE**.
- **Shell Variables**: 
  - These are local to the shell session and denoted in **lowercase**.

### Viewing Environment Variables

- To see default environment variables, use:
  ```bash
  env
  ```
- To view **all** environment variables, use:
  ```bash
  set | more
  ```
  - Press **q** to quit the output.

### Filtering Variables

- You can filter specific variables using `grep`. For example:
  ```bash
  set | grep HISTSIZE
  ```

### Changing Variable Values Temporarily

- You can change the value of a variable for the current session. For example, let's modify `HISTSIZE`:

#### Example
- View the current `HISTSIZE` value:
  ```bash
  set | grep HISTSIZE
  ```
  - **Output**:
    ```bash
    HISTSIZE=1000
    ```

- To change the value temporarily:
  ```bash
  HISTSIZE=10
  ```

- Verify the change:
  ```bash
  set | grep HISTSIZE
  ```
  - **Output**:
    ```bash
    HISTSIZE=10
    ```

### Making Variable Changes Permanent

- To change variable values permanently, use the `export` command. **Proceed with caution**, as modifying these can affect your system.

#### Example
- To make `HISTSIZE` permanent:
  ```bash
  export HISTSIZE=10
  ```
- This sets the new default value to 10 for future sessions.

> **Note**: Changes made with `export` will persist until the shell is closed or the system is rebooted. To make changes persist across reboots, you need to modify the shell configuration file, such as `~/.bashrc` or `~/.zshrc`.
