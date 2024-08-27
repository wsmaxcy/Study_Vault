## Overview
DirBuster is a multi-threaded application designed to brute force directories and files names on web/application servers. It is a powerful tool used by penetration testers to find hidden files and directories on a web server by using a wordlist.

## Features
- **Multi-threaded:** Uses multiple threads to perform fast scans.
- **Custom Wordlists:** Supports custom wordlists for directory and file name brute forcing.
- **Recursive Scanning:** Can recursively scan directories and subdirectories.
- **File Extension Brute Forcing:** Allows brute forcing of multiple file extensions.
- **Error Handling:** Detects and handles various HTTP error codes.
- **Proxy Support:** Supports scanning through a proxy server.

## Website
- [DirBuster GitHub Repository](https://github.com/OWASP/DirBuster)

## Installation

### On Unix-based systems:
1. **Clone Repository:**
```sh
git clone https://github.com/OWASP/DirBuster.git
cd DirBuster
```

2. **Run DirBuster:**
```sh
java -jar DirBuster.jar
```

### On Windows:
1. **Download JAR File:**
   - Visit the [DirBuster GitHub Repository](https://github.com/OWASP/DirBuster) and download the JAR file.

2. **Run DirBuster:**
   - Double-click the JAR file to launch DirBuster.

## Basic Usage
DirBuster is run through its graphical user interface (GUI). Here are some common steps to use DirBuster:

### Setting Up a Scan
1. **Launch DirBuster:**
   - Start DirBuster by running the JAR file.

2. **Set Target URL:**
   - Enter the URL of the target website in the "Target URL" field.

3. **Choose Wordlist:**
   - Select a wordlist to use for brute forcing. You can use the default wordlist or load a custom one.

4. **Configure Scan Options:**
   - Set options such as number of threads, recursion, and file extensions.

5. **Start Scan:**
   - Click the "Start" button to begin the scan.

### Analyzing Results
1. **View Discovered Paths:**
   - As the scan progresses, DirBuster will list discovered directories and files in the results pane.

2. **Check Status Codes:**
   - Review the HTTP status codes to identify valid and interesting paths.

3. **Recursive Scanning:**
   - If recursive scanning is enabled, DirBuster will continue to scan subdirectories.

### Custom Wordlists
To use a custom wordlist:
1. **Load Wordlist:**
   - Click the "Browse" button next to the wordlist field and select your custom wordlist file.

2. **Configure Extensions:**
   - Specify any file extensions to brute force.

## Best Practices
- **Use Relevant Wordlists:** Choose wordlists that are relevant to the target application to increase the chances of finding hidden directories and files.
- **Adjust Threads:** Configure the number of threads based on your network and server capabilities to avoid overloading the server.
- **Analyze Results Carefully:** Not all discovered paths are necessarily interesting or useful. Analyze the results to focus on relevant findings.
- **Combine with Other Tools:** Use DirBuster in combination with other scanning tools like [[Nmap.md|Nmap]] and [[Burp Suite]] for comprehensive assessments.

## References
- [DirBuster GitHub Repository](https://github.com/OWASP/DirBuster)
- [OWASP DirBuster Project Page](https://owasp.org/www-project-dirbuster/)
- [SecTools.org - DirBuster](https://sectools.org/tool/dirbuster/)
