## Overview
DirSearch is a command-line tool designed for brute-forcing directories and files on web servers to discover hidden content. It's a powerful tool commonly used by penetration testers, security researchers, and bug bounty hunters to identify sensitive directories, configuration files, and other potentially exposed resources on web applications. DirSearch uses a variety of techniques, including dictionary attacks and recursive scanning, to enumerate directories and files that are not publicly listed.

DirSearch is known for its speed, versatility, and support for various HTTP methods and headers, making it a go-to tool for web content discovery.

## Features
- **Recursive Directory Brute-Forcing:** Automatically traverses directories and subdirectories to find hidden content.
- **Multiple HTTP Methods:** Supports GET, POST, HEAD, PUT, DELETE, and other HTTP methods for comprehensive web enumeration.
- **Customizable Wordlists:** Allows users to specify custom wordlists to tailor directory and file enumeration.
- **Output Formatting:** Provides options for outputting results in multiple formats, including plain text, JSON, and CSV.
- **Request Headers and Cookies:** Supports custom HTTP headers and cookies to bypass WAFs and access protected resources.
- **Error and Status Code Filtering:** Filters responses based on HTTP status codes to focus on interesting results.
- **Rate Limiting:** Allows control over the rate of requests to avoid triggering web server defenses.
- **Cross-Platform:** Available on Unix-based systems (Linux, macOS) and Windows.

## Website
- [DirSearch GitHub Repository](https://github.com/maurosoria/dirsearch)

## Installation

### On Unix-based systems (Linux/macOS):

1. **Install via GitHub:**

   - Clone the DirSearch repository from GitHub:

```sh
git clone https://github.com/maurosoria/dirsearch.git
cd dirsearch
```

   - Install the required Python dependencies:

```sh
pip install -r requirements.txt
```

2. **Install via Package Manager (Linux):**

   - **On Debian-based systems (if available):**

```sh
sudo apt-get install dirsearch
```

### On Windows:

1. **Install via GitHub:**

   - Ensure Python and pip are installed, then run:

```sh
git clone https://github.com/maurosoria/dirsearch.git
cd dirsearch
pip install -r requirements.txt
```

2. **Run DirSearch:**

   - Use the `python` command to run DirSearch:

```sh
python dirsearch.py
```

## Basic Usage
DirSearch is a command-line tool with various options for directory and file brute-forcing. Here are some common commands and usage examples:

### Basic Directory Brute-Forcing
To brute-force directories and files on a web server:

```sh
python3 dirsearch.py -u http://target.com -w /path/to/wordlist.txt
```

- **`-u http://target.com`**: Specifies the target URL to scan.
- **`-w /path/to/wordlist.txt`**: Specifies the wordlist file for brute-forcing.

### Recursive Directory Brute-Forcing
To perform recursive scanning through all discovered directories:

```sh
python3 dirsearch.py -u http://target.com -w /path/to/wordlist.txt -r
```

- **`-r`**: Enables recursive scanning through directories.

### Filtering Responses by Status Code
To filter responses based on HTTP status codes, for example, showing only 200 OK and 403 Forbidden responses:

```sh
python3 dirsearch.py -u http://target.com -w /path/to/wordlist.txt --status=200,403
```

- **`--status=200,403`**: Shows only responses with 200 or 403 status codes.

### Using Custom HTTP Headers
To use custom HTTP headers, such as cookies or user-agent strings:

```sh
python3 dirsearch.py -u http://target.com -w /path/to/wordlist.txt -H "User-Agent: custom-agent" -H "Cookie: sessionid=abc123"
```

- **`-H`**: Adds custom HTTP headers to the request.

### Output Results to a File
To save results to a file for later analysis:

```sh
python3 dirsearch.py -u http://target.com -w /path/to/wordlist.txt -o results.txt
```

- **`-o results.txt`**: Outputs results to a specified file.

### Rate Limiting Requests
To control the rate of requests to avoid server defenses:

```sh
python3 dirsearch.py -u http://target.com -w /path/to/wordlist.txt --delay=2
```

- **`--delay=2`**: Adds a delay of 2 seconds between each request.

## Key Features and Options

### Recursive Scanning
- **Description:** Automatically traverses directories and subdirectories to find deeper hidden content on the web server.
- **Usage:**
```sh
python3 dirsearch.py -u http://target.com -w /path/to/wordlist.txt -r
```

### Custom HTTP Methods
- **Description:** Supports multiple HTTP methods (GET, POST, PUT, DELETE) for more comprehensive web application enumeration.
- **Usage:**
```sh
python3 dirsearch.py -u http://target.com -w /path/to/wordlist.txt -X POST
```

### Status Code and Error Filtering
- **Description:** Filters responses based on HTTP status codes to focus on potentially interesting results.
- **Usage:**
```sh
python3 dirsearch.py -u http://target.com -w /path/to/wordlist.txt --status=200,403
```

### Custom Wordlists and Encoding
- **Description:** Allows the use of custom wordlists and supports various encoding techniques to bypass web application firewalls and other security mechanisms.
- **Usage:**
```sh
python3 dirsearch.py -u http://target.com -w /path/to/wordlist.txt --encoding=base64
```

### Advanced Output Options
- **Description:** Outputs results in various formats, including plain text, JSON, and CSV, for easy analysis and documentation.
- **Usage:**
```sh
python3 dirsearch.py -u http://target.com -w /path/to/wordlist.txt -o results.json --format=json
```

## Tools for Web Application Security Testing Using DirSearch

- **Directory and File Discovery:** Use DirSearch to brute-force directories and files to discover hidden resources, sensitive files, and administrative pages on web servers.
- **Error and Status Code Handling:** Focus on specific HTTP status codes and error messages to identify exposed directories or files with misconfigurations.
- **Authentication and Session Management:** Test authentication mechanisms by brute-forcing directories and files that might contain authentication endpoints or session management issues.
- **Web Application Hardening:** Assess web servers for potential exposures and hidden content that could be exploited by attackers, aiding in web application hardening.
- **Fuzzing and Filter Bypass:** Use custom payloads and encoding techniques to bypass web application firewalls and filters for comprehensive testing.

## Best Practices
- **Use DirSearch Responsibly:** Always ensure that you have proper authorization before using DirSearch to perform brute-force attacks on web applications.
- **Stay Within Legal Boundaries:** Be aware of the legal implications of using directory brute-forcing tools and ensure compliance with local laws and regulations.
- **Limit Scope and Impact:** Use specific URLs and parameters to limit the scope of brute-forcing and avoid overloading the target server with excessive requests.
- **Combine with Other Tools:** Use DirSearch alongside other web application security tools like [[Wfuzz]], [[Burp Suite]], and [[OWASP ZAP]] for comprehensive assessments.
- **Keep DirSearch Updated:** Regularly update DirSearch to benefit from the latest features, security enhancements, and bug fixes.

## References
- [DirSearch GitHub Repository](https://github.com/maurosoria/dirsearch)
- [DirSearch Documentation](https://github.com/maurosoria/dirsearch#readme)
- [Web Directory Bruteforcing with DirSearch](https://null-byte.wonderhowto.com/how-to/bruteforce-web-directories-hidden-files-with-dirsearch-0187262/)
- [Advanced Techniques for Directory Bruteforcing](https://www.hackingarticles.in/advanced-web-directory-bruteforcing-using-dirsearch/)
- [DirSearch Cheat Sheet](https://www.sans.org/posters/dirsearch-cheat-sheet/)

