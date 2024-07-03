## Day in the Life of a Pentester
---
### External Network Pentest
- Most common type
- If you are just hired, you will probably start out with this
- Most straightforward
- Jr. could take on and build up experience
### What is it?
- Looking at the organization from the outside
- hacking in from the outside
- Focuses heavily on OSINT
	- Find out about organization and employees
### Questions?
- Who are their employees
- what is there email format
- breach?
- what breach?
- what passwords from that breach.
- collect data and use it against their organization where we get their login and breach an Email or VPN or Login page
### Vuln Scanning
 - If we find something that is incredibly dangerous, chances are that these have already been found out as well
 - usually they have their external networks buttoned up pretty well
 - Most common type of pentest for 2 reasons
	 1. Compliances dictates that this must be done
	 2. This is the easiest/cheapest
- Tend to last around 32-40 hours on average
- Smaller companies would scale down
- more time is needed for report writing as well
---
### Internal Network Pentest
- Normally this is when someone remotes into a laptop and the pentester preforms the pen test from on the network.
- Lot of work is remote because no one has to be on site to do it
- Big thing that is focused on is pentesting [[Active Directory]]
- 95 Percent of fortune 500 companies use [[Active Directory]]
- Need to understand AD to perform an internal pentest.
---
### Web Application Pentest
- Lot of attack surface that is out there
- Organizations will come to pentesters and ask them to perform a pentest to make sure that it is holding up
- [[OWASP]] is a great framework and has testing guidelines to perform a test.
- Learn the [[OWASP]] Top Ten vulnerabilities
- Mostly 32 - 40 hour range with time for Report
---
### Wireless Pentest
- Test segmentation - can user access everything or is it properly segmented on the network
- Key reuses - Test pre-shared key for password strength and see
- Wireless Adapter can use packet injection
- Last 4-8 hours per SSID, then 2 hours for report writing
___
### Physical Pentest
 - assessing an orginzation's physical security
 - Going on site and trying to break into the building
	 - cloning badges
	 - picking locks
	 - social engineering
	 - breaking in, etc.
- Client goals could be just to get in building, to get into server room, to get a shell on the network, etc.
- Phishing campaign
- Vishing Campaign
- SMSishing campaign
### Other Assessments
- Mobile
- IoT Pen Test
- Red Team
- Purple Team
- etc.
---
### Report Writing
 - Typically delivered within a week after the engagement ends
 - Report should highlight both non-technical (executive) and technical findings
 - Recommendations for remediation should be clear to both executives and technical staff
---
### Debrief
 - walk through your report findings. this can be with technical and non-technical staff present
 - It gives an opportunity for the client to ask questions and address any concerns before a final report is released.