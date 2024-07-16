## File Share
- Basically when there is s `Z` Drive or something that everyone can see
- Port `139`
- Scans folder, this would be from the printer/scanner to automatically give you access to files

## Metasploit
- run `msfconsole`
- [[Metasploit]] this is an exploitation framework
- auxiliary modules - scanning and enumeration
- post modules - post exploition

Looking for [[SMB]] Version types;

## Tools
[[smbclient]] is a tool that we can use that helps connect/enumerate [[SMB]]

****
### End of Video Questions

**Question**: My `enum4linux` and/or `smbclient` are not working. I am receiving "Protocol negotiation failed: `NT_STATUS_IO_TIMEOUT`". How do I resolve?

**Resolution**:

On Kali, edit `/etc/samba/smb.conf`

Add the following under global:

client min protocol = CORE

client max protocol = SMB3