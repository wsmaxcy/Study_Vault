## Overview
FoxyProxy is a browser extension that simplifies the process of configuring proxies for Firefox. It allows users to easily switch between multiple proxy servers and direct internet connections without having to constantly change browser settings. FoxyProxy also supports patterns and wildcards to automate proxy switching based on URL rules.

## Features
- **Easy Proxy Management:** Quickly switch between multiple proxy servers with a few clicks.
- **Automated Proxy Switching:** Use patterns and wildcards to automatically switch proxies based on URL rules.
- **Support for Multiple Protocols:** Works with HTTP, HTTPS, SOCKS4, and SOCKS5 proxies.
- **Proxy Import/Export:** Import and export proxy settings for easy sharing and backup.
- **Bypass List:** Define a list of sites that should bypass the proxy and connect directly.

## Website
- [FoxyProxy](https://getfoxyproxy.org/)

## Installation

### On Firefox:
1. **Install FoxyProxy:**
   - Visit the [FoxyProxy Addon Page](https://addons.mozilla.org/en-US/firefox/addon/foxyproxy-standard/) on the Firefox Add-ons website.

2. **Add to Firefox:**
   - Click the "Add to Firefox" button, then confirm by clicking "Add" in the prompt.

3. **Restart Firefox:**
   - Restart Firefox to complete the installation.

## Basic Usage
Once installed, FoxyProxy can be configured to manage proxies and automate switching based on your needs.

### Configure a New Proxy
1. **Open FoxyProxy Settings:**
   - Click on the FoxyProxy icon in the toolbar, then select "Options" to open the settings page.

2. **Add New Proxy:**
   - Click the "Add New Proxy" button.
   - Enter the proxy details, such as IP address, port, and protocol (HTTP, HTTPS, SOCKS4, SOCKS5).
   - Optionally, enter a username and password if the proxy requires authentication.

3. **Save Settings:**
   - Click "Save" to add the proxy to your list.

### Switching Between Proxies
1. **Switch Proxy Mode:**
   - Click on the FoxyProxy icon in the toolbar.
   - Select the desired proxy from the list to activate it.

2. **Set to Use No Proxy:**
   - Select "Disable FoxyProxy" or "Use Firefox Settings" to disable proxies and use a direct connection.

### Automating Proxy Switching
1. **Set Patterns and Rules:**
   - In the FoxyProxy settings, select the proxy you want to configure.
   - Click "Patterns" to add URL patterns or wildcards.
   - Define rules such as URLs that start with `https://intranet.example.com` should use a specific proxy.

2. **Save Patterns:**
   - Click "Save" to apply the patterns to the selected proxy.

### Bypass Proxy for Specific Sites
1. **Configure Bypass List:**
   - In the FoxyProxy settings, select "General" settings.
   - Enter URLs or IP addresses in the "Bypass proxies for these addresses" field.

2. **Save Bypass List:**
   - Click "Save" to update the settings.

## Advanced Options
FoxyProxy offers several advanced options for more specific use cases:

### Import/Export Proxy Settings
1. **Export Settings:**
   - Go to FoxyProxy settings, click "Import/Export", and choose "Export settings to a file".

2. **Import Settings:**
   - Click "Import/Export" in FoxyProxy settings, then select "Import settings from a file" and upload the file.

### Proxy Modes
- **Use Proxy for All URLs:** Use the selected proxy for all browsing activities.
- **Use Proxies Based on Their Predefined Patterns and Priorities:** Automatically switch proxies based on the configured patterns and rules.

### Using with SSH Tunnel
1. **Set Up SSH Tunnel:**
   - Use SSH to create a SOCKS proxy: 
```sh
ssh -D 8080 user@remote_host
```

2. **Configure FoxyProxy:**
   - Add a new SOCKS5 proxy with IP `127.0.0.1` and port `8080`.

## Best Practices
- **Secure Your Proxies:** Use proxies from trusted providers and avoid using public proxies for sensitive activities.
- **Use Patterns Wisely:** Configure patterns to automate proxy switching based on trusted sites and avoid routing sensitive data through untrusted proxies.
- **Regularly Update FoxyProxy:** Ensure you are using the latest version of FoxyProxy to benefit from security updates and new features.
- **Combine with Other Tools:** Use FoxyProxy in combination with other tools like [[Burp Suite]] or [[Wireshark]] for advanced network analysis and penetration testing.

## References
- [FoxyProxy Official Website](https://getfoxyproxy.org/)
- [FoxyProxy Addon Page](https://addons.mozilla.org/en-US/firefox/addon/foxyproxy-standard/)
- [FoxyProxy Documentation](https://help.getfoxyproxy.org/)

