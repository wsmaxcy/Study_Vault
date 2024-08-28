## Overview
Wfuzz is a versatile web application brute-forcing tool designed for fuzzing web applications to discover hidden resources, parameters, directories, files, and more. It is commonly used by penetration testers, security researchers, and bug bounty hunters to find vulnerabilities in web applications by automating the process of inputting multiple payloads and analyzing the output responses.

Wfuzz is highly customizable and can be integrated with wordlists, encoding techniques, and different HTTP methods to simulate a wide range of attack scenarios.

## Features
- **Directory and File Fuzzing:** Brute-forces directories and files on web servers to discover hidden content and administrative interfaces.
- **Parameter and Data Fuzzing:** Tests web application parameters for vulnerabilities such as SQL injection, XSS, and LFI/RFI.
- **Customizable Payloads:** Supports custom payloads, allowing users to specify input data for fuzzing.
- **Support for Various HTTP Methods:** Fuzzes web applications using GET, POST, PUT, DELETE, and other HTTP methods.
- **Advanced Response Analysis:** Provides options to analyze responses based on status codes, response size, word count, and regex patterns.
- **Encoding and Decoding Support:** Supports payload encoding techniques, such as Base64 and URL encoding, to bypass web application filters.
- **Cross-Platform:** Available on Unix-based systems (Linux, macOS) and Windows.

## Website
- [Wfuzz GitHub Repository](https://github.com/xmendez/wfuzz)

## Installation

### On Unix-based systems (Linux/macOS):

1. **Install Wfuzz via Package Manager:**

   - **On Debian-based systems:**

   ```sh
   sudo apt-get install wfuzz
   ```

   - **On macOS using Homebrew:**

   ```sh
   brew install wfuzz
   ```

2. **Install via pip:**

   - If you have Python and pip installed, you can install Wfuzz using pip:

```sh
pip install wfuzz
```

3. **Build from Source:**

   - Clone the Wfuzz repository from GitHub:

```sh
git clone https://github.com/xmendez/wfuzz.git
cd wfuzz
python setup.py install
```

### On Windows:

1. **Install via pip:**

   - Ensure Python and pip are installed, then run:

```sh
pip install wfuzz
```

2. **Build from Source in Windows Environment:**

   - Follow the Unix-based installation steps within a Windows command prompt or PowerShell.

## Basic Usage
Wfuzz is a command-line tool with various options and filters. Here are some common commands and usage examples:

### Fuzzing for Hidden Directories and Files
To discover hidden directories and files on a web server:

```sh
wfuzz -c -w /path/to/wordlist.txt --hc 404 http://target.com/FUZZ
```

- **`-c`**: Enables colorized output.
- **`-w /path/to/wordlist.txt`**: Specifies the wordlist file for fuzzing.
- **`--hc 404`**: Hides responses with a 404 status code.
- **`http://target.com/FUZZ`**: The URL to fuzz, with `FUZZ` as the placeholder.

### Fuzzing GET Parameters
To fuzz a GET parameter for SQL injection vulnerabilities:

```sh
wfuzz -c -w /path/to/payloads.txt -u "http://target.com/page.php?id=FUZZ"
```

- **`-u`**: Specifies the URL with `FUZZ` as the placeholder for the parameter value.

### Fuzzing POST Data
To fuzz POST data for vulnerabilities:

```sh
wfuzz -c -w /path/to/payloads.txt -d "username=FUZZ&password=FUZZ" http://target.com/login.php
```

- **`-d`**: Specifies the POST data with `FUZZ` placeholders.

### Filtering Responses by Status Code
To filter responses by status code, for example, showing only 200 OK responses:

```sh
wfuzz -c -w /path/to/wordlist.txt --sc 200 http://target.com/FUZZ
```

- **`--sc 200`**: Shows only responses with a 200 status code.

### Using Multiple Wordlists
To use multiple wordlists for fuzzing:

```sh
wfuzz -c -w /path/to/usernames.txt -w /path/to/passwords.txt -d "username=FUZZ1&password=FUZZ2" http://target.com/login.php
```

- **`FUZZ1`** and **`FUZZ2`** are placeholders for the first and second wordlists, respectively.

## Key Features and Options

### Directory and File Fuzzing
- **Description:** Brute-forces web directories and files to find hidden resources, sensitive files, and administrative pages.
- **Usage:**
```sh
wfuzz -c -w /path/to/wordlist.txt --hc 404 http://target.com/FUZZ
```

### Parameter and Data Fuzzing
- **Description:** Tests web application parameters for vulnerabilities such as SQL injection, XSS, and LFI/RFI by fuzzing input data.
- **Usage:**
```sh
wfuzz -c -w /path/to/payloads.txt -u "http://target.com/page.php?id=FUZZ"
```

### Custom Payloads and Encoding
- **Description:** Allows the use of custom payloads and encoding techniques to bypass web application filters and WAFs.
- **Usage:**
```sh
wfuzz -c -w /path/to/payloads.txt --hc 404 --hh 0 --hs "Invalid" --hw 0 --hc 403 http://target.com/FUZZ
```

### HTTP Methods Support
- **Description:** Supports various HTTP methods (GET, POST, PUT, DELETE) to simulate different types of web requests.
- **Usage:**
```sh
wfuzz -c -w /path/to/payloads.txt -X POST -d "param=FUZZ" http://target.com/page.php
```

### Advanced Response Analysis
- **Description:** Filters and analyzes responses based on status codes, response size, word count, and regex patterns to identify interesting results.
- **Usage:**
```sh
wfuzz -c -w /path/to/wordlist.txt --sc 200 --r "admin" http://target.com/FUZZ
```

## Tools for Web Application Security Testing Using Wfuzz

- **Directory and File Discovery:** Use Wfuzz to brute-force web directories and files to discover hidden content and administrative interfaces on web servers.
- **Vulnerability Testing:** Fuzz web application parameters for vulnerabilities such as SQL injection, cross-site scripting (XSS), and file inclusion.
- **Authentication Testing:** Test login pages by fuzzing usernames and passwords with multiple wordlists to perform brute-force attacks.
- **Filter Evasion:** Use encoding and custom payloads to bypass web application firewalls (WAFs) and other security controls.
- **Automation of Repeated Tasks:** Automate repetitive tasks like parameter fuzzing and directory brute-forcing during penetration tests and bug bounty hunts.

## Best Practices
- **Use Wfuzz Responsibly:** Always ensure that you have proper authorization before using Wfuzz to perform fuzzing and brute-force attacks on web applications.
- **Stay Within Legal Boundaries:** Be aware of the legal implications of using fuzzing tools and ensure compliance with local laws and regulations.
- **Limit Scope and Impact:** Use specific URLs and parameters to limit the scope of fuzzing and avoid overloading the target server with excessive requests.
- **Combine with Other Tools:** Use Wfuzz alongside other web application security tools like [[Burp Suite]], [[OWASP ZAP]], and [[Dirbuster]] for comprehensive assessments.
- **Keep Wfuzz Updated:** Regularly update Wfuzz to benefit from the latest features, security enhancements, and bug fixes.

## References
- [Wfuzz GitHub Repository](https://github.com/xmendez/wfuzz)
- [Wfuzz Documentation](https://wfuzz.readthedocs.io/)
- [Fuzzing Web Applications with Wfuzz](https://null-byte.wonderhowto.com/how-to/fuzz-web-servers-and-applications-with-wfuzz-0172771/)
- [Advanced Web Fuzzing Techniques with Wfuzz](https://www.hackingarticles.in/advanced-web-fuzzing-techniques-with-wfuzz/)
- [Wfuzz Cheat Sheet](https://www.sans.org/posters/wfuzz-cheat-sheet/)

