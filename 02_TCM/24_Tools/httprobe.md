## Overview
httprobe is a tool designed to take a list of domains and probe for working HTTP and HTTPS servers. It is useful for quickly finding live web servers from a list of domains or subdomains.

## Features
- Probes for HTTP and HTTPS servers
- Supports custom ports
- Fast and efficient
- Can handle large lists of domains
- Simple command-line interface

## Website
- [httprobe GitHub Repository](https://github.com/tomnomnom/httprobe)

## Installation

### Using Go
1. **Install Go:**
   - Ensure you have Go installed on your system. You can download it from [golang.org](https://golang.org/).

2. **Install httprobe:**
```sh
go install github.com/tomnomnom/httprobe@latest
```

3. **Verify Installation:**
   - Ensure `httprobe` is in your PATH. You can check by running:
```sh
httprobe -h
```

## Basic Usage
httprobe is run from the command line. Here are some common commands:

### Probe for HTTP and HTTPS Servers
```sh
cat domains.txt | httprobe
```

### Probe Custom Ports
You can specify custom ports to probe:
```sh
cat domains.txt | httprobe -p http:8080 -p https:8443
```

### Filter by Response Time
You can filter out slow responses by specifying a timeout:
```sh
cat domains.txt | httprobe -c 50 -t 3000
```
- `-c` specifies the concurrency level (default is 50).
- `-t` specifies the timeout in milliseconds (default is 2000).

### Save Output to a File
```sh
cat domains.txt | httprobe > live_domains.txt
```

## Advanced Options
httprobe offers several options for more advanced usage:

### Using a Different User-Agent
You can specify a custom User-Agent string:
```sh
cat domains.txt | httprobe -p http:8080 -p https:8443 -a "MyCustomUserAgent"
```

### Skip Default Ports
If you want to probe only custom ports and skip the default 80 and 443:
```sh
cat domains.txt | httprobe -p http:8080 -p https:8443 -s
```

## Best Practices
- **Combine with other tools:** Use httprobe in combination with subdomain enumeration tools like `amass` or `sublist3r` to find live servers from discovered subdomains.
- **Adjust concurrency and timeout:** Tweak the concurrency and timeout settings based on your network conditions and the size of your domain list.
- **Regularly update httprobe:** Keep httprobe updated to ensure you have the latest features and bug fixes.

## References
- [httprobe GitHub Repository](https://github.com/tomnomnom/httprobe)
