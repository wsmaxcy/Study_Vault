## Overview
SQLMap is an open-source penetration testing tool that automates the process of detecting and exploiting SQL injection vulnerabilities in web applications. It comes with a powerful detection engine, a variety of niche features for penetration testers, and a wide range of switches and options to customize its behavior. SQLMap is a preferred tool for cybersecurity professionals and ethical hackers to identify and exploit SQL injection vulnerabilities to test the security of web applications.

## Features
- **Automatic SQL Injection Detection:** Scans web applications for SQL injection vulnerabilities and determines the type of injection.
- **Database Fingerprinting:** Identifies the type of database management system (DBMS) and its version.
- **Data Extraction:** Extracts data such as tables, columns, and user credentials from the database.
- **Customizable Payloads:** Supports crafting custom SQL injection payloads for targeted attacks.
- **Bypass Web Application Firewalls (WAFs):** Includes techniques to evade WAFs and intrusion detection systems (IDS).
- **Post-Exploitation:** Offers features for database takeover, such as retrieving OS shell, downloading/uploading files, and more.

## Website
- [SQLMap Official Website](https://sqlmap.org/)

## Installation

### On Unix-based systems (Linux/macOS):
1. **Install SQLMap:**
   - On Debian-based systems:
```sh
sudo apt-get install sqlmap
```
   - On Red Hat-based systems:
```sh
sudo yum install sqlmap
```
   - On macOS using Homebrew:
```sh
brew install sqlmap
```

2. **Clone from GitHub:**
   - To get the latest version:
```sh
git clone --depth 1 https://github.com/sqlmapproject/sqlmap.git sqlmap-dev
cd sqlmap-dev
```

### On Windows:
1. **Download the Binary:**
   - Download the latest Windows binaries from the [SQLMap Download Page](https://sqlmap.org/).

2. **Extract and Run:**
   - Extract the downloaded files and run `sqlmap.py` from the command prompt using Python.

## Basic Usage
SQLMap is run from the command line interface (CLI). Here are some common commands and usage examples:

### Basic SQL Injection Test
To test a URL for SQL injection vulnerabilities:
```sh
python sqlmap.py -u "http://example.com/vulnerable.php?id=1"
```

### Specifying HTTP Request Methods
To specify an HTTP POST request method:
```sh
python sqlmap.py -u "http://example.com/vulnerable.php" --data="id=1"
```

### Database Enumeration
To enumerate the databases on the target system:
```sh
python sqlmap.py -u "http://example.com/vulnerable.php?id=1" --dbs
```

### Dumping Database Tables
To list tables from a specific database:
```sh
python sqlmap.py -u "http://example.com/vulnerable.php?id=1" -D database_name --tables
```

### Dumping Table Data
To dump data from a specific table:
```sh
python sqlmap.py -u "http://example.com/vulnerable.php?id=1" -D database_name -T table_name --dump
```

### Bypassing WAFs
To bypass Web Application Firewalls (WAFs) using tamper scripts:
```sh
python sqlmap.py -u "http://example.com/vulnerable.php?id=1" --tamper=space2comment
```

### Saving Output to a File
To save the output of SQLMap to a file for later analysis:
```sh
python sqlmap.py -u "http://example.com/vulnerable.php?id=1" --output-dir=/path/to/output/
```

## Key Features and Options

### Enumeration Options
SQLMap supports a variety of enumeration options for extracting information from the database:
- **`--dbs`**: Enumerates databases.
- **`--tables`**: Enumerates tables in a specified database.
- **`--columns`**: Enumerates columns in a specified table.
- **`--dump`**: Dumps all entries of a specified table.

### SQL Injection Techniques
SQLMap can use different types of SQL injection techniques:
- **Boolean-based blind**: Uses the page's true/false response to infer data.
- **Time-based blind**: Uses time delays to infer data.
- **Error-based**: Exploits error messages returned by the database.
- **Union-based**: Uses the UNION SQL operator to extract data.
- **Stacked queries**: Executes multiple queries in a single statement.

### Automated Database Takeover
SQLMap offers automated methods for database takeover:
- **`--os-shell`**: Retrieves an operating system shell on the target machine.
- **`--os-pwn`**: Uploads and executes Meterpreter or VNC payloads using Metasploit.
- **`--file-read`**: Reads files from the file system on the target machine.
- **`--file-write`**: Writes files to the file system on the target machine.

### Customizing Requests
SQLMap provides options to customize HTTP requests:
- **`--data`**: Specifies POST data for HTTP POST requests.
- **`--cookie`**: Specifies custom cookies for the HTTP request.
- **`--user-agent`**: Sets a custom User-Agent string.
- **`--referer`**: Sets a custom HTTP Referer header.

### Evading Detection
To evade detection from IDS and WAFs:
- **Tamper Scripts**: SQLMap includes several tamper scripts to modify payloads and bypass WAFs:
```sh
python sqlmap.py -u "http://example.com/vulnerable.php?id=1" --tamper=space2comment
```
- **Random User-Agents**: Automatically randomizes the User-Agent header to evade detection:
```sh
python sqlmap.py -u "http://example.com/vulnerable.php?id=1" --random-agent
```

## Tools for Exploiting and Defending Using SQLMap

- **Automated SQL Injection Testing:** Use SQLMap to quickly identify and exploit SQL injection vulnerabilities in web applications.
- **Database Enumeration:** Extract detailed information about the database schema, tables, columns, and data.
- **Penetration Testing:** Use SQLMap during penetration tests to validate the security of web applications against SQL injection attacks.
- **Post-Exploitation:** Automate tasks such as database takeover and data exfiltration once access to the database is obtained.

## Best Practices
- **Test Safely:** Always ensure that you have authorization before testing for vulnerabilities with SQLMap.
- **Use Non-Intrusive Techniques:** Start with non-intrusive techniques to avoid detection and potential disruption of services.
- **Combine with Manual Testing:** Use SQLMap in combination with manual testing techniques for a thorough assessment.
- **Leverage Tamper Scripts:** Utilize tamper scripts to bypass WAFs and IDS, but be aware of their limitations.
- **Stay Updated:** Regularly update SQLMap to benefit from new features and improvements.
- **Combine with Other Tools:** Use SQLMap alongside other web vulnerability scanners like [[Burp Suite]], [[OWASP ZAP]], and [[Nmap]] for comprehensive assessments.

## References
- [SQLMap Official Website](https://sqlmap.org/)
- [SQLMap GitHub Repository](https://github.com/sqlmapproject/sqlmap)
- [SQLMap User Manual](https://github.com/sqlmapproject/sqlmap/wiki)
- [OWASP Testing Guide for SQL Injection](https://owasp.org/www-project-web-security-testing-guide/latest/4-Web_Application_Security_Testing/07-Testing_for_Weaknesses_in_Authentication/01-Testing_for_SQL_Injection)

