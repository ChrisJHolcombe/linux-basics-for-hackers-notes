# [[Linux Basics for Hackers Getting Started with Networking, Scripting, and Security in Kali]]

### Viewing Storage Devices

You can first look in the `/dev` directory to see listed storage devices. The book mentions SATA hard drives, but if you have NVMe drives, the listings will differ.

**Example Output for `ls` in `/dev`:**
```bash
┌─[chris@parrot]─[/dev]
└──╼ $ ls
autofs           kmsg          nvme0n1p3  stdout  tty27  tty49  uhid         vcsa7
block            kvm           nvme0n1p4  tpm0    tty28  tty5   uinput       vcsu
bsg              log           nvme0n1p5  tpmrm0  tty29  tty50  urandom      vcsu1
btrfs-control    loop0         nvme0n1p6  tty     tty3   tty51  userfaultfd  vcsu2
...and so on...
```

For NVMe drives, partitions are listed as `nvme0n1p1`, `nvme0n1p2`, and so forth. If you have multiple operating systems like Windows, Ubuntu, and Parrot OS, each OS will have its own partition.

### Viewing Storage Devices Using `fdisk`

You can use the `fdisk -l` command to view all storage devices and their partitions.

### Character vs. Block Devices

When you use `ls -l` in `/dev`, you will see some devices prefixed with `c` or `b`:
- **Character Devices (`c`)**: Send data character by character, like a mouse or keyboard.
- **Block Devices (`b`)**: Send data in blocks, making them faster, used for hard drives and USB drives.

### Listing Block Devices

To list block devices, use:
```bash
lsblk
```

### Mounting and Unmounting Storage Devices

You can manually mount storage devices using:
```bash
mount <path_to_device> /mnt
```
- You can also mount to other locations, like `/media` for flash drives.

To unmount a storage device, use:
```bash
umount <path_to_device>
```
- Note: You cannot unmount a device that is in use. Attempting to do so will result in an error.

### Checking Mounted File Systems

You can get information on mounted file systems with:
```bash
df
```

**Example Output for `df`:**
```bash
┌─[chris@parrot]─[/dev]
└──╼ $ df
Filesystem      1K-blocks      Used  Available Use% Mounted on
udev             32707528         0   32707528   0% /dev
tmpfs             6554936      1788    6553148   1% /run
/dev/nvme0n1p6  115117056  48498636   65847060  43% /
```

### Checking and Repairing File System Errors

You can check for errors on a device using:
```bash
fsck <path_to_device>
```

To automatically repair problems:
```bash
fsck -p <path_to_device>
```
- Make sure the device is unmounted before running `fsck`.
