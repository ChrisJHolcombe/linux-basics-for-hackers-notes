# [[Linux Basics for Hackers Getting Started with Networking, Scripting, and Security in Kali]]

### Viewing Running Processes

To view all running processes on Linux, use `ps`. This command displays a list of processes along with their PIDs (Process IDs), crucial for process management.

To see all processes running for all users, use `ps aux`. This command provides detailed info about all active processes, including user, PID, CPU and memory usage, and command.

#### Example Terminal Output for `ps aux`
```bash
chris@parrot ~$
ps aux

USER         PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root           1  0.0  0.0  21732 13124 ?        Ss   09:19   0:00 /sbin/init splash
root           2  0.0  0.0      0     0 ?        S    09:19   0:00 [kthreadd]
root           3  0.0  0.0      0     0 ?        S    09:19   0:00 [pool_workqueue_release]
root           4  0.0  0.0      0     0 ?        I<   09:19   0:00 [kworker/R-rcu_gp]
root           5  0.0  0.0      0     0 ?        I<   09:19   0:00 [kworker/R-sync_wq]
root           6  0.0  0.0      0     0 ?        I<   09:19   0:00 [kworker/R-slub_flushwq]
root           7  0.0  0.0      0     0 ?        I<   09:19   0:00 [kworker/R-netns]
```

### Filtering Processes

To filter and search for specific processes using a keyword, use:
```bash
ps aux | grep <keyword>
```
#### Example Usage
```bash
ps aux | grep python
```
This will show you all running processes that contain the string "python" in their command line.

### Viewing Resource Usage

The `top` command displays running processes in real-time, sorted by resource usage. This is helpful for identifying which processes consume the most CPU and memory.

#### Example Output
```bash
top

chris@parrot ~$
top

tasks:  1 total,   0 running,   1 sleeping,   0 stopped,   0 zombie
%Cpu(s):  0.0 us, 99.9 sy,   0.1 ni,   0.0 id,   0.0 wa
KiB Mem :   16777216 total,       13120 used,    15500112 free
KiB Swap: 209715200 total,        52428 used, 203061568 free.
```

### Managing Process Priorities

You can start a process with a specified priority using the `nice` command.
```bash
nice -n -10 python3 my_script.py
```
Alternatively, use the `renice` command to change the priority of an existing process.
```bash
renice -10 1234
```
Replace `1234` with the actual PID of the process you want to modify.

### Killing Processes

Use the `kill` command to terminate a running process.
```bash
kill -15 1234
```
You can use other signals like `-9` (SIGKILL) or `-2` (SIGINT) to force-kill or interrupt the process, respectively.

#### Common Kill Signals
| Signal | Description |
| --- | --- |
| 1 (SIGHUP) | Hangup. Stops and restarts the process with the same PID. |
| 2 (SIGINT) | Interrupt. Weak but often sufficient to stop a process. |
| 3 (SIGQUIT) | Quits and generates a core dump in the working directory. |
| 15 (SIGTERM) | Default termination. Gracefully stops the process. |
| 9 (SIGKILL) | Force kill. Stops the process immediately. |

### Running Processes in the Background

To run a command or script in the background, append `&` at the end.
```bash
python3 my_script.py &
```
Check the status of your background job using:
```bash
chris@parrot ~$
jobs

[1]  Running         python3 my_script.py
```

### Scheduling Processes

Here's how to schedule a script to run at a specific time using `at`:
```bash
at -f /path/to/my_script.sh
> Ctrl + D
```
This schedules `my_script.sh` to run at the next scheduled time.
