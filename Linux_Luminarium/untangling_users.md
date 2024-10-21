# Untangling Users

## Becoming root with su
### Description
THIS challenge (and only this challenge) does have a root password. That password is `hack-the-planet`, and you must provide it to `su` to become root! Go do that, and read the flag
### Approach
>**Notes**:  
`su` = Switch User  
Older method to become root.  
`su` prompts for root password to elevate and fails if the password is incorrect.  
Modern systems rarely use root passwords, so this method is obsolute.  
### Commands
```
su
hack-the-planet
cat /flag
```
### Flag
`pwn.college{kfBtPioD185-2Hio0F2p4GNpO4w.dVTN0UDLyUzM2czW}`

## Other Users with su
### Description
In this level, you must switch to the `zardus` user and then run `/challenge/run`. Zardus' password is `dont-hack-me`.
### Approach
>**Notes**: `su` with an argument switches to the specified username instead of root.  
Syntax: `su <username>`
### Commands
```
su zardus
dont-hack-me
/challenge/run
```
### Flag
`pwn.college{wVby9vmJGD7svqaRvas-iH9-oZX.dZTN0UDLyUzM2czW}`

## Cracking Passwords
### Description
This level gives you a leak of `/etc/shadow` (in `/challenge/shadow-leak`). Crack it (this could take a few minutes), `su` to `zardus`, and run `/challenge/run` to get the flag!
### Approach
>**Notes**:  
Passwords were previously stored in `/etc/passwd`, which was globally readable and not secure.  
Now they are stored in `/etc/shadow`, which is not globally readable and hence secure.  
Format: `username:password:...`  
`*` or `!` implies password login is disabled.  
Empty field implies no password is set and a long string means a hashed password.   
`su` hashes the input password and compares it with the stored hash.  
Leaks can expose `/etc/shadow`.  
Tools like John the Ripper can crack hashed passwords.  

We are given a leaked password hashfile, which John the Ripper tool can crack password from, after which we `su` to `zardus` and execute run.  
### Commands
```
john /challenge/shadow-leak
su zardus
aardvark
/challenge/run
```
### Flag
`pwn.college{Mb9a_e6QMwD8hwoKAWjnxoMjGpl.ddTN0UDLyUzM2czW}`  

## Using sudo
### Description
In this level, we will give you `sudo` access, and you will use it to read the flag.
### Approach
>**Notes**: `sudo` = Superuser Do  
`sudo` runs a command as root without requiring root password.  
Uses policies from `/etc/sudoers` to authorize users.  
Scalable for large environments, unlike `su`.  
### Commands
`sudo cat /flag`
### Flag
`pwn.college{Uht4QH3BLKOwl4HilQgfLGLdwlW.dhTN0UDLyUzM2czW}`