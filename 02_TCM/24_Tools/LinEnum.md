## Overview
LinEnum is a shell script designed to automate the process of Linux privilege escalation enumeration. It performs an extensive range of checks on the target system to gather valuable information that can be used to escalate privileges. LinEnum is a powerful tool for penetration testers and red teams during the post-exploitation phase to identify potential vectors for privilege escalation.

## Features
- **System Enumeration:** Collects detailed information about the system, including kernel version, network configuration, and user accounts.
- **Permission Checks:** Analyzes file and directory permissions to identify misconfigurations.
- **Service Enumeration:** Identifies running services, scheduled tasks, and cron jobs.
- **SUID/SGID Files:** Enumerates files with SUID/SGID permissions that could be exploited for privilege escalation.
- **Writable Files:** Lists writable files and directories that could be leveraged by an attacker.

## Website
- [LinEnum GitHub Repository](https://github.com/rebootuser/LinEnum)

## Installation

### Download LinEnum:
1. **Clone the Repository:**
   ```sh
   git clone https://github.com/rebootuser/LinEnum.git
   cd LinEnum
   ```

2. **Download Directly:**
   - Use `wget` or `curl` to download `LinEnum.sh` directly:
   ```sh
   wget https://raw.githubusercontent.com/rebootuser/LinEnum/master/LinEnum.sh
   ```
   or
   ```sh
   curl -O https://raw.githubusercontent.com/rebootuser/LinEnum/master/LinEnum.sh
   ```

3. **Make the Script Executable:**
   ```sh
   chmod +x LinEnum.sh
   ```

## Basic Usage
LinEnum is run from the command line. Here are some common commands and usage examples:

### Run LinEnum
To run the script with default settings:
```sh
./LinEnum.sh
```

### Save Output to a File
To save the output of LinEnum to a file for later analysis:
```sh
./LinEnum.sh > linenum_output.txt
```

### Running with Verbose Output
To run LinEnum with verbose output to see all checks being performed:
```sh
./LinEnum.sh -v
```

### Running with Thorough Checks
To run LinEnum with thorough checks, which includes more in-depth enumeration:
```sh
./LinEnum.sh -t
```

## Advanced Options
LinEnum offers several options for more specific use cases:

### Running with Specified Output
To save output to a specified file:
```sh
./LinEnum.sh -o /path/to/output.txt
```

### Suppressing Output Colors
To run LinEnum without color codes (useful for saving plain-text output):
```sh
./LinEnum.sh -n
```

### Display Help
To display the help menu with all options:
```sh
./LinEnum.sh -h
```

## Key Enumeration Areas

### Kernel and System Information
- **Kernel Version:** Checks for known vulnerable kernel versions.
- **OS Version:** Identifies the operating system version for further enumeration.

### User and Group Information
- **Current User Privileges:** Displays the privileges of the current user.
- **User and Group Enumeration:** Lists all users and groups on the system.

### SUID/SGID Files
- **Check for Misconfigurations:** Identifies files with SUID/SGID permissions that could be exploited for privilege escalation.

### Writable Directories and Files
- **World-Writable Files:** Lists files that are world-writable and could be modified by a low-privileged user.
- **Writable Directories:** Identifies directories that a user can write to and potentially misuse.

### Running Processes and Services
- **Service Enumeration:** Lists running services and their associated privileges.
- **Process Enumeration:** Displays currently running processes and their owners.

### Scheduled Tasks and Cron Jobs
- **Cron Jobs:** Lists scheduled cron jobs and their associated scripts or commands.
- **Anomalies:** Identifies cron jobs running with elevated privileges or pointing to writable scripts.

## Tools for Post-Exploitation Using LinEnum

- **Privilege Escalation:** Use LinEnum to identify potential vectors for privilege escalation on a compromised Linux system.
- **System Hardening:** Administrators can use LinEnum to audit systems and identify security misconfigurations or vulnerabilities.
- **Reconnaissance:** Gather detailed information about the target environment for further exploitation.

## Best Practices
- **Run with Limited Privileges First:** Start by running LinEnum as a non-root user to identify potential privilege escalation paths.
- **Analyze Output Carefully:** Review the output to prioritize critical findings and determine the most effective escalation method.
- **Use in Combination with Other Tools:** Use LinEnum alongside other enumeration tools like [[linpeas.sh]], [[Linux Exploit Suggester]], and [[pspy]] for comprehensive assessments.
- **Keep LinEnum Updated:** Regularly update LinEnum to benefit from new checks and features.

## References
- [LinEnum GitHub Repository](https://github.com/rebootuser/LinEnum)
- [Linux Privilege Escalation Techniques](https://www.hackingarticles.in/linux-privilege-escalation/)
- [LinEnum Usage Guide](https://github.com/rebootuser/LinEnum#usage)

