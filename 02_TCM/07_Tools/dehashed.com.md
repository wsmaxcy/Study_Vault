## Overview
Dehashed.com is a comprehensive search engine for breached data. It allows users to search across multiple data breaches to find compromised information such as email addresses, usernames, passwords, and other personal details. It is a valuable tool for security professionals, researchers, and individuals to monitor and investigate data breaches.

## Features
- Search for compromised email addresses, usernames, passwords, and more
- Extensive database of data breaches
- Provides detailed information about the source and nature of the breach
- API access for automated searching and integration with other tools
- Monitoring and alerting services for new breaches

## Website
- [Dehashed.com](https://www.dehashed.com/)

## Usage

### Web Interface
1. Visit [Dehashed.com](https://www.dehashed.com/)
2. Enter the email address, username, or other search criteria in the search bar
3. Click on the search button to find compromised information
4. Review the results to understand the nature and extent of the breach

### API
Dehashed.com provides an API for programmatic access to its database. Below are examples of how to use the API.

#### API Key
You need an API key to use Dehashed.com's API. You can find your API key in your account settings on the Dehashed.com website.

### Search for Compromised Information
To search for compromised information using the API:
```sh
curl -H "Authorization: Bearer YOUR_API_KEY" \
"https://api.dehashed.com/search?query=email@example.com"
```

### Get Breach Details
To get detailed information about a specific breach:
```sh
curl -H "Authorization: Bearer YOUR_API_KEY" \
"https://api.dehashed.com/breach?name=breach_name"
```

## Best Practices
- **Regularly monitor your email addresses and usernames:** Use Dehashed.com to regularly check if your email addresses, usernames, or other sensitive information have been compromised in a data breach.
- **Integrate with security tools:** Use the API to integrate Dehashed.com with your security tools and workflows to automate the monitoring process.
- **Act on breach information:** If you find that your information has been compromised, take immediate steps to secure your accounts, such as changing passwords and enabling two-factor authentication.

## References
- [Dehashed.com Website](https://www.dehashed.com/)
- [Dehashed.com API Documentation](https://www.dehashed.com/docs)
