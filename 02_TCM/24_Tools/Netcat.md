## Overview
Netcat is a versatile networking tool used for reading from and writing to network connections using TCP or UDP. It's commonly used for debugging, network exploration, and as a back-end tool in scripts for various networking tasks.

## Features
- TCP/UDP connections
- Port scanning
- Data transfer
- Network debugging

## Installation
```sh
sudo apt-get install netcat
```
## Usage

- Connect to a server: `nc example.com 80`
- Listen on a port: `nc -l 1234`
- File transfer: `nc -l 1234 > received_file`

## References

- Netcat Manual