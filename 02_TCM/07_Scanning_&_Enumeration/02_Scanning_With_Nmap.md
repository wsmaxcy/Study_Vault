Basic scan is 
`SYN SYNACK ACK`
Here, [[Nmap]] will do this and can do this with Stealth Scanning like this `-sS`

This USED to be stealthy, but it is not stealthy at all. 

## Why is it called Stealth Scanning?
It goes `SYN SYNACK RST`
- Instead of connecting, there will be no connection. This means that there were never actually any connection, but it can still be picked up today. It is not stealthy anymore
### Other Commands
- `-T4` - Timing. T4 is faster and not really worried about speed purposes
- `-p-` - scan all ports. When there is no `-p` selected, it scans the top 1000 ports
- `-A` - Stands for EVERYTHING. I want the Version Info, Operating System, Fingerprinting, Everything.
- `-sU` - Scans UDP - UDP takes forever to scan. There is no connection response time. He says only to scan the top 1000 for UDP

