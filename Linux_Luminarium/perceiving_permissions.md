# Perceiving Permissions

## Changing File Ownership
### Description
In this level, we will practice changing the owner of the `/flag` file to the `hacker` user, and then the flag. For this challenge only, I made it so that you can use chown to your heart's content as the `hacker` user (again, typically, this requires you to be `root`). Use this power wisely and chown away!
### Approach
>**Notes**: 
User: Usually the one who created the file.  
On shared systems (e.g., computer labs), each user has their own files.  
Root Account: The admin account with full access (hacker's target)  
Use `chown` command to change ownership(only root can change file ownership).  
Syntax: `chown <username> <filename>`  
### Commands
```
chown hacker /flag
cat /flag
```
### Flag
`pwn.college{MjiGCnTDyYX07bGbXHeiKmOdA38.dFTM2QDLyUzM2czW}`

## Groups and Files
### Description
In this level, I have made the flag readable by whatever group owns it, but this group is currently `root`. Luckily, I have also made it possible for you to invoke `chgrp` as the `hacker` user! Change the group ownership of the flag file, and read the flag!
### Approach
> Linux files have both an owning user and group.  
Use `id` command to check your group membership: `id` shows your user ID, group ID, and groups you're in.  
Use `chgrp` to change file group ownership (usually requires `root`)   
Syntax: `chgrp <groupname> <filename>`
### Commands
```
chgrp hacker /flag
cat /flag
```
### Flag
`pwn.college{IyLJDjSQbW1RESh0Qf6sWuihw4O.dFzNyUDLyUzM2czW}`

## Fun with Group names
### Description
You've used `hacker` for the group before, but in this level, that is not going to work. I'll still allow you to use `chgrp`, but I have randomized the name of the group that your user is in. You will need to use the `id` command to figure that name out, then `chgrp` to victory!
### Commands
```
id
chgrp grp14544 /flag
cat /flag
```
### Flag
`pwn.college{gjNYFUlaLqxismmW4hScttxVsKY.dJzNyUDLyUzM2czW}`

## Changing Permissions
### Description
In this challenge, you must change the permissions of the `/flag` file to read it! Typically, you need to have write access to the file in order to change its permissions, but I have made the `chmod` command all-powerful for this level, and you can `chmod` anything you want even though you are the `hacker` user. This is an ultimate power. The `/flag` file is owned by root, and you can't change that, but you can make it readable.
### Approach
>**Notes**:    
Permissions format: `rwxrwxrwx` (user, group, others).  
File Types:  
`-`: Regular file  
`d`: Directory  
Permission Characters:  
`r` (read): Can view file contents (list directory contents).  
`w` (write): Can modify file (add/remove files in a directory).  
`x` (execute): Can run file as a program (enter directory).  
`-`: No permission.  
Use `chmod` to modify file permissions.  
Syntax: `chmod [OPTIONS] <mode> <filename>`  
MODE can adjust or overwrite existing permissions.  
Modifying an existing mode: `chmod <who> +/- <what>`  
WHO: `u`, `g`, `o`, `a` (user, group, others, all)  
WHAT: `r`, `w`, `x` (read, write, execute)  

Upon checking the file permissions of the flag file, it is found that only the owner can read it. We change this so that all users can read it.  
### Commands
```
ls -l /flag
chmod a+r /flag
cat /flag
```
### Flag
`pwn.college{QBbNzTqf71ClbBsST54IGvVPlUc.dNzNyUDLyUzM2czW}`

## Executable Files
### Description
In this challenge, the `/challenge/run` program will give you the flag, but you must first make it executable! Remember your `chmod`, and get `/challenge/run` to tell you the flag!
### Approach
All users initially have only read permission. We enable the execution permission through `chmod`  
### Commands
```
ls -l /challenge/run
chmod a+x /challenge/run
/challenge/run
```
### Flag
`pwn.college{cylxtkKmmwO_vvlwOM7b7x1TZ_h.dJTM2QDLyUzM2czW}`

## Permission tweaking practice
### Description
This challenge will ask you to change the permissions of the `/challenge/pwn` file in specific ways a few times in a row. If you get the permissions wrong, the game will reset and you can try again. If you get the permissions right eight times in a row, the challenge will let you `chmod` `/flag` to make it readable for yourself :-\) Launch `/challenge/run` to get started!
### Approach
Changing the file permission 8 times as instructed, the user(hacker) gets the ability to change permissions of the flag file.  
### Commands
```
/challenge/run
chmod go+w /challenge/pwn
chmod ugo-rw /challenge/pwn
chmod uo+w /challenge/pwn
chmod uo+rx /challenge/pwn
chmod u-rwx /challenge/pwn
chmod o-x /challenge/pwn
chmod ug-rw /challenge/pwn
chmod u+r /flag
cat /flag
```
### Flag
`pwn.college{ITpcftjv6vxmGkWa_Ft04P1eeYO.dBTM2QDLyUzM2czW}`

## Permission Setting Practice
### Description
This level extends the previous level by requesting more radical permission changes, which you will need `=` and `,`-chaining to achieve.
### Approach
>**Notes**:  
Use `=` to set permissions(instead of +/-), replacing old ones.  
Combine modes with `,` to set different permissions for user and group.  
Use `-` to remove all permissions for a category.

### Commands
```
/challenge/run
chmod u=x,g=rx,o=rx /challenge/pwn
chmod u=r,g=r,o=rwx /challenge/pwn
chmod g=-,o=rwx /challenge/pwn
chmod u=2,g=r /challenge/pwn
chmod u=rw,o=x,/challenge/pwn
chmod u=rwx,g=x,o=rw /challenge/pwn
chmod g=r,o=x /challenge/pwn
chmod u=-,g=rx,o=rx /challenge/pwn
chmod u=r /flag
cat /flag
```
### Flag
`pwn.college{8cWAYudRnDnw7h7DyRqyAWj6kVR.dNTM5QDLyUzM2czW}`

## The SUID Bit
### Description
We are going to let you add the SUID bit to the `/challenge/getroot` program in order to spawn a root shell for you to `cat` the flag yourself!
### Approach
>**Notes**:  
SUID = Set User ID   
Non-root users sometimes need temporary elevated privileges for system tasks.  
SUID allows a program to run as the file's owner (e.g., root), regardless of who executes it.
Commonly used for programs like `su` and `sudo`.  
SUID is represented by s in the executable permission.  
Use `chmod` to enable SUID: `chmod u+s <program>`  
Setting SUID on root-owned executables can create security risks.  

Set the SUID and then execute the program to get access to the root shell and then cat the flag.  
### Commands
```
chmod u+s /challenge/getroot
/challenge/getroot
cat /flag
```
### Flag
`pwn.college{YUxvxUN6wHsYT9pR-5z4MhQ0X05.dNTM2QDLyUzM2czW}`