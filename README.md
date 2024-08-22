## Contents
- [Prerequisites](#prerequisites)
- [Overview](#overview)
  - [Purpose](#purpose)
  - [Pros](#pros)
  - [Cons](#cons)
  - [MySQL Clustering and Router](#mysql-clustering-and-router)
  - [NCS Interconnect](#ncs-interconnect)
- [Procedure](#procedure)
  - [Initial Setup](#initial-setup)
  - [Install/Setup MySQL](#installsetup-mysql)
  - [Setup Cluster](#setup-cluster)
  - [Setup MySQL Router](#setup-mysql-router)
  - [Install/Setup EMS and NCS Interconnect](#installsetup-ems-and-ncs-interconnect)
  - [Generate SSL Certificates and Configure Tomcat SSL](#generate-ssl-certificates-and-configure-tomcat-ssl)
  - [Change Properties Files](#change-properties-files)
  - [Adjust Firewall](#adjust-firewall)
- [Install VSH](#install-vsh)
- [Testing](#testing)

## Prerequisites
- MySQL Installer 8.0
- MySQL Workbench or HeidiSQL
- Airship AI Software (Testing on 10.1.2.0)
- At least 4 VMs or Servers where everything can be installed

## Overview

### Purpose
This document outlines the steps required to set up MySQL clustering with Airship AI 9.2, in conjunction with NCS Interconnect and Failover EMS. By enabling NCS interconnect with EMS failover and MySQL clustering, a dynamic failover solution is provided for EMS/NCS. This setup allows two different EMS/NCS servers to share and manage each other’s components, even if one of the NCS/EMS servers is down.

### Pros
- Redundancy
- Automatic failover of databases and EMS/NCS components
- Potential performance improvements through load balancing

### Cons
- Requires a minimum of 3 database nodes to form a MySQL cluster, which increases deployment size
- Added system complexity and potential obfuscation

### MySQL Clustering and Router
MySQL Cluster automatically configures SSL between the nodes, eliminating the need for separate setup. It configures one node as the primary and the other two as replicas. MySQL Router must be installed alongside the cluster to direct applications to the correct database. MySQL Router listens on port `6446` for read/write connections and on port `6447` for read-only connections. All connections can be made through the read/write port; the read-only port is available to distribute read load to the secondary nodes. As MySQL Router uses a different port than the MySQL database, the JDBC URL in the NCS and `application.properties` files needs to be updated to point to port `6446` instead of `3306`.

### NCS Interconnect
NCS Interconnect enables multiple NCS instances to connect with each other to obtain the status of Airship AI components connected to those NCS instances. This feature allows one EMS/NCS to launch cases or adjust settings for components that would not otherwise be connected to that particular EMS/NCS instance. NCS Interconnect should automatically establish connections without requiring adjustments to configuration files. The only necessary configuration step is to add each EMS/NCS node to the database using the provided SQL script below.

## Procedure

### Initial Setup
1. Ensure you have 3 VMs with at least Windows Server 2016 installed (this example uses Windows Server 2019).
2. [Download](https://dev.mysql.com/downloads/installer/) and copy the MySQL installer to the 3 nodes. Use version 8.0.39, and select the `mysql-installer-web-community-8.0.39.0.msi` file.

### Install/Setup MySQL
1. Run the MySQL Installer:
   1. Select "Custom Install".
   2. Select the following components:
      1. MySQL Server
      2. MySQL Workbench
      3. MySQL Router
      4. MySQL Shell
   3. Click "Next".
   4. On the prerequisite page, click "Execute":
      1. A Visual C++ popup should appear; check the box to accept the EULA, then click "Next" to install.
      2. Click "Finish" when the installation is complete.
   5. Click "Next" to proceed.
   6. Click "Execute" to run the installers, then click "Next" when the installation is complete.
   7. Click "Next" on the product configuration page.
   8. Continue clicking "Next" until the root password page appears.
   9. Set the root password and document it for future reference.
   10. Click "Add User":
       1. Username: `<username>`
       2. Host: Leave as default.
       3. Role: DB Admin
       4. Password: Set your password.
   11. Click "Next" through the remaining setup steps, and finish the installation.

2. Add Airship AI Parameters to the `My.ini`:
   1. Open `C:\ProgramData\MySQL\MySQL Server 8.0\my.ini` in an administrative notepad on each node.
   2. Add the following lines at the bottom of the file (change the `server_id` value for each node accordingly; e.g., 1 for node 1, 2 for node 2, etc.):
```ini
   # Airship Settings
   server_id=1
   max_allowed_packet=64M
   event_scheduler=ON
   max_connections=200
   group_concat_max_len=4294967295
   innodb_log_file_size=128M
   sql_mode=STRICT_TRANS_TABLES,ERROR_FOR_DIVISION_BY_ZERO,NO_ENGINE_SUBSTITUTION
   optimizer_switch=derived_merge=off
```

3. Ensure the file is saved as ANSI; saving as UTF-8 may cause issues.
4. Restart the MySQL service on each of the nodes.

### Setup Cluster

1. Open a MySQL shell session on one of the nodes for each node in the cluster:
    1. Launch MySQL shell three times.
    2. Log in to each one with the username created earlier:
        1. Type `\connect <username>@<hostname of server>`
        2. Enter the password when prompted.
    3. Adjust permissions for the user account:
        
        1. Type `\sql`
        2. Run the following command:
```sql
GRANT CLONE_ADMIN, CONNECTION_ADMIN, GROUP_REPLICATION_ADMIN, PERSIST_RO_VARIABLES_ADMIN, REPLICATION_APPLIER, REPLICATION_SLAVE_ADMIN, ROLE_ADMIN, SYSTEM_VARIABLES_ADMIN ON *.* TO '<username>'@'%' WITH GRANT OPTION;
```
        
        3. Type `FLUSH PRIVILEGES;`
    4. Configure the cluster on each node by running the following commands:
        1. Type `\js`
        2. Type `dba.configureInstance()`
        3. Confirm any prompts for required configuration.
        4. Confirm the restart after configuration.
    5. On only one node, run the following command to create the cluster:
        1. `cluster = dba.createCluster('airship')`
    6. Add the other two nodes to the cluster:
        1. `cluster.addInstance('username@hostname for node 2')`
        2. `cluster.addInstance('username@hostname for node 3')`

### Setup MySQL Router

1. Perform the following steps on all three nodes:
    1. Open an administrative command prompt and run the following commands:
        1. `mkdir "C:\ProgramData\MySQL\MySQL Router"`
        2. `cd "C:\Program Files\MySQL\MySQL Router 8.0\bin"`
        3. `mysqlrouter.exe --bootstrap username@node1 -d "C:\ProgramData\MySQL\MySQL Router"`
            1. Enter the password when prompted.
        4. `.\mysqlrouter.exe --config "C:\ProgramData\MySQL\MySQL Router\mysqlrouter.conf" --install-service`
        5. `start-service mysqlrouter`

### Install/Setup EMS and NCS Interconnect

1. Choose which nodes to install EMS on.
2. Run the EMS installer on 2/3 of the nodes following the usual steps:
    1. **Important:** Only run the database scripts one time.
    2. If MySQL is already installed, check the "Force Run Create Database Script" box in the installer.
3. Prepare NCS Interconnect:
    1. Generate a new GUID for each server:
        1. Run `new-guid` in PowerShell.
    2. In the database, navigate to the `DVR` database.
    3. Access the `api_key` table:
        1. Add a new row and update the columns as follows:
            1. `ApiKeyId` = The next available number.
            2. `ApiKey` = The new GUID created for each EMS/NCS server.
            3. `MachineIp` = IP or hostname of the machine being associated.
    4. Go to the `application` table:
        1. Add a new row and update the columns as follows:
            1. `Id` = The next available number.
            2. `ApiKeyId` = The same number as the `MachineIp` GUID you want to relate to.
            3. `ApplicationTypeId` = Depending on the application type, use one of the following numbers:
                1. `EMS` = 4
                2. `NCS` = 10
                3. `NVP` = 12
            4. `ReportedPort` = The port on which the application is running. Defaults are `443`, `80`, and `8080`.
            5. `ReportedVersion` = The version number of the associated application.
            6. `CreatedByUsername` = Typically an Admin user (`system` or `svraccess`)
            7. `CreatedTime` = This will auto-fill when you access the cell.
### Tomcat SSL Setup

1. Stop Tomcat if it is running.
2. Open PowerShell and run:
    1. `mkdir C:\Temp`
    2. `New-SelfSignedCertificate -DnsName <dns> -CertStoreLocation "Cert:\LocalMachine\My" -NotAfter (Get-Date).AddMonths(60) | Export-PfxCertificate -FilePath C:\Temp\airdemo.pfx -Password (ConvertTo-SecureString"<password>" -AsPlainText -Force)`
3. Trust the certificate in the Windows Root Authority.

### Change Properties Files

1. For the EMS machines:
    1. Navigate to `C:\Program Files\Apache Software Foundation\Tomcat\webapps\ems\WEB-INF\classes\application.properties` and update the following values:
        - `app.apiKey` - GUID for the machine previously implemented.
        - `app.ip` - Hostname/DNS/IP of the local system.
        - `database.primary.password.clear` - Plaintext password for the database.
        - `database.primary.password.encrypted` - Encrypted password for the database.
        - `database.primary.url` - Change the port from `3306` to `6446`.
        - `database.primary.username` - Username created earlier in the installation.
        - `database.secondary.password.clear` - Plaintext password for the secondary database.
        - `database.secondary.password.encrypted` - Encrypted password for the secondary database.
        - `database.secondary.url` - Change the port from `3306` to `6446`.
        - `ncs.ip` - Ensure it matches the correct hostname/DNS/IP of the machine.
        - `ncs.port` - Ensure it matches the correct port.
        - `ncs.useSsl` - Set to `true`.
2. For the NCS machines:
    1. Navigate to `C:\Program Files\Apache Software Foundation\Tomcat\webapps\ncs\WEB-INF\classes\ncs.properties` and update the following values:
        - `app.apiKey` - GUID for the machine previously implemented.
        - `app.ip` - Hostname/DNS/IP of the local system.
        - `database.primary.password.clear` - Plaintext password for the database.
        - `database.primary.password.encrypted` - Encrypted password for the database.
        - `database.primary.url` - Change the port from `3306` to `6446`.
        - `database.primary.username` - Username created earlier in the installation.
        - `database.secondary.password.clear` - Plaintext password for the secondary database.
        - `database.secondary.password.encrypted` - Encrypted password for the secondary database.
        - `ncs.useSsl` - Set to `true`.
3. For the NVP machines:
    1. Navigate to `C:\Program Files\Apache Software Foundation\Tomcat\webapps\nvp\WEB-INF\classes\nvp.properties` and update the following values:
        - `app.apiKey` - GUID for the machine previously implemented.
        - `app.ip` - Hostname/DNS/IP of the local system.
        - `ncs.ip` - Ensure it matches the correct hostname/DNS/IP of the machine.
        - `ncs.port` - Ensure it matches the correct port.
        - `ncs.useSsl` - Set to `true`.

### Adjust Firewall

Ensure that ports `6446`, `3306`, and `443` are open.

## Install VSH

1. Install VSH on the node that did not have EMS/NCS installed or on a different node based on your configuration.
2. After installing VSH, manage it with one of the EMS/NCS instances and set the other as a backup.
3. Ensure firewall ports `6446`, `3306`, and the relevant Airship ports are open.

## Testing

There should now be two NCS instances running and communicating with each other. To validate this, start Tomcat on both EMS/NCS instances and wait for NCS to initialize. Once it's up, both NCS and EMS instances should appear as “green” in NCS, with both also showing connections to the VSH (AVA).

Additionally, it should be possible to stop Tomcat on the primary EMS/NCS that the VSH connects to and see that the VSH remains connected to the secondary EMS/NCS.

To ensure the MySQL cluster is functioning correctly, open MySQL shell (using DB credentials to connect) and execute the following commands:

```mysql
\connect <username>@<host>
dba.getCluster().status()
```

Key items to look for in the output are that the status is "OK" and that the primary node is "ONLINE" with mode "R/W". Example output below:

```json
{
    "clusterName": "airship",
    "defaultReplicaSet": {
        "name": "default",
        "primary": "WIN-BVES639U5SG:3306",
        "ssl": "REQUIRED",
        "status": "OK",
        "statusText": "Cluster is ONLINE and can tolerate up to ONE failure.",
        "topology": {
            "WIN-AL7BILGR5UR:3306": {
                "address": "WIN-AL7BILGR5UR:3306",
                "memberRole": "SECONDARY",
                "mode": "R/O",
                "readReplicas": {},
                "replicationLag": "applier_queue_applied",
                "role": "HA",
                "status": "ONLINE",
                "version": "8.0.39"
            },
            "WIN-BVES639U5SG:3306": {
                "address": "WIN-BVES639U5SG:3306",
                "memberRole": "PRIMARY",
                "mode": "R/W",
                "readReplicas": {},
                "replicationLag": "applier_queue_applied",
                "role": "HA",
                "status": "ONLINE",
                "version": "8.0.39"
            },
            "WIN-QN1U6CGHJES:3306": {
                "address": "WIN-QN1U6CGHJES:3306",
                "memberRole": "SECONDARY",
                "mode": "R/O",
                "readReplicas": {},
                "replicationLag": "applier_queue_applied",
                "role": "HA",
                "status": "ONLINE",
                "version": "8.0.39"
            }
        },
        "topologyMode": "Single-Primary"
    },
    "groupInformationSourceMember": "WIN-BVES639U5SG:3306"
}
```


