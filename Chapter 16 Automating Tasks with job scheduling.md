# [[Linux Basics for Hackers Getting Started with Networking, Scripting, and Security in Kali]]

### Automating Tasks with Cron Jobs

One of the great things about Linux is the ability to automate tasks using **cron jobs**. You can schedule tasks to run at specific intervals by editing the `crontab`. Here's how I would explain it:

---

### Setting Up a Cron Job in Crontab

First, to edit your crontab, use:
```bash
crontab -e
```
This opens your crontab file, where you can add, edit, or remove scheduled tasks. 

Each line in your crontab file follows this format:
```plaintext
minute hour day month day_of_week command
```
For example, to run a task every day at 2:30 AM:
```plaintext
30 2 * * * /path/to/your/script.sh
```

---

### Sample Crontab Implementation for Backing Up Data to a NAS Server

Here's a real-world example of how I might set up a backup to my locally hosted NAS server using Open Media Server. Suppose I want to back up my `/home/user/Documents` directory every night at 1:00 AM:

1. **Edit the Crontab**:
   ```bash
   crontab -e
   ```

2. **Add the Backup Task**:
   ```plaintext
   0 1 * * * rsync -av --delete /home/user/Documents/ /mnt/nas-backup/Documents/
   ```
   - **Explanation**:
     - `0 1 * * *`: Runs the command every day at 1:00 AM.
     - `rsync -av --delete`: Uses `rsync` to back up data, where `-a` stands for archive mode and `-v` for verbose output. The `--delete` option ensures that deleted files in the source are also removed from the backup.
     - `/home/user/Documents/`: The directory to back up.
     - `/mnt/nas-backup/Documents/`: The mount point of the NAS server.

---

### Crontab Shortcuts

Crontab also has some shortcuts to simplify scheduling:
- `@reboot`: Runs the command once at startup.
- `@daily`: Runs the command once a day.
- `@hourly`: Runs the command every hour.
- `@weekly`: Runs the command once a week.
- `@monthly`: Runs the command once a month.

**Example Using Shortcuts**:
```plaintext
@daily /path/to/daily_task.sh
@reboot /path/to/startup_task.sh
```

---

### Running Jobs at Startup with `rc`

You can use `rc` to run specific jobs or scripts when the system starts.

**Adding a Service to Run at Startup**:
```bash
update-rc.d <service_or_script_name> <remove | defaults | disable | enable>
```
- **remove**: Removes the service from startup.
- **defaults**: Adds the service with default settings.
- **disable**: Disables the service from starting at boot.
- **enable**: Enables the service to run at boot.

---

### Linux Run Levels

Understanding run levels helps you know what state the system is in:

- **0**: Halt the system.
- **1**: Single-user mode (minimal, often used for maintenance).
- **2-5**: Multiuser modes with different configurations.
- **6**: Reboot the system.

---

### Using `rcconf` for a GUI Version

If you prefer a graphical interface to manage startup services, use `rcconf`:

1. **Install `rcconf`**:
   ```bash
   sudo apt install rcconf
   ```

2. **Run `rcconf`**:
   ```bash
   sudo rcconf
   ```
This will bring up a simple interface allowing you to enable or disable services at startup.

