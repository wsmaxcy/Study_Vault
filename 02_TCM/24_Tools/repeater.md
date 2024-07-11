## Overview
The Burp Suite Repeater module is a powerful tool within Burp Suite that allows you to manually modify and resend individual HTTP requests. It is commonly used for manual testing, such as probing for vulnerabilities, testing custom payloads, and analyzing server responses in detail.

## Features
- **Manual Request Editing:** Modify and resend HTTP requests to analyze responses.
- **Multiple Tabs:** Open multiple tabs to manage different requests simultaneously.
- **Response Analysis:** View and analyze server responses in detail.
- **Session Handling:** Manage and use session cookies.
- **Custom Headers:** Add or modify custom headers in requests.
- **Support for All HTTP Methods:** Use GET, POST, PUT, DELETE, and other HTTP methods.

## Website
- [Burp Suite](https://portswigger.net/burp)

## Basic Usage

### Setting Up
1. **Launch Burp Suite:**
   - Start Burp Suite from your applications menu or start menu.

2. **Navigate to Repeater:**
   - Open the Repeater module by clicking on the "Repeater" tab.

### Sending Requests
1. **Send Request to Repeater:**
   - From any intercepted request in the Proxy tab, right-click and select "Send to Repeater".

2. **Modify Request:**
   - In the Repeater tab, modify the request as needed. You can change the URL, method, headers, and body.

3. **Send Modified Request:**
   - Click the "Go" button to send the modified request.

4. **Analyze Response:**
   - Review the server's response in the lower pane. You can analyze headers, response body, and other details.

### Practical Examples

#### Testing for SQL Injection
1. **Intercept Login Request:**
   - Capture a login request using the Proxy tab and send it to Repeater.

2. **Modify Payload:**
   - Modify the username or password fields to include SQL injection payloads such as `' OR '1'='1`.

3. **Send Request:**
   - Click "Go" to send the request and analyze the response for SQL error messages or signs of successful injection.

#### Custom Header Testing
1. **Add Custom Headers:**
   - Add custom headers like `X-Forwarded-For` or `X-HTTP-Method-Override` to see how the server handles them.

2. **Send Request:**
   - Send the modified request and check if the server processes the custom headers correctly.

### Using Multiple Tabs
- **Open Multiple Tabs:**
  - Use multiple tabs in Repeater to manage and test different requests simultaneously.
  - Click the "+" icon to open a new tab.

## Best Practices
- **Keep Track of Changes:** Use descriptive tab names or comments to keep track of changes and tests performed.
- **Monitor Session State:** Ensure that you maintain the correct session state by managing cookies and session tokens.
- **Combine with Other Modules:** Use Repeater in conjunction with other Burp Suite modules like [[Burp Suite Intruder]] for automated testing and payload generation.
- **Detailed Analysis:** Use Repeater for detailed analysis and manual testing of potential vulnerabilities identified by automated scans.

## References
- [Burp Suite Official Documentation](https://portswigger.net/burp/documentation)
- [Burp Suite Repeater Guide](https://portswigger.net/burp/documentation/desktop/tools/repeater)

