# [[Linux Basics for Hackers Getting Started with Networking, Scripting, and Security in Kali]]

I won’t dive too deeply into this chapter since I already have a solid grasp of Python, but I’ll cover some essential highlights.

---

### Checking and Setting Up Python

Linux systems typically come with Python pre-installed. However, it’s always a good idea to confirm the installation:

**Check Python Version**:
```bash
python3 --version
```

**Ensure `pip` Is Installed**:
```bash
sudo apt install python3-pip
```

---

### Installing Third-Party Modules

You can use `pip` to install Python libraries, but sometimes, for downloading files directly, `wget` comes in handy.

---

### Setting Up a Virtual Environment

It’s a good practice to work in a virtual environment to keep your projects organized and avoid conflicts between dependencies.

1. **Create a Virtual Environment**:
   ```bash
   python -m venv myenv
   ```

2. **Activate the Virtual Environment**:
   ```bash
   source myenv/bin/activate
   ```

Once activated, you can use `pip` to install libraries specifically for your project, ensuring that everything stays separate from the system's global Python installation.

---

### Variables in Python

We all know about variables: they’re names used to store data values.

**Example**:
```python
myvariable = "Hello"
```

---

### Common Python Built-In Libraries

Here are some essential built-in libraries that I often use:

1. **os**: For interacting with the operating system (e.g., file handling, environment variables).
2. **sys**: Access system-specific parameters and functions.
3. **datetime**: Work with dates and times.
4. **random**: Generate random numbers or make random selections.
5. **subprocess**: Run and manage subprocesses.
6. **math**: Perform mathematical operations (e.g., trigonometry, logarithms).
7. **re**: Use regular expressions for text matching.
8. **json**: Work with JSON data.
9. **hashlib**: Perform hashing operations like SHA-256.
10. **argparse**: Parse command-line arguments.
11. **shutil**: Perform high-level file operations (e.g., copying and removing files).
12. **socket**: Work with network connections.

---

### Final Note

I’m wrapping things up here. If anyone comes across these notes, I highly recommend starting with a basic Python programming course before attempting to script in Linux. Having a foundational understanding of Python will make your Linux scripting experience far more enjoyable and efficient.
