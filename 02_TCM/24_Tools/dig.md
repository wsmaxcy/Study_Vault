## Overview
Dig (Domain Information Groper) is a command-line tool used for querying DNS name servers. It performs DNS lookups and displays the responses.

## Features
- Query DNS servers
- Troubleshoot DNS issues
- Gather information about domain records

## Installation
```sh
sudo apt-get install dnsutils
```

## Usage

```sh
dig example.com
```
## Common Commands

- Basic query: `dig example.com`
- Query specific record type: `dig example.com MX`
- Query a specific DNS server: `dig @8.8.8.8 example.com`

## References

- Dig Manual