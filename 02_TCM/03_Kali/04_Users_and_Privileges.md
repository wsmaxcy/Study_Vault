```
drwx------ 66 will will      4096 Jul  3 22:57 .
drwxr-xr-x  4 root root      4096 Jun 16 15:43 ..
-rw-r--r--  1 will will     11354 Sep 24  2023 3389.txt
-rw-r--r--  1 will will    126069 Sep 24  2023 445.txt
drwxrwxr-x  4 will will      4096 Jun 30 16:15 .ansible
drwxr-xr-x  4 will will      4096 Jul 30  2023 .armitage
```
`d` - means that it is a directory - will be the first list of the  example
`-` means not
## List is as follows

| Directory               | Owner Membership                | Group Membership                | All other users                 |
| ----------------------- | ------------------------------- | ------------------------------- | ------------------------------- |
| `d` if yes<br>`=` if no | `rwx` - if yes<br>`---` - if no | `rwx` - if yes<br>`---` - if no | `rwx` - if yes<br>`---` - if no |
### How to change permissions
`chmod` - change mode - changes permissions
`chmod +rwx <filename>` - changes the permissions to read, write, executable for the file selected

### chmod numbers

| Num | Perm  | Totals |
| --- | ----- | ------ |
| 0   | `---` | 0+0+0  |
| 1   | `--x` | 0+0+1  |
| 2   | `-w-` | 0+2+0  |
| 3   | `-wx` | 0+2+1  |
| 4   | `r--` | 4+0+0  |
| 5   | `r-x` | 4+0+1  |
| 6   | `rw-` | 4+2+0  |
| 7   | `rwx` | 4+2+1  |
### Ways to see who can sudo

`grep 'sudo' /etc/group`

output will look like this:
```bash
➜  ~ grep 'sudo' /etc/group
sudo:x:27:will
```
