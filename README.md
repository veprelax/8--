# Completed Independently by Shevchenko Artem, RPZ-23A

# Topic: System Service Data Storage and Network Configuration

## Objective

- To gain practical skills in working with the Bash command-line interface.  
- To become familiar with basic structures for storing system data such as processes, memory, log files, and kernel status messages.  
- To get introduced to the Filesystem Hierarchy Standard (FHS).  
- To understand the basic procedures for network configuration.
---

## Key Terms
1. **Network Configuration Commands**: Tools like `ifconfig`, `ip`, `ping`, and `netstat` for managing and monitoring networks.
2. **Pseudo Filesystems**: Virtual file systems that provide access to system and process information without storing data on physical disks.
3. **FHS (Filesystem Hierarchy Standard)**: A standard outlining the directory structure for Unix-like systems.
4. **Log Files**: Records of system or application events, used for monitoring and troubleshooting
5. **/proc**: A directory holding details about system processes and parameters.
6. **/var/log**: A directory storing log files that track system and application events.
7. **Pseudo Filesystems**: Virtual file systems that provide access to system and process information without storing data on physical disks.
---

## Responses to Questions

### 1. What is a pseudo filesystem, and why is it needed?

Pseudo filesystems are virtual systems that provide real-time access to system states, processes, and hardware details without using physical storage. They are essential for enabling administrators and users to monitor and interact with system information efficiently.

### 2. Why is direct access to the /proc directory uncommon, and how is its data retrieved?

Direct access to /proc is rare because its files contain raw, technical data that can be difficult to interpret without expertise. Instead, users typically rely on commands like `cat`, `grep`, or specialized tools to extract and format information from /proc in a user-friendly way.

### 3. What are the roles of /proc/cmdline, /proc/meminfo, and /proc/modules?

- **/proc/cmdline**: Stores kernel boot parameters, aiding in system diagnostics and configuration.
- **/proc/meminfo**: Provides details on system memory, including total, free, and used amounts.
- **/proc/modules**: Lists active kernel modules, helping identify loaded system components.

### 4. What does the `free` command do?

The `free` command displays information about system RAM, showing total, used, free, and cached memory.

### 5. What are log files used for, and what are some practical examples?

Log files record system and application events, supporting monitoring, troubleshooting, security audits, and change tracking. Examples include:
- Reviewing web server errors in `access.log` or `error.log`.
- Monitoring system activities via `/var/log/syslog`.

### 6. What is the purpose of /var/log/dmesg?

The `/var/log/dmesg` file stores kernel messages generated during system startup and operation, useful for diagnosing hardware issues and monitoring kernel activity.

### 7. What is the role of the FHS?

The Filesystem Hierarchy Standard (FHS) defines a consistent directory structure for Unix-like systems, simplifying system administration, software development, and maintenance.

### 8. What are the primary Linux commands for network management and monitoring?

Key commands include:
- `ifconfig`: Displays and configures network interfaces (older tool).
- `ip`: A modern tool for network management, replacing `ifconfig`.
- `ping`: Tests connectivity to network hosts.
- `netstat`: Shows active connections and network statistics.
- `ss`: A modern alternative to `netstat` for socket and connection details.
- `route`: Manages the routing table.

---

## Command Reference Table

# Linux Command Overview

Below is a restructured table categorizing essential Linux commands by their primary use case. Each command is briefly described to highlight its role in system administration, network management, or file/log operations.

| Category                | Command            | Role in System Operations                                                                 |
|-------------------------|--------------------|-------------------------------------------------------------------------------------------|
| **System Information**  | `su`               | Grants root access by switching to the superuser account.                                  |
|                         | `ls /proc`         | Reveals contents of the `/proc` virtual directory (root privileges needed).                |
|                         | `cat /proc/cmdline`| Outputs the kernel's boot-time parameters.                                                 |
|                         | `cat /proc/meminfo`| Summarizes system memory stats, including used and available RAM.                          |
|                         | `cat /proc/modules`| Identifies active kernel modules loaded in the system.                                     |
|                         | `free`             | Provides a snapshot of memory usage, covering free, used, and cached memory.               |
|                         | `dmesg`            | Shows kernel messages, aiding in hardware and boot issue diagnosis.                        |
|                         | `journalctl`       | Queries and displays logs managed by the systemd journal.                                  |
| **Network Management**  | `ifconfig`         | Manages network interfaces (older tool, superseded by `ip`).                               |
|                         | `ip addr`          | Lists network interfaces and their IP configurations (modern `ifconfig` replacement).      |
|                         | `ping <host>`      | Checks network reachability by sending ICMP packets to a host.                             |
|                         | `netstat`          | Reports network stats, connections, and routing details.                                   |
|                         | `ss`               | Offers detailed socket and connection info (updated alternative to `netstat`).             |
|                         | `route`            | Manages the system's IP routing table for network traffic control.                         |
| **File/Log Operations** | `grep`             | Finds specific patterns in files or command outputs for targeted searches.                 |
|                         | `cat`              | Prints file contents directly to the terminal for quick inspection.                        |


---

# Exploring `cat`, `dig`, and `netstat` Commands

## Using the `cat` Command

The `cat` command (short for "concatenate") is versatile for:
- Viewing file contents.
- Creating new files.
- Combining multiple files.
- Redirecting output to other files.

### Tasks and Examples

Using the cat Command for File Operations

The cat command, short for "concatenate," is a versatile tool in Linux for handling text files. It supports a range of tasks, from creating new files to merging multiple files and formatting output. Below, the primary uses of cat are described to illustrate its role in file manipulation.

To create a new file, cat > file.txt allows users to type text directly into the terminal, saving it to file.txt by pressing Ctrl+D when finished. For viewing file contents, cat file.txt prints the entire file to the terminal, providing a quick way to inspect its data. If copying is needed, cat file.txt > file_copy.txt redirects the contents of file.txt into a new file named file_copy.txt. To combine multiple files, cat file1.txt file2.txt > merged.txt merges the contents of file1.txt and file2.txt into a single file, merged.txt. For enhanced readability, cat -n file.txt adds line numbers to the output, making it easier to reference specific lines. To reveal hidden or non-printable characters, such as carriage returns or tabs, cat -v file.txt displays these symbols explicitly. Finally, to clean up output, cat -s file.txt eliminates consecutive blank lines, resulting in a more compact display.
---

## Using the `dig` Command

The `dig` command queries DNS servers to retrieve domain information.

###Exploring the dig Command for DNS Queries

The dig command, an acronym for Domain Information Groper, is a powerful tool for querying DNS servers to retrieve information about domains. It is widely used in network administration to troubleshoot connectivity issues and inspect domain configurations. Below, the key functionalities of dig are outlined to demonstrate its versatility in fetching DNS-related data.

To obtain a domain’s IP addresses, running dig example.com retrieves the A records, providing the primary network addresses associated with the domain. For a more streamlined output, dig +short example.com delivers only the IP addresses, omitting extraneous details for quick reference. When investigating email configurations, dig example.com MX fetches the mail exchanger (MX) records, identifying the servers responsible for handling the domain’s email. To gather a comprehensive view of a domain’s DNS setup, dig example.com ANY pulls all available DNS records, including A, MX, and others, offering a complete snapshot. Additionally, to query a specific DNS server, dig @8.8.8.8 example.com directs the request to a designated server, such as Google’s public DNS, ensuring precise control over the query source.

---

## Using the `netstat` Command

The `netstat` command provides insights into network connections, ports, and statistics.

### Utilizing the netstat Command for Network Analysis

The netstat command is a fundamental tool in Linux for examining network activity, offering insights into connections, routing, and protocol performance. Its versatility makes it invaluable for network administrators troubleshooting connectivity or monitoring system behavior. Below, the primary applications of netstat are explored to highlight its role in network diagnostics.

To view all network activity, netstat -a generates a comprehensive list of active connections and ports currently listening for incoming requests. For a focused overview of TCP and UDP connections, netstat -tuln presents these details without resolving hostnames, ensuring a concise output ideal for quick checks. To trace which applications are using network resources, netstat -p reveals the processes linked to each connection, aiding in identifying resource-heavy or unexpected activity. For understanding network traffic paths, netstat -r outputs the system’s routing table, showing how data is directed across networks. Lastly, netstat -s provides detailed statistics on protocols like TCP and UDP, enabling analysis of network performance and error rates.
---

## Task Screenshots

![image](https://github.com/user-attachments/assets/1cf5f8f7-4d4c-48a3-80a8-858eb47e8920)
![image](https://github.com/user-attachments/assets/e4bba433-9521-4894-8b5d-264c430ba825)
![image](https://github.com/user-attachments/assets/712e8c5e-68b1-4ea3-bff3-7800a82315bd)
![image](https://github.com/user-attachments/assets/db9a45db-de58-4c53-9e96-d401b927d4d9)
![image](https://github.com/user-attachments/assets/e01898f2-050d-4718-9df6-697ce464c84e)
![image](https://github.com/user-attachments/assets/87540b1b-72ae-4635-b7a0-6c39d3b65bfa)
![image](https://github.com/user-attachments/assets/17b417f7-8ecf-4777-80fd-35f5192103d6)
![image](https://github.com/user-attachments/assets/6e5ff307-dea7-469b-989b-ce2624f01f02)
![image](https://github.com/user-attachments/assets/a29dab1f-e849-46d3-8a57-fc9d6941180d)
![image](https://github.com/user-attachments/assets/36eb132f-2da6-4318-9edb-f6ba3e381409)
![image](https://github.com/user-attachments/assets/a3728bd8-bd80-4350-8bd7-41bec6018511)
![image](https://github.com/user-attachments/assets/0f805305-6015-46ca-a7ad-c4d3c2ecef22)
![image](https://github.com/user-attachments/assets/4014c474-f8e1-4444-9aeb-18932e47ff03)

---

## Conclusion

This lab explored the core functionalities of the `cat`, `dig`, and `netstat` commands. The `cat` command is effective for file manipulation, including viewing, creating, and merging files. The `dig` command supports DNS queries for domain analysis, while `netstat` offers visibility into network connections and ports. These skills provide a strong foundation for advancing in system and network administration.
