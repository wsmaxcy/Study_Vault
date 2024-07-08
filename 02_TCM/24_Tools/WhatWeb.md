## Overview
WhatWeb is an open-source web scanner that identifies websites' technologies. It reveals content management systems, frameworks, web servers, and more. WhatWeb is used in security assessments, penetration testing, and competitive analysis to understand the tech stack of a website.

## Features
- Detects web technologies including CMS, frameworks, programming languages, and more
- Supports over 1800 plugins
- Customizable plugin system
- JSON, XML, and other output formats for easy integration with other tools
- Stealth, aggressive, and thorough scanning modes
- Command-line tool with simple syntax

## Website
- [WhatWeb GitHub Repository](https://github.com/urbanadventurer/WhatWeb)

## Installation

### On Unix-based systems:
1. **Using Git:**
   ```sh
   git clone https://github.com/urbanadventurer/WhatWeb.git
   cd WhatWeb
   sudo gem install bundler
   bundle install
   ```

### On Windows:
1. **Using Git:**
   - Install Git for Windows from [git-scm.com](https://git-scm.com/).
   - Install Ruby from [rubyinstaller.org](https://rubyinstaller.org/).
   - Follow Unix-based system steps using Git Bash.

## Basic Usage
WhatWeb is run from the command line. Here are some common commands:

### Basic Scan
```sh
./whatweb example.com
```

### Scan Multiple URLs
You can scan multiple URLs by listing them in a text file and using the `-i` option:
```sh
./whatweb -i urls.txt
```

### Output Formats
WhatWeb supports various output formats such as JSON, XML, and CSV.

#### JSON
```sh
./whatweb -a 3 -l -q --log-json=json_output.json example.com
```

#### XML
```sh
./whatweb -a 3 -l -q --log-xml=xml_output.xml example.com
```

### Verbose Output
To get more detailed output:
```sh
./whatweb -v example.com
```

### Stealth Mode
WhatWeb has a stealth mode to avoid detection by IDS/IPS:
```sh
./whatweb -a 1 example.com
```

### Aggressive Mode
Aggressive mode uses more requests to gather more information:
```sh
./whatweb -a 4 example.com
```

### Custom Plugins
WhatWeb allows you to write custom plugins to extend its capabilities. Plugins are written in Ruby and stored in the `plugins/` directory.

## Advanced Options
WhatWeb offers a wide range of options for more advanced usage:

### Using Proxy
To scan through a proxy server:
```sh
./whatweb -p http://proxyserver:port example.com
```

### Specify User-Agent
To use a custom User-Agent string:
```sh
./whatweb -U "MyCustomUserAgent" example.com
```

### Log Output to File
You can log the output to a file:
```sh
./whatweb -l -o output.txt example.com
```

## Best Practices
- **Use different modes based on need:** Choose the appropriate scanning mode (stealth, aggressive, etc.) based on your requirements and the environment.
- **Combine with other tools:** Use WhatWeb in conjunction with other scanning and enumeration tools for comprehensive assessments.
- **Regularly update WhatWeb:** Keep WhatWeb and its plugins updated to ensure you have the latest detection capabilities.

## References
- [WhatWeb GitHub Repository](https://github.com/urbanadventurer/WhatWeb)
- [WhatWeb Documentation](https://github.com/urbanadventurer/WhatWeb/wiki)
