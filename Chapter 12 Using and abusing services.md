# [[Linux Basics for Hackers Getting Started with Networking, Scripting, and Security in Kali]]

### Starting, Stopping, and Restarting Services

To manage services on Linux, use the following syntax:
```bash
service <service_name> start | stop | restart
```
- Replace `start | stop | restart` with the desired action.

On Parrot OS, the command is `systemctl`:
```bash
systemctl <service_name> start | stop | restart
```

### Apache Web Server

Apache is one of the most widely used web servers, powering about 60% of the world's websites. 

- The default HTML file for Apache's homepage is located at:
  ```bash
  /var/www/html/index.html
  ```
- To replace the default index file with your own HTML file, use the `mv` command:
  ```bash
  mv <path_to_your_index.html> /var/www/html/index.html
  ```

### SSH and Raspberry Pi


**Starting SSH on Parrot OS:**
```bash
systemctl start ssh
```

After setting up and flashing your Raspberry Pi, find its IP address:
```bash
ip addr show
```

**SSH into the Raspberry Pi:**
```bash
ssh <username>@<ip_address>
```

### Configuring and Using the Raspberry Pi Camera

To configure the camera on a Raspberry Pi:
```bash
sudo raspi-config
```
- Select "Enable Camera."
- Choose "Yes" to reboot.

**Taking Pictures with `raspistill`:**
```bash
raspistill -v <photo_name>.jpg
```

### Working with SQL Databases

SQL is vital for handling and exfiltrating data from databases. Here's how to manage MySQL services on Parrot OS:
```bash
systemctl start mysql
```
On other systems:
```bash
service mysql start
```

### Basic SQL Commands

1. **SELECT**: Retrieves data from a database.
2. **UNION**: Combines the results of two or more SELECT statements.
3. **INSERT**: Adds new data to a table.
4. **UPDATE**: Modifies existing data in a table.
5. **DELETE**: Deletes data from a table.

**Viewing All Users with Access:**
```sql
SELECT USER, host, password FROM mysql.user;
```
- Remember to terminate each SQL command with a semicolon `;`.

**Show All Databases:**
```sql
SHOW databases;
```

### Using the MySQL Database

- MySQL comes with three default databases:
  - **information_schema**: System database for metadata.
  - **performance_schema**: Used for performance tuning.
  - **mysql**: The database for user and privilege management.

**To use the MySQL database:**
```sql
USE mysql;
```

**Connecting to a Remote Database:**
```bash
mysql -u <username> -p <ip_address>
```

**Show All Tables in the Database:**
```sql
SHOW tables;
```

**Describe the Schema of a Table:**
```sql
DESCRIBE <table_name>;
```

**View Data from a Table:**
```sql
SELECT * FROM <table_name>;
```

### PostgreSQL with Metasploit

To install PostgreSQL:
```bash
apt-get install postgresql
```

**Starting PostgreSQL:**
```bash
systemctl start postgresql
```

**Starting Metasploit:**
```bash
msfconsole
```

Once in Metasploit (`msf>` prompt), initialize the database:
```bash
msfdb init
```

**Create a User in the PostgreSQL Database:**
- Switch to the `postgres` user:
  ```bash
  su postgres
  ```
- Create a new database user:
  ```bash
  createuser <username> -P
  ```
- Enter and confirm the password.

**Create a Database Owned by the User:**
```bash
createdb --owner=<username> <database_name>
```

**Exit `su` and Connect Metasploit to the Database:**
```bash
exit
db_connect <username>:<password>@127.0.0.1/<database_name>
```

**Check the Database Status:**
```bash
db_status
```

These commands will help you manage and configure services, set up SSH connections, work with SQL databases, and integrate PostgreSQL with Metasploit for penetration testing.
