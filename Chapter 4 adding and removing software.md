# [[Linux Basics for Hackers Getting Started with Networking, Scripting, and Security in Kali]]

### Package Management

This chapter focuses on adding and removing packages in Linux. Below are the essential commands and concepts.

### Searching for Packages

- You can use `apt-cache search <keyword>` to search for software packages. 
  - **Example**: Searching for "burp"

    ```console
    ┌─[chris@parrot]─[~]
    └──╼ $ apt-cache search burp
    arjun - HTTP parameter discovery suite
    burp - Simple cross-platform network BackUp and Restore Program
    burpsuite - platform for security testing of web applications
    proxify - Swiss Army knife Proxy tool for HTTP/HTTPS traffic capture, manipulation
    ┌─[chris@parrot]─[~]
    └──╼ $
    ```
  
  - This is a useful tool for finding applications.

### Installing and Removing Software

- **Installing Software**: The installation process is straightforward using the `apt-get` command.
- **Removing Software**: You can remove software using:
  - `sudo apt-get remove <package_name>`: Removes the package but keeps configuration files.
  - `sudo apt-get purge <package_name>`: Removes the package and all of its configuration files.

### Updating and Upgrading Packages

- **Updating Package Lists**: `sudo apt-get update`  
- **Upgrading Packages**: `sudo apt-get upgrade`

### Adding Repositories

- You can add repositories to your `sources.list` file to gain access to additional software repositories.
- **Accessing the sources list**:
  - Kali Linux: `sudo nano /etc/apt/sources.list`
  - Parrot OS: `sudo nano /etc/apt/sources.list.d/parrot.list`

### Example: Adding a Kali Repository

- I added the Kali repository line:
  
  ```console
  deb http://http.kali.org/kali kali-rolling main contrib non-free non-free-firmware
  ```

- **Note**: I had to remove it because Parrot OS is based on Arch, while Kali is based on Debian, which caused compatibility issues. I only commented out the line for future reference, so I remember not to attempt this again.

### Graphical Package Manager

- There is a graphical package manager called **Synaptic** that can be used for managing packages in a more visual way.

### Installing Software from GitHub

- To install software from GitHub:
  1. Use `git clone` to clone the repository.
  2. Follow the installation instructions provided in the GitHub repository.

---
