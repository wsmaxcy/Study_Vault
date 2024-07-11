`80`,`443` - Typical Web ports = BAD
`111`,`139` - Typically SMB = BAD
`22` - Typically SSH = Good

### Low Hanging Fruit
Go for Web Apps and SMB before things like SSH

### Thought process after a scan
Lets look at port 80 and 443
1. Go to website and take a look around to see what is going on.
	1. If we see a default web page like this, this is an automatic finding.
	2. Tells us what type of architecture that is running
	3. Tells us that the client hygiene isn't great
		1. Are there other web directories there
		2. Aren't hosting any website and these web clients are just running
			1. This seems like poor hygiene if so
	4. Take notes of what you see
2. See if you can click on anything. Manual enumeration
	1. If there is an error page, see what site info you can glean from the info given back
	2. Track any information disclosure that you find.
3. Maybe do some vulnerability scanning on the web app. [[Nikto]] is a great example
	1. Lots of times the site can block you if they see you are using Nikto scan
	2. `nikto -h <ipaddress>`
	3. Take a look and see what info the output gives you. What is out of date? What security headers aren't there? What vulnerabilities can you find?
4. Save all of these scans to go back for notes.
5. Directory Busting using [[dirbuster]], [[dirb]], or [[gobuster]].
	1. Dirbuster lets you use this with a GUI. Fill out the info on what you want it to use.
	2. Select wordlist that you want to use. These tools enumerate the directory in order to check for the folder/page
	3. This also can check file extensions like `.txt` or `.php`.
		1. The more you put in, the longer that it takes
6. Get out [[Burp Suite]] and take a peek to see what is out there.
	1. Use the Burp Suite [[repeater]] method to try to forward crafted packets.
7. View the source code
	1. View comments, user names, passwords, etc. This is popular in source code, but in a pentest looking for passwords helps out.