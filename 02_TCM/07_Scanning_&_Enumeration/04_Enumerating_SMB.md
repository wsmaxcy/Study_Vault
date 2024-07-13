## File Share
- Basically when there is s `Z` Drive or something that everyone can see
- 
****
### End of Video Questions

**Question**: My `enum4linux` and/or `smbclient` are not working. I am receiving "Protocol negotiation failed: `NT_STATUS_IO_TIMEOUT`". How do I resolve?

**Resolution**:

On Kali, edit `/etc/samba/smb.conf`

Add the following under global:

client min protocol = CORE

client max protocol = SMB3