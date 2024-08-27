## Overview
OWASP Amass is an open-source tool that performs network mapping of attack surfaces and external asset discovery using open-source information gathering and active reconnaissance techniques. It is widely used by security professionals to map out the external infrastructure of organizations.

## Features
- Subdomain enumeration
- DNS information gathering
- Network infrastructure mapping
- Passive and active reconnaissance
- Data source integration (APIs and scraping)
- Visualization of discovered assets

## Website
- [OWASP Amass](https://owasp.org/www-project-amass/)

## Installation

### On Unix-based systems:
1. **Using Homebrew (macOS and Linux):**
```sh
brew install amass
```

2. **Using Snap (Linux):**
```sh
sudo snap install amass
```

3. **Using Go:**
```sh
go get -v github.com/OWASP/Amass/v3/...
```

### On Windows:
1. **Using Scoop:**
```sh
scoop install amass
```

2. **Using Go:**
```sh
go get -v github.com/OWASP/Amass/v3/...
```

## Basic Usage
Amass is run from the command line. Here are some common commands:

### Subdomain Enumeration
```sh
amass enum -d example.com
```

### Passive Enumeration
```sh
amass enum -passive -d example.com
```

### Active Enumeration
```sh
amass enum -active -d example.com
```

### Output Results to a File
```sh
amass enum -d example.com -o output.txt
```

### Visualize the Results
Amass can generate a graph of the discovered network infrastructure using tools like D3.js.

1. **Generate Graph Data:**
```sh
amass viz -d example.com -o amass_graph.dot
```

2. **Convert to HTML (requires D3.js):**
```sh
cat amass_graph.dot | dot -Tsvg -o amass_graph.svg
```

## Advanced Options
Amass offers a wide range of options for more advanced usage. Some key options include:

### Use API Keys
Amass can integrate with various APIs for enhanced data gathering. Configure your API keys in the `config.ini` file.

### Configuration File
You can specify a configuration file with the `-config` option to customize Amass’s behavior.

```sh
amass enum -d example.com -config config.ini
```

### Include All Data Sources
```sh
amass enum -d example.com -src
```

## Best Practices
- **Use API keys for better results:** Integrate Amass with available APIs to get more comprehensive data.
- **Combine passive and active enumeration:** Use both passive and active techniques to discover as much information as possible.
- **Regularly update Amass:** Keep Amass updated to benefit from the latest features and data sources.
- **Visualize results:** Use the visualization capabilities of Amass to better understand the discovered network infrastructure.

## References
- [OWASP Amass GitHub Repository](https://github.com/OWASP/Amass)
- [OWASP Amass Documentation](https://owasp.org/www-project-amass/)
