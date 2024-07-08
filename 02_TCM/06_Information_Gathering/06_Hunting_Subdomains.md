Lots of times Web Pen tests will be asked for. So Enumeration and gathering information will be very helpful.
### Important things
1. **Identify Subdomains** - `*.tesla.com`, the `*` would be a subdomain, so `dev.tesla.com` could be a part of that
A good tool for this would be [[Sublist3r]]. All you have to do is type
`sublist3r -d testla.com` and it will look for all subdomains. similar to what the harvester will do.

### crt.sh
[[crt.sh]] is another way to use "Certificate Fingerprinting" in DNS to find all subdomains and sub subdomains. It looks for 3rd level domains as well

results of this lists out all the subdomains of the website searched for

### Go To tool for Bug Bounty
- [[OWASP Amass]]
- Configure it to do a lot of things and configure a lot of sub domains

[[httprobe]] - another tool that basically does the same thing. 