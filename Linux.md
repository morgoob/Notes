# Linux

# Useful Terms

---

- **Kernel:** The core component of the operating system that manages hardware resources and provides essential services to software. (ex. Linux Kernel)
- **Distribution:** A complete Linux operating system package that includes the Linux kernel, system utilities, libraries, and often additional software, bundled together for specific purposes or user preferences. (ex. Ubuntu, RHEL, Fedora, Gentoo)
- **Boot Loader:** Software responsible for loading the operating system into memory during startup; it allows you to choose between multiple operating systems if installed. (ex. GRUB and ISOLINUX)
- **Service (daemon):** A background program or process that runs independently, providing specific functions or capabilities to the operating system or applications. (ex. httpd, nfsd, ntpd, ftpd, and named)
- **Filesystem:** A hierarchical structure used to organize and store files and directories on storage devices, allowing for efficient data access and management. (ex. ext3, ext4, FAT, XFS, NTFS, and Btrfs)
- **Partition**: distinct and logically separated portion of a storage device, such as a hard drive or SSD (Solid-State Drive). Partitions are created to divide the storage space of a device into isolated sections, each of which can be independently managed and used for specific purposes.
- **X Window System:** A graphics system for Unix-like operating systems that provides the framework for creating graphical user interfaces (GUIs) and managing windowed applications.
- **Desktop Environment:** A complete graphical user interface (GUI) package that includes a window manager, file manager, and other utilities, providing a user-friendly desktop experience. (ex. GNOME, KDE, Xfce, and Fluxbox)
- **Command Line:** A text-based interface where users input commands to interact with the operating system and execute tasks, typically used for system administration and scripting.
- **Shell:** A command-line interface (CLI) program that interprets and executes user commands, enabling users to interact with the operating system by typing text-based commands and receiving text-based responses. (ex. bash, tcsh, and zsh)
- **********Socket:********** A software abstraction that allows programs to communicate over a network, either locally or across the internet. It provides a mechanism for processes running on different devices to exchange data
- **GNOME**: A user-friendly and highly customizable desktop environment (GUI) for Unix-like operating systems, known for its modern design and focus on simplicity and productivity.
- ************GRUB (************"GNU GRand Unified Bootloader,"): A widely used boot loader software that manages the boot process of a computer, allowing users to select and load different operating systems or kernels at startup.

# Command Line Interface

---

**The command line is the same for all Linux distributions** 

A **terminal emulator** emulates a stand-alone terminal within a window on the desktop (it behaves the same as if you were logging into a machine at a pure text terminal with no running GUI)

### TTY vs. Terminal Emulator

---

- A **terminal emulator** is a graphical software application that provides a user-friendly interface for command-line interaction
- A **TTY (Virtual Terminal)** refers to the actual text-based interface where command-line tasks are performed, whether in a terminal emulator window or via keyboard shortcuts.

**Terminal emulators emulate the behavior of TTYs within a graphical environment.**

- Why is it called “TTY”?
    
    "tty" stands for "teletypewriter." It is a term inherited from the early days of computing when physical teletypewriters were used as input and output devices for interacting with computers.
    

## Useful Commands `command -options arguments`

---

- `systemctl` (System Control)
    - Starting, stopping, restarting a service (using httpd as an example) on a currently running system:
        - `$ sudo systemctl start|stop|restart httpd.service`
    - Enabling or disabling a system service from starting up at system boot:
        - `$ sudo systemctl enable|disable httpd.service`
- `df` → Report file system disk space usage
- `super` + `l` → lock screen
- **File Manager:**
    - `ctrl` + `1` → view files as list
    - `ctrl` + `2` → view files as icons
    - `ctrl` + `h` → view hidden files
- `alt` + `f2` → run single command
- `cat` → print file contents
- `tac` → prints entire file backwards
- `touch -t`  → allows you to update the date and time of a file
- `head` → print first 10 lines of a file
    - `head -# filename`  → print first # lines of a file
- `tail` → print last few lines of a file
- Virtual Terminal (no GUI):
    - `ctrl` + `alt` + `f#` →Switch to vt# (number 1 through 6)
    - To restart the graphic display manager:
        - `sudo systemctl start|stop gdm`
- `which programName` → locate programName
- `whereis programName`  → locate programName (in a broader range of system directories)
- `tree` → view entire filesystem tree (`-d` to suppress filenames)
- `wc filename` → word count
- `less filename` →display one page of file at a time
    - `less -N filename` →display one page of file at a time with line numbers

## `bash` Keyboard Shortcuts

---

1. **Navigation Shortcuts**:
    - **`Ctrl + A`**: Move to the beginning of the line.
    - **`Ctrl + E`**: Move to the end of the line.
    - **`Alt + B`** or **`Esc + B`**: Move back one word.
    - **`Alt + F`** or **`Esc + F`**: Move forward one word.
    - **`Ctrl + U`**: Delete from the cursor to the beginning of the line.
    - **`Ctrl + K`**: Delete from the cursor to the end of the line.
    - **`Ctrl + W`**: Delete the word to the left of the cursor.
    - **`Ctrl + Y`**: Paste the most recently deleted text.
2. **Editing Shortcuts**:
    - **`Ctrl + L`** or **`clear`**: Clear the screen (similar to running the **`clear`** command).
    - **`Ctrl + C`**: Interrupt (terminate) the currently running command.
    - **`Ctrl + D`**: Exit the current shell session or send an EOF (End of File) character to exit input mode.
    - **`Ctrl + Z`**: Suspend the current foreground process. Use **`fg`** to bring it back to the foreground or **`bg`** to run it in the background.
    - **`!!`**: Repeats the last executed command.
    - **`!command`**: Repeats the last command that starts with "command."
3. **History Shortcuts**:
    - **`Ctrl + R`**: Search backward in command history. Start typing a command, and it will auto-fill with the most recent matching command.
    - **`Up Arrow`** and **`Down Arrow`**: Navigate through previously entered commands.
    - **`!!`**: Repeats the last executed command.
    - **`!n`**: Repeats the nth command in history (e.g., **`!5`** runs the fifth command).
4. **Tab Completion**:
    - **`Tab`**: Automatically completes filenames, directories, commands, and variables when typing. Pressing **`Tab`** twice shows a list of available options if there's ambiguity.
5. **Other Useful Shortcuts**:
    - **`Ctrl + S`**: Pause the terminal output. Press **`Ctrl + Q`** to resume.
    - **`Ctrl + G`**: Cancel the current action (e.g., incremental search).
    - **`Ctrl + T`**: Swap the two characters before the cursor.
    - **`Ctrl + _`** (underscore): Undo the last change.
6. **Custom Shortcuts**:
    - You can create custom keyboard shortcuts by modifying your shell's configuration files (e.g., **`~/.bashrc`** for Bash) or by using a utility like **`bind`** to assign specific functions to key combinations.

### The Pipe `|`

---

The pipe (**`|`**) in Linux and Unix-like systems allows you to take the output of one command and use it as the input for another, enabling the creation of command pipelines for tasks like text filtering, data transformation, and complex data processing.

Using the pipe is **more efficient** when doing multiple Linux commands because it allows for the simultaneous execution of commands, enabling data to flow directly from one command to another **without the need to store intermediate results in temporary files or buffers**.

For example, **`command1 | command2`** takes the output of **`command1`** and feeds it as input to **`command2`**.

You can chain multiple commands together using pipes to perform complex operations. For instance, you can use `ps` to list running processes, filter them with `grep`, and then sort the result:

```bash
ps aux | grep "process_name" | sort
```

### Secure Shell `ssh user@remoteserver.com`

---

SSH securely connects a user to a computer or server and gives that user a command line terminal window.

SSH (Secure Shell) is a network protocol that allows secure remote access to a computer or server. It works by establishing an encrypted connection between a client (your computer) and a server (the remote machine) to ensure secure data transmission. SSH uses **public-key cryptography** for authentication and encryption to protect the communication between the client and server, making it difficult for unauthorized parties to intercept or tamper with the data being transmitted.

### PS1

---

The **`PS1`** variable in Linux is an environment variable that defines the format and content of the primary shell prompt. Heres an example customized PS1 variable:

```bash
export PS1="\u@\h:\w\$ "
```

In this example:

- **`\u`** represents the username.
- **`\h`** represents the hostname.
- **`\w`** represents the current working directory.
- **`\$`** represents the command prompt symbol (**`$`** for a regular user and **`#`** for the root user).

### IO Redirection

---

| File Descriptor | Description |
| --- | --- |
| 0 | Standard Input (stdin) |
| 1 | Standard Output (stdout) |
| 2 | Standard Error (stderr) |
| 3+ | Additional File Descriptors (custom) |

| I/O Redirection | Description | Example | File Descriptors |
| --- | --- | --- | --- |
| > | Redirects stdout to a file | command > file.txt | stdout → file.txt (1 → file descriptor) |
| >> | Appends stdout to a file | command >> file.txt | stdout → file.txt (1 → file descriptor) |
| < | Redirects stdin from a file | command < input.txt | stdin ← input.txt (0 ← file descriptor) |
| 2> | Redirects stderr to a file | command 2> error.txt | stderr → error.txt (2 → file descriptor) |
| 2>> | Appends stderr to a file | command 2>> error.txt | stderr → error.txt (2 → file descriptor) |
| &> | Redirects both stdout and stderr to a file | command &> output.txt | stdout, stderr → output.txt (1, 2 → file descriptors) |
| ` | ` | Redirects stdout of one command to stdin of another | `command1 |

### Locating Files

---

1. **`find`**: Searches for files and directories **recursively** from a specified starting location.
Example: **`find /path/to/search -name filename`**
2. **`locate`**: Utilizes a pre-built database to quickly search for files and directories.
Example: **`locate filename`**
3. **`which`**: Finds the path to an executable program in your system's PATH.
Example: **`which program_name`**
4. **`whereis`**: Locates the binary, source code, and man page for a command.
Example: **`whereis command_name`**
5. **`locate`**: Searches for files and directories based on patterns.
Example: **`locate pattern`**
6. **`grep`**: Searches for a specific pattern within files.
Example: **`grep "search_string" file_or_directory`**
7. **`fd`**: A faster alternative to **`find`** with a simpler syntax.
Example: **`fd search_string /path/to/search`**
8. **`rg`** (ripgrep): A fast and efficient recursive search tool.
Example: **`rg search_string /path/to/search`**

### Find & Remove Files

`find -name "*swp" -exe rm {} ';'` → finds and removes files that ends with .swp 

### Wildcards for Searching (REGEX)

---

| Wildcard | Description | Example |
| --- | --- | --- |
| * | Matches any sequence of characters | file*.txt matches file1.txt, file2.txt, etc. |
| ? | Matches any single character | file?.txt matches file1.txt, but not file12.txt |
| [...] | Matches any character within the brackets | [aeiou] matches any vowel character |
| [!...] | Matches any character NOT within the brackets | [^0-9] matches any non-digit character |
| {...,...} | Matches any of the comma-separated patterns | {file1,file2}.txt matches file1.txt or file2.txt |

If you put your wildcard in quotes, the command will not run in the current directory 

These wildcards are used in conjunction with commands like **`ls`**, **`find`**, and **`grep`** to perform flexible and powerful file and directory searches in Linux.

### **Environmental Variables**

- To set a temporary environmental variable for the current session, use **`export`**:
    - **`export MY_VARIABLE='my_value'`**
- To set a permanent environmental variable for all sessions, add it to your shell's configuration file (e.g., **`~/.bashrc`** for Bash) and reload the configuration:
    - **`echo 'export MY_VARIABLE="my_value"' >> ~/.bashrc`**
    - **`source ~/.bashrc`**

**Viewing Environmental Variables**:

- To view all environmental variables:
    - **`env`**
- To view a specific variable, use **`echo`**:
    - **`echo $MY_VARIABLE`**

**Modifying Environmental Variables**:

- To modify an existing variable, reassign its value (in .bashrc):
    - **`MY_VARIABLE='new_value'`**

**Unsetting Environmental Variables**:

- To unset (remove) a variable:
    - **`unset MY_VARIABLE`**

**Managing Global Environmental Variables**:

- System-wide environmental variables are often set in files like **`/etc/environment`** or scripts within **`/etc/profile.d/`**.

## Manipulating Text & Files

---

`less`: A terminal pager utility ideal for viewing larger files. It allows for efficient navigation and reading of content by loading only the portion of the file that is currently visible, reducing memory consumption and enabling quick access to specific sections.

### `sed`

---

The Linux command **`sed`** (**stream editor**) is a powerful text manipulation tool used for modifying text and streams of data, primarily through the use of regular expressions.

Here's an overview of **`sed`**:

**Purpose**:

- **`sed`** is used for text processing tasks, such as search and replace, text transformations, and selective printing of lines from input text or files.

**Basic Syntax**:

- The basic syntax of **`sed`** is:
    
    ```bash
    sed [options] 'command' filename
    ```
    

**Usage Examples**:

1. **Search and Replace**:
    - To replace the first occurrence of a pattern in a file:
        
        ```bash
        sed 's/pattern/replacement/' filename
        ```
        
    - To replace all occurrences of a pattern globally in a file:
        
        ```bash
        sed 's/pattern/replacement/g' filename
        ```
        
2. **Print Specific Lines**:
    - To print specific lines from a file (e.g., lines 5 to 10):
        
        ```bash
        sed -n '5,10p' filename
        ```
        
3. **Deleting Lines**:
    - To delete lines matching a pattern:
        
        ```bash
        sed '/pattern/d' filename
        ```
        
4. **Appending and Inserting Text**:
    - To append text after a specific line number (e.g., after line 3):
        
        ```bash
        sed '3a\New line to append' filename
        ```
        
    - To insert text before a specific line number (e.g., before line 3):
        
        ```bash
        sed '3i\New line to insert' filename
        ```
        
5. **Substituting with Special Characters**:
    - **`sed`** allows you to use different delimiter characters, like **`#`** or **`|`**, when specifying patterns or replacements to avoid conflicts with forward slashes.
    
    ```bash
    sed 's#pattern#/replacement/#' filename
    ```
    

**Options and Flags**:

- **`sed`** has various options and flags for controlling its behavior, such as **`i`** for in-place editing of files, **`e`** for specifying multiple commands, and more. You can explore these options in the manual (**`man sed`**) for advanced usage.

**Piping with `sed`**:

- **`sed`** is often used in conjunction with other commands and pipelines to perform complex text processing tasks.

**Important Note**:

- When using **`sed`** for in-place editing with the **`i`** option, be cautious, as it directly modifies the file. Make backups or use **`i.bak`** to create backup files.

### **`awk`**

---

The Linux command **`awk`** is a versatile text processing tool used for extracting and manipulating structured data from files, particularly when data is organized in rows and columns.

Here's an overview of **`awk`**:

**Purpose**:

- **`awk`** is designed for text processing tasks that involve data extraction, transformation, and reporting, making it ideal for tasks like data analysis and text manipulation.

**Basic Syntax**:

- The basic syntax of **`awk`** is:
    
    ```bash
    awk [options] 'pattern { action }' filename
    ```
    
    - **`pattern`** specifies a condition that determines when the action should be applied.
    - **`action`** defines what should be done when the condition is met.

**Usage Examples**:

1. **Print Specific Columns**:
    - To print specific columns from a file (e.g., columns 2 and 4):
        
        ```bash
        awk '{print $2, $4}' filename
        ```
        
2. **Filtering Data**:
    - To filter data based on a condition (e.g., print lines where the third column is greater than 50):
        
        ```bash
        awk '$3 > 50' filename
        ```
        
3. **Calculations**:
    - **`awk`** can perform calculations on data, such as summing values in a column:
        
        ```bash
        awk '{sum += $1} END {print sum}' filename
        ```
        
4. **Custom Output**:
    - You can customize the output format, including adding labels and separators:
        
        ```bash
        awk '{print "Name: " $1, "Age: " $2}' filename
        ```
        
5. **Field Separators**:
    - **`awk`** can handle various field separators (e.g., comma, tab) to work with different data formats:
        
        ```bash
        awk -F',' '{print $1, $3}' data.csv
        ```
        

**Options and Flags**:

- **`awk`** provides various options and flags for specifying field separators, input files, and more. Consult the manual (**`man awk`**) for a comprehensive list of options.

**Piping with `awk`**:

- **`awk`** is often used in pipelines with other commands to process and transform data within complex data analysis workflows.

**Advanced `awk`**:

- **`awk`** supports user-defined functions and more complex programming constructs, making it a powerful tool for data processing and manipulation.

**Important Note**:

- Understanding the structure of your data and the desired transformations is crucial when using **`awk`**. With its robust features, it's a valuable tool for data extraction and manipulation in the Linux command line.

### Regular Expression (REGEX)

---

| Component | Description | Example |
| --- | --- | --- |
| Literal Characters | Characters that match themselves. | a matches 'a' |
| Metacharacters | Special characters with reserved meanings. | . matches any character |
|  |  | * matches zero or more |
|  |  | + matches one or more |
|  |  | ? matches zero or one |
|  |  | ` |
|  |  | () grouping |
|  |  | [] character classes |
|  |  | {} quantifiers |
| Common Uses |  |  |
| Matching Strings | Find specific words or phrases in text. | grep 'pattern' file.txt |
| Search and Replace | Replace text based on patterns. | sed 's/pattern/repl/g' |
| Data Extraction | Extract data from structured text. | awk '/pattern/ {print $2}' |
| Examples |  |  |
| .  | Matches any single character. |  |
| * | Matches zero or more occurrences of preceding char. |  |
| +  | Matches one or more occurrences of preceding char. |  |
| ? | Matches zero or one occurrence of preceding char. |  |
| | | | | Alternation operator, matches either pattern. |
| ()  | Groups characters or subpatterns together. |  |
| []  | Character class, matches characters in brackets. |  |
| {}  | Quantifiers, specify occurrence quantity. |  |
| Advanced Features |  |  |
| ^ | Matches start of a line. |  |
| $  | Matches end of a line. |  |
| Escape Sequences | Use backslashes to escape metacharacters. | \. matches a literal dot |
| Modifiers | i (case-insensitive), g (global), m (multiline) |  |
- Useful regex Examples
    1. **Matching Email Addresses**:
        - This regex matches valid email addresses:
            
            ```c
            ^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$
            ```
            
    2. **Matching URLs**:
        - This regex matches URLs, including http and https schemes:
            
            ```c
            ^(http|https)://[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}/[a-zA-Z0-9.-]+$
            ```
            
    3. **Extracting Dates from Text**:
        - This regex extracts dates in the format "MM/DD/YYYY" from text:
            
            ```c
            \b(0[1-9]|1[0-2])/(0[1-9]|[12][0-9]|3[01])/\d{4}\b
            ```
            
    4. **Extracting Phone Numbers**:
        - This regex extracts U.S. phone numbers in various formats:
            
            ```c
            \b\d{3}[-.]?\d{3}[-.]?\d{4}\b
            ```
            
    5. **Matching IP Addresses**:
        - This regex matches IPv4 addresses:
            
            ```c
            \b\d{1,3}\.\d{1,3}\.\d{1,3}\.\d{1,3}\b
            ```
            
    6. **Matching HTML Tags**:
        - This regex matches HTML tags and extracts their content:
            
            ```c
            <[^>]+>([^<]+)</[^>]+>
            ```
            
    7. **Matching Hex Color Codes**:
        - This regex matches hex color codes (e.g., #FFA500):
            
            ```c
            #[0-9A-Fa-f]{6}
            ```
            
    8. **Matching File Extensions**:
        - This regex matches file extensions (e.g., .txt, .jpg):
            
            ```c
            \.\w+$
            ```
            
    9. **Matching Words with a Specific Prefix**:
        - This regex matches words starting with "pre-":
            
            ```c
            \bpre-\w+\b
            ```
            
    10. **Extracting Hashtags from Social Media Posts**:
        - This regex extracts hashtags (words starting with "#") from social media posts:
            
            ```c
            #\w+
            ```
            

# Linux Processes

---

A **process** is a running instance of a program in a computer's memory, with its own set of resources, execution state, and system resources, capable of performing tasks and running independently of other processes.

**List processes with `ps`**

| Process Type | Description |
| --- | --- |
| Foreground Processes | Processes that run in the foreground and interact with the user directly through the terminal. |
| Background Processes | Processes that run in the background and do not require user interaction, allowing the user to continue working in the terminal. |
| Daemon Processes | System processes that run continuously in the background, often providing essential system services, such as web servers, database servers, or print spoolers. |
| Kernel Processes | Low-level processes that are part of the Linux kernel itself, responsible for managing hardware and core system functions. |
| Zombie Processes | Processes that have completed their execution but still have an entry in the process table, awaiting their parent process to retrieve exit status. |
| Orphan Processes | Processes whose parent process has terminated, and they are adopted by the init process (usually with process ID 1). |
| User Processes | Processes initiated and controlled by regular users, such as running applications or user-specific tasks. |
| System Processes | Processes that are crucial for the functioning of the operating system, including those managing hardware, memory, and other system-level tasks. |

## Process IDs

---

| Process ID Type | Description |
| --- | --- |
| Parent Process ID (PPID) | The ID of the parent process that spawned the current process. |
| Process Group ID (PGID) | Identifies a group of processes within the same session, typically used for job control. |
| Session ID (SID) | Represents a collection of process groups, often associated with a user's login session. |
| Thread Group ID (TGID) | Identifies the thread group leader in a multithreaded process; other threads in the same process have the same TGID. |
| Foreground Process Group ID | The process group ID associated with the currently active foreground job in a terminal. |
| Process ID (PID) | The unique identifier for an individual running process, assigned by the operating system. |

### Killing a process

`$ kill -SIGKILL <pid>` OR `$ kill -9 <pid>`

### Process Priority

**Lower values == higher priority**

**Higher values == lower priority** 

- To **increase** a process's priority (make it less nice), use: **`nice -n <priority> <command>`**
- To **decrease** a process's priority (make it more nice), use: **`nice -- <command>`**

Example (higher priority):

```bash
nice -n -10 ./myprocess
```

### Scheduling a Process

---

You can schedule processes on a Linux machine using the **`cron`** and **`at`** utilities:

**Cron:**

1. Edit your user's crontab file: **`crontab -e`**
2. Add a line specifying the schedule and command, e.g., **`* * * * /path/to/command`**
3. Save and exit the editor.

The five asterisks represent the schedule (minute, hour, day of month, month, day of week). Use **`man 5 crontab`** for syntax details.

**At:**

1. Use the **`at`** command to schedule a one-time task: **`at HH:MM`**
2. Enter the command(s) you want to run.
3. Press **`Ctrl+D`** to save and schedule the task.
    
    Replace **`HH:MM`** with the desired time.
    

## Load Average (System Workload)

---

**Load Average**: The load average in Linux represents the average number of processes in the run queue over different time intervals. It provides a measure of system workload. **Typically, you'll see three load average values for the last 1, 5, and 15 minutes.**

| Command | Description |
| --- | --- |
| w | Displays load average, current users, and more system statistics. |
| top | Interactive system monitoring tool showing load average and detailed process information. |
| uptime | Shows system uptime and load average for the last 1, 5, and 15 minutes. |

**To interpret load average values:**

- A load average of 1.0 means the system is fully utilizing one CPU core.
- Values above 1.0 indicate a workload exceeding the capacity of a single core.
- Values below the number of CPU cores generally indicate a healthy system.

# Linux Networking

---

**1. `ifconfig` (or `ip`)**

**Description**: **`ifconfig`** is a legacy tool used for configuring and displaying network interfaces, while **`ip`** is a more modern and versatile command for managing network interfaces.

**Usage**: Display network interface information or configure interfaces.

**Example**:

```bash
# Display network interface information
ifconfig

# Set the IP address of an interface (using 'ip')
ip address add 192.168.1.10/24 dev eth0
```

**2. `ping`**

**Description**: **`ping`** is used to test network connectivity by sending ICMP echo request packets to a destination host and waiting for responses.

**Usage**: Check if a remote host is reachable and measure round-trip time.

**Example**:

```bash
# Ping a host (e.g., google.com)
ping google.com
```

**3. `traceroute` (or `tracepath`)**

**Description**: **`traceroute`** (or **`tracepath`**) is used to trace the route that packets take to reach a destination, showing all the hops between your computer and the target.

**Usage**: Diagnose network path and identify routing issues.

**Example**:

```bash
# Trace the route to a host (e.g., google.com)
traceroute google.com
```

**4. `netstat` (or `ss`)**

**Description**: **`netstat`** (or **`ss`**) displays network statistics, including active network connections, listening ports, and routing tables.

**Usage**: View network status and configuration.

**Example**:

```bash
# Display listening ports and their associated processes (using 'ss')
ss -tuln
```

**5. `nslookup` (or `dig`)**

**Description**: **`nslookup`** (or **`dig`**) is used for DNS (Domain Name System) queries to resolve hostnames to IP addresses and vice versa.

**Usage**: Resolve DNS queries and troubleshoot DNS issues.

**Example**:

```bash
# Perform a DNS lookup for a hostname (using 'nslookup')
nslookup google.com

# Perform a more detailed DNS query (using 'dig')
dig google.com
```

**6. `curl` (or `wget`)**

**Description**: **`curl`** (or **`wget`**) is used for downloading files or accessing web resources over HTTP, HTTPS, FTP, or other protocols.

**Usage**: Fetch files or interact with web services from the command line.

**Example**:

```bash
# Download a file from a URL (using 'curl')
curl -O https://example.com/file.txt
```

**7. `ssh` (Secure Shell)**

**Description**: **`ssh`** is used for secure remote access and administration of systems over a network. It provides encrypted communication.

**Usage**: Connect to remote servers securely, transfer files, and execute commands remotely.

**Example**:

```bash
# Connect to a remote server
ssh username@remote_host

# Securely copy files to/from a remote server (using 'scp')
scp local_file.txt username@remote_host:/path/to/destination/
```

**8. `iptables` (or `firewalld`)**

**Description**: **`iptables`** (or **`firewalld`**) is used for configuring and managing firewall rules to control network traffic.

**Usage**: Set up firewall rules to secure your system.

**Example**:

```bash
# Allow incoming SSH traffic (port 22) through the firewall
iptables -A INPUT -p tcp --dport 22 -j ACCEPT
```

**9. `netcat` (or `nc`)**

**Description**: **`netcat`** (or **`nc`**) is a versatile tool for creating network connections, port scanning, and transferring data over TCP or UDP.

**Usage**: Perform various network-related tasks, including port scanning and data transfer.

**Example**:

```bash
# Create a simple TCP server on port 12345 (using 'nc')
nc -l -p 12345

# Connect to a remote server on a specific port (using 'nc')
nc remote_host 80
```

**10. `scp` (Secure Copy Protocol)**

**Description**: **`scp`** is a command-line tool for securely copying files and directories between hosts over an SSH (Secure Shell) connection. It provides encrypted data transfer.

**Usage**: Transfer files and directories between local and remote systems securely.

**Example**:

```bash
# Copy a local file to a remote server
scp local_file.txt username@remote_host:/path/to/destination/

# Copy a remote file to the local system
scp username@remote_host:/path/to/remote_file.txt /local/destination/
```

# Linux Families (Distro Categories)

---

1. **Debian-Based:**
    - Debian: The Debian distribution is known for its stability and commitment to free and open-source software principles.
    - Ubuntu: Ubuntu is based on Debian and is designed to be more user-friendly and geared towards desktop users. It has both LTS (Long Term Support) and regular releases.
2. **Red Hat-Based:**
    - Red Hat Enterprise Linux (RHEL): RHEL is a commercial distribution known for its stability, security, and support. It serves as the basis for other distributions.
    - CentOS: CentOS was a free, community-supported clone of RHEL. However, it has been replaced by CentOS Stream, which is not a direct RHEL clone.
    - Fedora: Fedora is a bleeding-edge distribution sponsored by Red Hat, designed for developers and enthusiasts. It often introduces new technologies and features.
3. **SUSE-Based:**
    - openSUSE: openSUSE is a community-driven distribution known for its flexibility and choice of desktop environments. It has a rolling release version called "openSUSE Tumbleweed."
4. **Arch-Based:**
    - Arch Linux: Arch is known for its simplicity and customizability. It follows a rolling release model, providing the latest software updates and packages.
5. **Gentoo-Based:**
    - Gentoo: Gentoo is a highly customizable distribution known for its source-based package management system (Portage). Users compile software from source code, optimizing it for their hardware.
6. **Slackware-Based:**
    - Slackware: Slackware is one of the oldest Linux distributions, known for its simplicity and minimalism. It adheres to the KISS (Keep It Simple, Stupid) principle.
7. **Independent:**
    - These distributions are not based on any of the major families and often have unique features or purposes. Examples include:
        - Alpine Linux: Known for its small size and security features, often used in containerized environments.
        - Void Linux: A rolling-release distribution with its package manager (xbps).
8. **Specialized:**
    - Some distributions are designed for specific purposes, such as security and penetration testing (e.g., Kali Linux), multimedia production (e.g., Ubuntu Studio), or education (e.g., Edubuntu).

It's important to note that within each family, there may be various derivatives and flavors, each tailored to different use cases or preferences. The choice of a Linux distribution depends on factors like your intended use, system requirements, familiarity with the distribution, and personal preferences.

## Choosing a Distro Based on Specific Needs

---

| Server | Desktop | Embedded |
| --- | --- | --- |
| RHEL/CentOS | Ubuntu | Yocto |
| Ubuntu Server | Fedora | Open Embedded |
| SLES | Linux Mint | Android |
| Debian | Debian |  |

# Linux Boot Process

---

### 1. **BIOS/UEFI Initialization:**

- When powered on, the BIOS/UEFI firmware (stored in a motherboard ROM chip) performs Power-On Self-Test (POST) to check hardware integrity and identify bootable devices.
- It locates the boot device (typically the hard drive or SSD) specified in the boot order.

### 2. **Master Boot Record (MBR):**

- The MBR (first sector of the hard disk) loads the boot loader.

### 3. **Boot Loader (GRUB) Execution:**

- The boot loader (e.g., GRUB or LILO) is loaded from MBR or EFI System Partition (ESP).
- It presents boot options, including Linux kernel selection.

### 4. **Kernel Initialization:**

- The chosen Linux kernel loads into RAM.
- The kernel initializes hardware and mounts an initial ramdisk (initramfs) containing tools for root filesystem mounting.
- After successfully mounting the root filesystem, initramfs is cleared, and the root filesystem's init program is executed.

### 5. **Execution of `/sbin/init`:**

- The kernel launches **`/sbin/init`** as the first user-space process.
- **`/sbin/init`** is known as the "init process," responsible for managing all user-space processes, services, and system initialization tasks.

### 6. **System Initialization:**

- **`/sbin/init`** reads its configuration file (usually **`/etc/inittab`** or **`/etc/init`**) to determine the system's runlevel or target (e.g., multi-user.target).
- It starts system services, mounts additional filesystems, and sets up the desired system state.

### 7. **Initialization and Service Management (Modern Systems):**

- On modern Linux distributions using systemd, **`/sbin/init`** may spawn systemd as the init process (i.e. `/sbin/init` points to `/lib/systemd/systemd` and takes over the init process).
- systemd takes over process management, service initialization, and system configuration from **`/etc/systemd`**.
- The init process (historically SysVinit or Systemd) is the first user-space program.
- It manages system service initialization, filesystem mounting, environment variables, and executes startup scripts to reach the target system state.

### 8. **Service Initialization:**

- Systemd (which is very fast due to aggressive parallel execution of startup scripts) or SysVinit initializes system services (e.g., networking, logging, device management) based on dependencies and runlevels.

### 9. **User Login:**

- The system is ready for user interaction, presenting a login prompt through text-based terminals (TTY) or graphical login managers.

### 10. **Desktop Environment (X (X11) Server is Launched):**

- If configured, the X (X11) server is launched. The X (X11) server is responsible for managing graphics hardware and rendering the graphical user interface.
- GNOME == Desktop Environment

### 11. **User Sessions:**

- Users run applications, manage files, and perform tasks within their sessions.

# Filesystem

---

### Linux Operating System vs. Linux Filesystem vs. Linux Partition

---

**Linux Operating System**: Linux is the kernel or core of the operating system. It provides low-level hardware interaction, process management, memory management, and other essential functions. Linux itself is not a file system; it's the software that manages hardware resources and facilitates interactions between hardware and software.

**Partitions**: In the context of a Linux system, partitions are logical divisions of a physical storage device, such as a hard drive or SSD. Each partition functions as a separate unit on which a file system can be created and mounted. Partitions serve several important purposes within the Linux ecosystem:

- **Isolation**: Partitions allow you to isolate data and system files. For example, the root partition ("/") contains the core operating system files, while other partitions can hold user data, applications, or specific types of data. This isolation helps with security and system stability.
- **Organization**: Partitions help organize and manage data more efficiently. You can create separate partitions for different purposes, such as a /home partition for user home directories or a /var partition for variable data like logs and databases.
- **Flexibility**: Partitions can be resized, formatted, or managed independently, without affecting other partitions. This flexibility allows you to adapt your storage configuration to changing needs.

**File System**: A file system is a higher-level abstraction that sits on top of the kernel and is applied to partitions. It provides a structured way to organize and manage files and directories within a partition. In Linux, there are several types of file systems (e.g., ext4, XFS, Btrfs), and each partition can have its own file system.

- **File System Hierarchy**: The file system defines how data is stored on disk, how directories are structured, and how file metadata is managed. In Linux, there's a standardized directory structure known as the Filesystem Hierarchy Standard (FHS). It specifies where different types of files and directories should be located within the system. The root directory ("/") is the starting point for this hierarchy.

To illustrate the relationship:

- The Linux operating system (kernel) interacts with hardware and provides a platform for running applications.
- Partitions are logical divisions of storage devices, and each partition can have its own file system.
- File systems define how data is organized and managed within each partition.
- The Filesystem Hierarchy Standard (FHS) guides the organization of directories and files within the file systems, starting from the root directory ("/").

### Managing Partitions

---

| Task | Command/Procedure |
| --- | --- |
| Creating Partitions | Using fdisk: |
|  | 1. sudo fdisk /dev/sdX (replace "X" with the appropriate drive letter). |
|  | 2. Use the n command to create a new partition. |
|  | 3. Specify the partition type, start and end sectors, and write changes with the w command. |
|  |  |
|  | Using parted: |
|  | 1. sudo parted /dev/sdX (replace "X" with the appropriate drive letter). |
|  | 2. Use the mkpart command to create a new partition. |
|  | 3. Specify the file system type, start, and end points. |
|  | 4. Quit and save changes with the quit command. |
| Destroying Partitions | Using fdisk: |
|  | 1. sudo fdisk /dev/sdX (replace "X" with the appropriate drive letter). |
|  | 2. Use the d command to delete a partition. |
|  | 3. Write changes with the w command. |
|  |  |
|  | Using parted: |
|  | 1. sudo parted /dev/sdX (replace "X" with the appropriate drive letter). |
|  | 2. Use the rm command to remove a partition. |
|  | 3. Quit and save changes with the quit command. |
| Unmounting Partitions | To unmount a currently mounted partition, use the umount command followed by the mount point: |
|  | sudo umount /mnt/my_partition |
| Mounting Partitions | 1. Create a directory where you want to mount the partition. For example: sudo mkdir /mnt/my_partition |
|  | 2. Mount the partition using the mount command: sudo mount /dev/sdXY /mnt/my_partition (replace "/dev/sdXY" with the actual partition device and "/mnt/my_partition" with the desired mount point). |
| Managing Partitions | - To list partitions: lsblk, fdisk -l, or parted -l. |
|  | - To check the file system: sudo fsck /dev/sdXY (replace "/dev/sdXY" with the actual partition device). |
|  | - To resize partitions: Use tools like resize2fs (for ext file systems) or xfs_growfs (for XFS file systems). |
|  | - To modify labels: Commands like e2label (for ext file systems) or xfs_admin (for XFS file systems). |
|  | - To change mount options: Edit the /etc/fstab file or use the mount command with specific options. |
|  | - Always back up data and exercise caution when modifying partitions to avoid data loss. |

### Filesystem Hierarchy Standard (FHS)

---

1. **`/` (Root Directory):** The top-level directory that contains all other directories and files on the system.
2. **`/bin` (Essential User Binaries):** Contains essential command binaries required for system recovery and repair.
3. **`/boot` (Boot Loader Files):** Stores bootloader configuration, kernel images, and initial ramdisk (initramfs) files needed for system booting.
4. **`/dev` (Device Files):** Contains device files representing hardware devices, allowing user programs to interact with hardware through device files.
5. **`/etc` (System Configuration Files):** Stores system-wide configuration files and startup scripts for various services and applications.
6. **`/home` (User Home Directories):** Each user typically has a home directory here, where they store their personal files and settings.
7. **`/lib` (Essential Shared Libraries):** Contains essential shared libraries used by programs and utilities in **`/bin`** and **`/sbin`**.
8. **`/lib64` (64-bit Shared Libraries):** On 64-bit systems, it contains 64-bit shared libraries.
9. **`/media` (Removable Media Mount Points):** Mount points for removable media devices (e.g., USB drives, CDs) that are automatically mounted when inserted.
10. **`/mnt` (Temporary Mount Points):** A directory used for temporarily mounting filesystems.
11. **`/opt` (Optional Packages):** Typically used by software packages that are not part of the core system distribution.
12. **`/proc` (Kernel and Process Information):** A virtual filesystem that provides information about the kernel, processes, and system settings.
13. **`/root` (Root User Home Directory):** The home directory for the root user.
14. **`/run` (Runtime Data):** Contains system runtime data, such as process IDs (PIDs) and socket files.
15. **`/sbin` (System Binaries):** Contains essential system binaries, typically used by the root user.
16. **`/srv` (Service Data):** Stores data for services provided by the system.
17. **`/sys` (Sysfs Filesystem):** A virtual filesystem that exposes information about the kernel and hardware devices.
18. **`/tmp` (Temporary Files):** A directory for temporary files created by user and system programs.
19. **`/usr` (User Binaries and Libraries):** Contains user binaries, libraries, documentation, and other non-essential system files.
20. **`/var` (Variable Data):** Contains variable data, including logs, spool files, and temporary files generated by applications and services.
21. **`/mnt` (Mount Point for Temporary Mounts):** A common directory for temporarily mounting filesystems.

### Disk Partitions

---

A disk partition is a logical division of a physical hard drive or storage device. Each partition functions as a separate unit, and you can think of them as separate "virtual" drives even though they share the same 

1. **Primary Purpose**: Disk partitions are used to organize and manage data on a storage device efficiently. They help separate different types of data, control access, and provide isolation between various parts of the file system.
2. **File Systems**: Each partition typically has its own file system, which defines how data is stored, accessed, and organized. Common Linux file systems include ext4, XFS, and Btrfs.
3. **Partition Table**: The partition table is a data structure that stores information about the partitions on a storage device. In Linux, the two most commonly used partition table formats are MBR (Master Boot Record) and GPT (GUID Partition Table).
    - MBR: Supports up to four primary partitions or three primary partitions and one extended partition containing multiple logical partitions.
    - GPT: Supports a much larger number of partitions (up to 128) and is the modern standard for new systems.
4. **Mount Points**: Each partition is typically mounted at a specific directory in the Linux file system hierarchy. This directory is called the mount point. When a partition is mounted at a particular mount point, the files and directories on that partition become accessible at that location.
5. **Root Partition**: In Linux, the root partition (often denoted as "/") contains the core operating system files and directories. It's essential for the system to boot and function correctly.
6. **Data Partitions**: Linux users often create additional partitions for storing user data, applications, or specific types of data. For example, you might have a separate partition for /home, where user home directories are located, or a partition for /var, which stores variable data like logs and databases.
7. **Advantages**:
    - Partitioning allows you to isolate data and system files, which can help with security and system stability.
    - It enables you to resize, format, or manage partitions independently, without affecting other partitions.
    - Different file systems and partitioning schemes can be used to optimize performance or accommodate specific use cases.
8. **Commands**: Common Linux commands for working with partitions include **`fdisk`**, **`parted`**, and **`gparted`** for partition management and **`mkfs`** for creating file systems on partitions. To mount and unmount partitions, you can use **`mount`** and **`umount`**.

### Filesystems supported by Linux:

---

- **Conventional disk filesystems** (ext3, ext4, XFS, Btrfs, JFS, NTFS, vfat, etc..)
- **Flash storage filesystems** (ubifs, jffs2, yaffs, etc..)
- **Database filesystems**
- **Special purpose filesystems** (procfs, sysfs, tmpfs, squashfs, debugfs, etc..)

### File Permissions

---

when running `ls -l` the output will display the file type as well as the file permissions for:

The **OWNER**’s permissions      the **GROUP**’s permissions      **OTHER**’s permissions

F**ile types**:

- `-` indicates a regular file.
- **`d`** indicates a directory.
- **`l`** indicates a symbolic link.
- **`c`** indicates a character device.
- **`b`** indicates a block device.
- **`s`** indicates a Unix socket.
- **`p`** indicates a named pipe (FIFO).

### Changing File Permissions

---

**Changing Permissions**:

- You can use the **`chmod`** command to change file permissions. The basic syntax is:
    
    ```bash
    chmod permissions file_or_directory
    ```
    
- Permissions can be represented using three different notations:
    - **Symbolic Notation**: Uses symbols like **`u`** (user/owner), **`g`** (group), **`o`** (others), **`a`** (all), **`+`** (add permission), **``** (remove permission), and **`=`** (set permission).
        
        ```bash
        chmod u+r file.txt  # Add read permission for the owner.
        chmod o-rwx file.txt  # Remove read, write, and execute permissions for others.
        chmod a=rx file.txt  # Set read and execute permissions for all.
        ```
        
    - **Octal Notation**: Represents permissions as three octal digits (0-7). **Each digit corresponds to the owner, group, and others, with values indicating read (4), write (2), and execute (1) permissions.**
        
        ```bash
        chmod 644 file.txt  # Owner can read and write, group and others can only read.
        chmod 755 script.sh  # Owner can read, write, and execute; group and others can read and execute.
        ```
        
    - **Absolute Notation**: Specifies permissions explicitly using the **`r`** (read), **`w`** (write), and **`x`** (execute) options.
        
        ```bash
        chmod u=rwx,g=rx,o=r file.txt  # Owner can read, write, and execute; group can read and execute; others can only read.
        ```
        

**Changing Ownership**:

- To change the owner of a file or directory, use the **`chown`** command:
    
    ```bash
    chown new_owner:group file_or_directory
    ```
    
- For example, to change the owner of a file named **`file.txt`** to **`newuser`** and set the group to **`newgroup`**:
    
    ```bash
    chown newuser:newgroup file.txt
    ```
    

**Changing Group Ownership**:

- To change the group ownership of a file or directory, use the **`chgrp`** command:
    
    ```bash
    chgrp new_group file_or_directory
    ```
    
- For example, to change the group of **`file.txt`** to **`newgroup`**:
    
    ```bash
    chgrp newgroup file.txt
    ```
    

### File Links

---

1. **Symbolic Links (Symlinks)**:
    - Symbolic links are references to other files or directories by their paths.
    - They act as pointers or shortcuts to the target file or directory.
    - They can span across different file systems and even point to non-existent targets.
    - Symbolic links can be easily identified as separate files and can link to directories.
2. **Hard Links**:
    - Hard links are multiple directory entries pointing to the same inode (data structure) on disk.
    - They essentially represent different names for the same file or directory.
    - Hard links must reside on the same file system as the target.
    - Deleting one hard link does not affect the data until all hard links to the same inode are removed.

### Giving `sudo` Access to a User

---

1. `su`
2. Enter root password
3. `# echo "student ALL=(ALL) ALL" > /etc/sudoers.d/student"` (student is example username)

# Linux Graphical Interface

---

## **X Window System (X11) X Server:**

The X Server, often referred to as simply "X," is a crucial component of the X Window System (X11), which is a widely used **windowing system and graphical user interface (GUI) for Unix-like operating systems, including Linux**. The X Server is responsible for managing graphical hardware and providing the infrastructure for GUI applications to display graphics on the screen.

The X server uses `/etc/X11/xorg.conf` as its configuration file

## **Responsibilities of a Linux Display Manager:**

1. **User Authentication:** One of the primary responsibilities of a display manager is to handle user authentication. It presents a graphical login screen to users, where they can enter their usernames and passwords to access the system. After users submit their credentials, the display manager verifies their authenticity.
2. **Session Management:** Once a user is authenticated, the display manager manages the user's session. It sets up the user's environment, loads the chosen desktop environment or window manager, and initializes various components needed for the graphical desktop experience.
3. **User Selection:** Display managers often allow multiple users to have their own login sessions on the same system. Users can select their usernames from a list or enter them manually, depending on the configuration.
4. **Accessibility Features:** Many display managers include accessibility features to assist users with disabilities. These features may include screen magnification, on-screen keyboards, and options for adjusting font size and contrast.
5. **Customization:** Display managers offer options for customization. System administrators and users can configure the login screen's appearance, including background images, themes, and login prompt settings.
6. **User Session Termination:** When a user logs out or the session ends, the display manager is responsible for terminating the user's graphical session gracefully and returning to the login screen.
7. **Session Locking:** Display managers may provide the option to lock a user's session, requiring the entry of a password to unlock and resume the session without logging out.
8. **Integration with X Server:** In systems using the X Window System (X11), the display manager interacts with the X server to provide the graphical interface. It manages the communication between user input devices (e.g., keyboard, mouse) and the X server.
9. **Management of Screen Resolution:** Display managers often allow users to select their preferred screen resolution and other display settings when logging in.
10. **Error Handling:** If authentication fails or other errors occur during the login process, the display manager handles error messages and prompts users to retry or take appropriate action.

Popular display managers for Linux include GDM (GNOME Display Manager), LightDM, SDDM (Simple Desktop Display Manager), and more.

# Citations and Thank Yous

---

These notes were made possible by this wonderful course on youtube (and some help formatting/paraphrasing by ChatGPT):

[https://youtu.be/sWbUDq4S6Y8?si=2opCZxYJsvjQ4Spm](https://youtu.be/sWbUDq4S6Y8?si=2opCZxYJsvjQ4Spm)
