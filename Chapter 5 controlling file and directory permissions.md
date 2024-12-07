# [[Linux Basics for Hackers Getting Started with Networking, Scripting, and Security in Kali]]

### Granting Permissions

Every user and file should have specific permissions to control access and functionality. The different permissions are:

- **Write Permission**: Allows viewing and editing access to a file.
- **Execute Permission**: Allows executing the file but not necessarily viewing or editing it.

### Granting Ownership

- **chown**: The command used to change ownership of a file to a specific user.
  - **Syntax**: `chown <user> <file>`
  - Example: This command changes the ownership of the file to the specified user.

- **chgrp**: Used to change the group ownership of a file.
  - **Syntax**: `chgrp <group_name> <file>`

### Checking Permissions

- Use the `ls -l` command to check the permissions of a file.

### Changing Permissions with Octal Notation

- **Octal Notations**: Permissions in Linux are often represented using octal notation. Each permission (read, write, execute) is assigned a numerical value:
  - **Read (r)**: 4
  - **Write (w)**: 2
  - **Execute (x)**: 1
- The permissions are represented by three digits (owner, group, others). For example:
  - **chmod 755 <file>**:
    - **7**: Owner has read (4) + write (2) + execute (1) = 7
    - **5**: Group has read (4) + execute (1) = 5
    - **5**: Others have read (4) + execute (1) = 5
  - **chmod 644 <file>**:
    - **6**: Owner has read (4) + write (2) = 6
    - **4**: Group has read (4) = 4
    - **4**: Others have read (4) = 4

### Default Permissions with umask

- **umask**: Sets the default permissions by specifying which permissions to remove.
- The umask value is a 3-digit number that corresponds to the three permission digits. It is subtracted from the default permissions to produce the final permission status.

### Changing umask Variables

- The umask variables can be adjusted in the `.profile` file located in `/home/username/.profile`.

### Temporary Root Permissions with SUID and SGID

- **SUID (Set User ID)**: Grants temporary root permissions. To set SUID, add the number **4** before the permission digits.
  - **Syntax**: `chmod 4<3-digit_permission> <filename>`
- **SGID (Set Group ID)**: Grants permissions to a group. Add the number **2** before the permission digits.

### Privilege Escalation

- Exploiting the SUID bit can lead to privilege escalation if permissions are incorrectly set. You can check for files with SUID permissions:
  - **Command**: `find / -user root -perm -4000`
  - This command searches for files with root permissions set with SUID.
