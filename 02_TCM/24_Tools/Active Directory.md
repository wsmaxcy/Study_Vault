## Overview
Active Directory (AD) is a directory service developed by Microsoft for Windows domain networks. It is a centralized and standardized system that automates network management of user data, security, and distributed resources, and enables interoperation with other directories.

## Features
- **Centralized Management:** Manages users, computers, and other resources from a centralized location.
- **Authentication and Authorization:** Provides secure authentication and authorization mechanisms.
- **Group Policy:** Allows administrators to manage settings and configurations across users and computers.
- **Replication:** Ensures data consistency across multiple domain controllers.
- **Integration:** Integrates with various Microsoft and third-party applications and services.

## Components
- **Domain:** A logical group of objects such as users, computers, and devices that share the same AD database.
- **Tree:** A collection of one or more domains that share a common namespace.
- **Forest:** A collection of one or more domain trees that share a common schema and global catalog.
- **Organizational Unit (OU):** A container used to organize objects within a domain.
- **Domain Controller (DC):** A server that responds to security authentication requests within the domain.

## Installation

### On Windows Server:
1. **Open Server Manager:**
   - Click on "Add Roles and Features."

2. **Add Active Directory Domain Services:**
   - Select "Active Directory Domain Services" and complete the wizard.

3. **Promote Server to Domain Controller:**
   - After installation, click on the notification flag and promote the server to a domain controller.

4. **Configure the Domain:**
   - Choose "Add a new forest" and specify the root domain name.

5. **Complete Configuration:**
   - Complete the remaining configuration steps and restart the server.

## Basic Usage
Active Directory is managed using tools like the Active Directory Users and Computers (ADUC) snap-in, PowerShell, and Group Policy Management Console (GPMC).

### Creating Users
To create a new user in ADUC:
1. **Open ADUC:**
   - Go to "Start" > "Administrative Tools" > "Active Directory Users and Computers."

2. **Navigate to OU:**
   - Right-click on the desired OU, select "New" > "User."

3. **Complete the Wizard:**
   - Enter user details and complete the wizard.

### Managing Group Policies
To create a new Group Policy Object (GPO):
1. **Open GPMC:**
   - Go to "Start" > "Administrative Tools" > "Group Policy Management."

2. **Create GPO:**
   - Right-click on the desired domain or OU, select "Create a GPO in this domain, and Link it here."

3. **Edit GPO:**
   - Right-click the newly created GPO and select "Edit" to configure settings.

### Using PowerShell
PowerShell provides cmdlets for managing AD. Below are some common commands:

#### Creating a New User
```sh
New-ADUser -Name "John Doe" -GivenName John -Surname Doe -SamAccountName jdoe -UserPrincipalName jdoe@example.com -Path "OU=Users,DC=example,DC=com" -AccountPassword (ConvertTo-SecureString "P@ssw0rd" -AsPlainText -Force) -Enabled $true
```

#### Resetting a User's Password
```sh
Set-ADAccountPassword -Identity jdoe -NewPassword (ConvertTo-SecureString "NewP@ssw0rd" -AsPlainText -Force)
```

#### Enabling a User Account
```sh
Enable-ADAccount -Identity jdoe
```

## Best Practices
- **Regular Backups:** Regularly back up AD to ensure data recovery in case of failure.
- **Least Privilege:** Assign the least privilege necessary to users and administrators.
- **Group Policy Management:** Use Group Policies to enforce security settings and configurations.
- **Monitor AD:** Use monitoring tools to keep an eye on AD health and security.
- **Documentation:** Keep thorough documentation of your AD environment, including configurations and changes.

## References
- [Microsoft Active Directory Documentation](https://docs.microsoft.com/en-us/windows-server/identity/active-directory-domain-services)
- [Active Directory PowerShell Module](https://docs.microsoft.com/en-us/powershell/module/addsadministration/?view=win10-ps)
