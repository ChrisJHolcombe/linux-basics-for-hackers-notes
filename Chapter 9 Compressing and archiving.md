# [[Linux Basics for Hackers Getting Started with Networking, Scripting, and Security in Kali]]

### Archiving Files with `tar`

The `tar` command stands for **tape archive**, paying homage to the early days of computing when data was stored on tape drives.

To archive a list of files together using `tar`:
```bash
tar -cvf <name_of_file>.tar <file1> <file2> <file3>
```
- You can list as many files as needed, separating each with a space.
- The first argument `<name_of_file>.tar` is the name of your tar file.

### Viewing the Contents of a Tar File

To display the contents of a tar file without extracting it, use:
```bash
tar -tvf <filename.tar>
```

### Compressing Tar Archives

Once you have a tar archive, you can compress it using several options:

1. **gzip**: Produces files with `.tar.gz` or `.tgz` extensions.
   ```bash
   gzip <filename>.*
   ```
   - The `*` wildcard is used to ensure all file types within the tar archive are compressed.

2. **bzip2**: Produces files with a `.tar.bz2` extension.
   ```bash
   bunzip2 <filename>.*
   ```

3. **compress**: Creates files with a `.tar.gz` extension but is less commonly used due to larger file sizes.
   ```bash
   compress <filename>.*
   ```

### Creating a System Image with `dd`

The `dd` command can be used to create a bit-by-bit copy of a system. This can be useful for:
- **Hackers**: To copy an entire target system, including deleted files.
- **Investigators**: To create forensic images of a target system for analysis and artifact recovery.

**Sample Syntax for `dd`:**
```bash
dd if=<input_file> of=<output_file>
```
- `if=` specifies the input file or device (e.g., `/dev/sda`).
- `of=` specifies the output file or device (e.g., `/path/to/backup.img`).

Using `dd` can recover even deleted data, making it a powerful tool for both offensive and defensive purposes in cybersecurity.
