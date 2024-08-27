## Overview
`pspy` is a powerful command-line tool designed to monitor and identify processes without requiring root privileges on a Linux system. It is particularly useful for discovering privilege escalation vectors by observing running processes and understanding what is happening on a system in real-time. `pspy` allows penetration testers and red team operators to detect automated tasks, cron jobs, and other periodic processes that may be exploited for privilege escalation.

## Features
- **No Root Required:** Runs without needing root privileges or installation, making it ideal for use on compromised systems.
- **Process Monitoring:** Observes currently running processes and new process executions.
- **Command Execution Tracking:** Tracks commands executed by users and services, including those executed by cron jobs or other automated scripts.
- **Filter Capabilities:** Allows filtering of output to focus on specific processes or patterns.
- **Static Binary:** No dependencies are required, and the binary can be run directly on the target system.

## Website
- [pspy GitHub Repository](https://github.com/DominicBreuker/pspy)

## Installation

### Download pspy:
1. **Clone the Repository:**
   ```sh
   git clone https://github.com/DominicBreuker/pspy.git
   cd pspy
   ```

2. **Download Precompiled Binary:**
   - Use `wget` or `curl` to download a precompiled binary directly:
   ```sh
   wget https://github.com/DominicBreuker/pspy/releases/download/v1.2.1/pspy64
   ```
   or
   ```sh
   curl -LO https://github.com/DominicBreuker/pspy/releases/download/v1.2.1/pspy64
   ```

3. **Make the Binary Executable:**
   ```sh
   chmod +x pspy64
   ```

## Basic Usage
`pspy` is run from the command line. Here are some common commands and usage examples:

### Run pspy
To run `pspy` with default settings (64-bit binary example):
```sh
./pspy64
```

### Filter Output by User
To filter the output to show processes run by a specific user:
```sh
./pspy64 | grep username
```

### Monitor Cron Jobs
To specifically monitor cron jobs and scheduled tasks:
```sh
./pspy64 | grep cron
```

### Save Output to a File
To save the output of `pspy` to a file for later analysis:
```sh
./pspy64 > pspy_output.txt
```

### Use in Quiet Mode
To run `pspy` in quiet mode, which suppresses some of the output:
```sh
./pspy64 -q
```

## Key Use Cases

### Detecting Automated Tasks
- **Identify Cron Jobs and Timers:** Watch for scheduled tasks that run with elevated privileges or execute scripts that can be modified by a low-privileged user.
- **Detect Periodic Scripts:** Identify scripts and binaries that are executed periodically, which may be exploited for privilege escalation.

### Monitoring Command Execution
- **User Commands:** Observe commands executed by users, which may reveal sensitive information or indicate patterns of behavior.
- **Service Executions:** Monitor commands executed by services or daemons that could be exploited.

### Analyzing System Behavior
- **Track Privileged Processes:** Focus on processes run by root or other high-privilege users to identify potential privilege escalation opportunities.
- **Detect Anomalous Activity:** Monitor for unusual or unauthorized processes that could indicate compromise or malicious activity.

## Advanced Options
`pspy` offers several advanced options for more specific use cases:

### Specify Paths to Monitor
To monitor specific directories or files for execution:
```sh
./pspy64 -p /usr/bin,/usr/local/bin
```

### Adjust Output Format
To change the output format to make it more readable or to tailor it to specific needs:
```sh
./pspy64 -f json
```

### Change Polling Interval
To adjust the polling interval for detecting new processes:
```sh
./pspy64 -i 1000  # Sets the interval to 1000 milliseconds
```

## Tools for Post-Exploitation Using pspy

- **Privilege Escalation:** Use `pspy` to identify cron jobs, scripts, and other automated tasks that can be exploited to elevate privileges.
- **Persistent Backdoors:** Monitor for potential persistence mechanisms used by other attackers or malicious scripts.
- **System Reconnaissance:** Gather intelligence about the target system's behavior, user activity, and scheduled tasks to inform further exploitation.

## Best Practices
- **Run on Compromised Systems:** Use `pspy` on systems where you already have limited access to identify escalation vectors.
- **Filter and Focus:** Utilize filtering options to focus on specific users, directories, or types of processes for more targeted analysis.
- **Keep pspy Updated:** Regularly check for updates to `pspy` to benefit from new features and bug fixes.
- **Combine with Other Tools:** Use `pspy` alongside other enumeration and post-exploitation tools like [[LinEnum]], [[linpeas.sh]], and [[Linux Exploit Suggester]] for comprehensive assessments.
- **Analyze Carefully:** Review the output of `pspy` thoroughly to identify critical findings that may lead to privilege escalation or additional compromises.

## References
- [pspy GitHub Repository](https://github.com/DominicBreuker/pspy)
- [Linux Privilege Escalation Techniques](https://www.hackingarticles.in/linux-privilege-escalation/)
- [Using pspy for Linux Privilege Escalation](https://book.hacktricks.xyz/linux-hardening/privilege-escalation/pspy)

