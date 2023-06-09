# File Systems

## Types of file systems

- Windows:
  - Installation FS:
    - **FAT** (File Allocation Table);
    - **NTFS** (New Technology File System);
  - Native recognized FS:
    - FAT;
    - NTFS;
    - **ExFAT** (Extended File Allocation Table);
- Linux:
  - Installation FS:
    - **Ext** (Extended File System);
    - **ReiserFS**;
    - ...
  - Native recognized FS: almost all;

## Quota

- **Limit on disk usage (inodes or blocks)**;
- Can be set on a **per-user** or **per-group** basis;
- Max number of **files** is related to the limit on **inodes** (1 file = 1
  inode);
- Max **disk space** is related to the limit on **blocks**;
- Hard limit: user **cannot exceed** the limit;
- Soft limit: user can exceed the limit for a **certain amount of time** (grace
  period) before the hard limit is enforced;

### Quota Packages

| Package       | Description                   |
|---------------|-------------------------------|
| `quota`       | **user** and **group** quotas |
| `quota-tools` | **project** quotas            |

- Mount options:
  - `usrquota`: **user** quotas;
  - `grpquota`: **group** quotas;
  - `prjquota`: **project** quotas;
- Quota configuration files are located at partition root:
  - `/aquota.user`: **user** quotas;
  - `/aquota.group`: **group** quotas;
  - `/aquota.project`: **project** quotas;

### Getting started with quotas

1. Install `quota` and `quota-tools` packages:

- Debian/Ubuntu:

```console
sudo apt install quota quota-tools
```

- Arch/Manjaro:

```console
sudo pacman -S quota quota-tools
```

2. In `/etc/fstab`, add `usrquota` and/or `grpquota` to the partition you want
   to enable quotas:

```fstab
/dev/sda1 / ext4 defaults,usrquota,grpquota 0 1
```

3. Remount the partition:

```console
sudo mount -o remount /
```

4. Create quota files:

```console
sudo quotacheck -cug /
```

## Disk management

### Devices information

#### `blkid`

- List **block devices** connected to the system with:
  - **UUID**;
  - **File system type**;
  - **Label** if any;
  - **System name**.
- Filter by **file system type** with `-t` option:

```console
sudo blkid -t TYPE=ext4
```

## Extended access rights

### SUID & SGID

- **S**et **U**ser/**G**roup **ID**;
- **Special permissions** that can be set on **executable files**.

## Sticky bit

- **Special permission** that can be set on **directories**;
- **Prevents users** from **deleting** files they **do not own** in a
  **directory**;
- View sticky bit with `ls -l`. You should see a `t` at the end of the
  permissions:

```console
drwxrwxrwt  2 root root  4096 May  1 12:34 tmp
```

## Find files

### `locate`

- **Fast**;
- **Searches** in a **database** containing **all files** on the system;
- **Does not search** in **real time**, since the database needs to be updated
  first (`updatedb` command).

### `find`

- **Slower**;
- **Searches** in **real time**.
- Can **execute commands** on the **found files** with `-exec` option;
- 
```console
find /home –size +100M –exec rm '{ }' ';'
```

- **Can** search by:
  - **Name** (`-name`);
  - **Type**;
  - **Size** (`-size`, `-empty`);
  - **Permissions**;
  - **User** (`-user`);
  - **Group**;
  - **Date** (`-mtime`, `-daystart`);
  - **Content**;
  - And more....
  - 
```console
find / -name "file.txt"
```

## `which`

**Locates** the **default executable file** associated with a **command**.

## `whereis`

- **Locates** the executable file associated with a command;
- **Locates** the **manual page** associated with a command;
- **Locates** the **source code** associated with a command.
