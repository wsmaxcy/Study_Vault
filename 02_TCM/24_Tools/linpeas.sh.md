## Overview
`linpeas.sh` is a script part of the PEASS (Privilege Escalation Awesome Scripts SUITE) that helps in finding potential privilege escalation vectors on Linux/Unix systems. It performs a comprehensive scan of the system for security misconfigurations, outdated software, and common vulnerabilities that could allow attackers to escalate privileges.

## Features
- **Privilege Escalation Checks:** Scans for potential privilege escalation vectors such as writable files, misconfigured binaries, and vulnerable services.
- **Configuration Analysis:** Examines system configuration files for misconfigurations.
- **User Enumeration:** Gathers detailed information about users, groups, and sudo privileges.
- **Service Enumeration:** Identifies running services, installed packages, and their versions.
- **Color-Coded Output:** Provides a color-coded output to easily identify issues that need attention.
- **Quick Execution:** Lightweight script that can be run quickly to gather essential information.

## Website
- [PEASS GitHub Repository](https://github.com/carlospolop/PEASS-ng)

## Installation

### Download linpeas.sh:
1. **Clone the PEASS-ng Repository:**
   ```sh
   git clone https://github.com/carlospolop/PEASS-ng.git
   cd PEASS-ng/linPEAS
   ```

2. **Download Directly:**
   - Use `wget` or `curl` to download `linpeas.sh` directly:
   ```sh
   wget https://github.com/carlospolop/PEASS-ng/releases/latest/download/linpeas.sh
   ```
   or
   ```sh
   curl -L https://github.com/carlospolop/PEASS-ng/releases/latest/download/linpeas.sh -o linpeas.sh
   ```

3. **Make the Script Executable:**
   ```sh
   chmod +x linpeas.sh
   ```

## Basic Usage
`linpeas.sh` is run from the command line. Here are some common commands and usage examples:

### Run linpeas.sh
To run the script with default settings:
```sh
./linpeas.sh
```

### Save Output to a File
To save the output of `linpeas.sh` to a file for later analysis:
```sh
./linpeas.sh > linpeas_output.txt
```

### Running with Less Output (Speed Mode)
To run `linpeas.sh` with reduced output for quicker execution:
```sh
./linpeas.sh -s
```

### Running with Verbose Output
To run `linpeas.sh` with verbose output to see all checks and commands executed:
```sh
./linpeas.sh -a
```

## Advanced Options
`linpeas.sh` offers several options for more specific use cases:

### Running a Specific Section
To run only a specific section (e.g., processes):
```sh
./linpeas.sh -p
```

### Display Help
To display the help menu with all options:
```sh
./linpeas.sh -h
```

### Suppressing Output Colors
To run `linpeas.sh` without color codes (useful for saving plain-text output):
```sh
./linpeas.sh -nocolor
```

## Best Practices
- **Run as a Limited User:** For best results, run `linpeas.sh` as a non-root user to identify privilege escalation paths.
- **Analyze Output Carefully:** Review the color-coded output to prioritize critical issues marked in red and yellow.
- **Use in Combination with Other Tools:** Use `linpeas.sh` alongside other enumeration tools like [[LinEnum]], [[Linux Exploit Suggester]], and [[pspy]] for comprehensive assessments.
- **Keep Updated:** Regularly update `linpeas.sh` to benefit from new checks and features.

## References
- [PEASS GitHub Repository](https://github.com/carlospolop/PEASS-ng)
- [linpeas.sh Documentation](https://github.com/carlospolop/PEASS-ng/tree/master/linPEAS)
- [PEASS Wiki](https://github.com/carlospolop/PEASS-ng/wiki)

