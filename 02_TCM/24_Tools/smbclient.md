# smbclient

## Overview
`smbclient` is a command-line tool provided by Samba that allows users to access SMB/CIFS resources on a network. It functions similarly to an FTP client, enabling users to list, download, upload, and manage files on remote SMB servers.

## Features
- **File Access:** List, download, and upload files to SMB shares.
- **Interactive Mode:** Provides an interactive shell for managing files on SMB shares.
- **Authentication:** Supports username and password authentication for accessing protected shares.
- **Versatile Operations:** Allows for various file operations such as copying, moving, and deleting files.

## Website
- [Samba.org](https://www.samba.org/)

## Installation

### On Unix-based systems (Linux/macOS):
1. **Install smbclient:**
   - On Debian-based systems:
```sh
sudo apt-get install smbclient
```
   - On Red Hat-based systems:
```sh
sudo yum install samba-client
```
   - On macOS using Homebrew:
```sh
brew install samba
```

### On Windows:
- SMB client functionality is built into Windows and accessible through File Explorer and Command Prompt (`net` commands).

## Basic Usage
`smbclient` can be used in both interactive and non-interactive modes. Here are some common commands and usage examples:

### List Shared Folders
To list available shares on a server:
```sh
smbclient -L //server -U username
```

### Access Shared Folder
To connect to a specific share:
```sh
smbclient //server/share -U username
```

### Download a File
To download a file from a share:
```sh
smbclient //server/share -U username -c 'get remote_file local_file'
```

### Upload a File
To upload a file to a share:
```sh
smbclient //server/share -U username -c 'put local_file remote_file'
```

### Interactive Mode
To start an interactive session:
```sh
smbclient //server/share -U username
```
Within the interactive session, you can use commands such as:
- `ls` - List files and directories
- `cd` - Change directory
- `get` - Download a file
- `put` - Upload a file
- `del` - Delete a file
- `mkdir` - Create a directory
- `rmdir` - Remove a directory

### Using smbclient with a Password
You can specify the password directly in the command (not recommended for security reasons):
```sh
smbclient //server/share -U username%password
```
Alternatively, you can omit the password and `smbclient` will prompt you for it securely:
```sh
smbclient //server/share -U username
```

## Advanced Options
`smbclient` offers several advanced options for more specific use cases:

### Specify Workgroup
To specify a workgroup:
```sh
smbclient //server/share -U username -W workgroup
```

### Use a Config File
To use a custom configuration file:
```sh
smbclient //server/share -U username -s /path/to/smb.conf
```

### Recursive File Operations
To download/upload directories recursively:
```sh
smbclient //server/share -U username -c 'prompt OFF; recurse ON; mget directory/*'
```

## Best Practices
- **Use Secure Password Handling:** Avoid including passwords in command-line arguments. Use secure prompting or password files with appropriate permissions.
- **Restrict Permissions:** Ensure that the SMB shares and files have appropriate permissions to prevent unauthorized access.
- **Monitor Usage:** Regularly monitor and log access to SMB shares to detect and respond to unauthorized activities.
- **Combine with Other Tools:** Use `smbclient` in conjunction with other tools like [[Nmap.md|Nmap]] for comprehensive network assessments.

## References
- [Samba Documentation](https://www.samba.org/samba/docs/current/man-html/smbclient.1.html)
- [smbclient Man Page](https://www.samba.org/samba/docs/man/manpages/smbclient.1.html)
- [SMB Protocol Documentation](https://docs.microsoft.com/en-us/openspecs/windows_protocols/ms-smb/)

