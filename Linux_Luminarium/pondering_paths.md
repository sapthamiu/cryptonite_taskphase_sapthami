# Pondering Paths
## The Root
### Description
In this level, we've added a program right in /, called pwn, that will give you the flag. All you need to do for this level is to invoke this program!
### Approach
Just type the given command after SSHing to the server
### Commands
`/pwn`
### Flag
`pwn.college{gr8DAhzw4ZWYy4tQPJjA2RCCX_j.dhzN5QDLyUzM2czW}`

## Program and Absolute Paths
### Description
The name of the challenge program in this level is run, and it lives in the /challenge directory. Thus, the path to the run challenge program is /challenge/run.
### Approach
Invoke the challenge as described in the problem
### Commands
`/challenge/run`
### Flag
`pwn.college{YYZ3CSbKt1-p3gSTbIRNFMtuoqC.dVDN1QDLyUzM2czW}`

## Position Thy Self
### Description
This challenge will require you to execute the /challenge/run program from a specific path (which it will tell you). You'll need to cd to that directory before rerunning the challenge program.
### Approach
Upon running the command `/challenge/run` command, it asks you to get into the `usr/include` directory and rerun the command.
### Commands
```
/challenge/run
cd /usr/include
/challenge/run
```
### Flag
`pwn.college{YQEGD8o88dRFsw8ydrpZBA0U6Ke.dZDN1QDLyUzM2czW}`

## Position Elsewhere
### Description
This challenge will require you to execute the /challenge/run program from a specific path (which it will tell you). You'll need to cd to that directory before rerunning the challenge program.
### Approach
Upon invoking the challenge, it asks you to redirect to the `/proc/67/fd ` directory and rerun the challenge.
### Commands
```
/challenge/run
cd /proc/67/fd
/challenge/run
```
### Flag
`pwn.college{47ptEdRDSXpTqnyUkkdAFDiFg7X.ddDN1QDLyUzM2czW}`

## Position yet Elsewhere
### Description
This challenge will require you to execute the /challenge/run program from a specific path (which it will tell you). You'll need to cd to that directory before rerunning the challenge program.
### Approach
Upon invoking the challenge, it asks you to redirect to`/etc/apt/sources.list.d` and rerun the challenge.  
### Commands
```
/challenge/run
cd /etc/apt/sources.list.d
/challenge/run
```
### Flag
`pwn.college{4hTaZgg4nRwUMZS8XsnMd4yuHoz.dhDN1QDLyUzM2czW}`

## Implicit relative paths, from /
### Description
You'll need to run /challenge/run using a relative path while having a current working directory of /. For this level, I'll give you a hint. Your relative path starts with the letter c. 
### Approach
First get into the root directory and then run the challenge.  
### Commands
```
cd /
challenge/run
```
### Flag
`pwn.college{YCraROPERPzKIj2w4-VtteQd5Ac.dlDN1QDLyUzM2czW}`

## Explicit relative paths, from /
### Description
This challenge will get you using . in your relative paths.
### Approach
In most operating systems, including Linux, every directory has two implicit entries that you can reference in paths: `.` and `..`.  
The first, `.`, refers right to the same directory.  
First get into the root folder and then use an explicit relative path as in the description.  
### Commands
```
cd /
./challenge/run
```
### Flag
`pwn.college{AJWuDSqmi0DpOaQwwE-F2D0Mz6r.dBTN1QDLyUzM2czW}`

## Implicit relative path
### Description
In this level, we'll practice refering to paths using `.` a bit more. This challenge will need you to run it from the /challenge directory.
### Approach
>**Notes:** Linux explicitly avoids automatically looking in the current directory when you provide a "naked" path.  
    ```
    cd /challenge  
    run
    ```
This will not invoke `/challenge/run`.  
This is actually a safety measure: if Linux searched the current directory for programs every time you entered a naked path, you could accidentally execute programs in your current directory that happened to have the same names as core system utilities!  
As a result, the above commands will yield a `command not found` error.  
We have to explicitly use relative paths to launch run in this scenario.  
The way to do this is to tell Linux that you explicitly want to execute a program in the current directory, using `.`.  

Change directories to `challenge` and invoke `run`.  
### Commands
```
cd /challenge
./run
```
### Flag
`pwn.college{wBF5zOD4rKyiReuV57FofVHgQEa.dFTN1QDLyUzM2czW}`

## Home Sweet Home
### Description
In this challenge, `/challenge/run` will write a copy of the flag to any file you specify as an argument on the commandline, with these constraints:

1. Your argument must be an absolute path.
2. The path must be inside your home directory.
3. Before expansion, your argument must be three characters or less.
### Approach
> **Notes:** Typically, your shell session will start with your home directory as your current working directory.  
The `~` in the initial prompt is shorthand for the current working directory.  
Bash provides and uses this shorthand because most of your time will be spent in your home directory.  
Thus, whenever bash sees `~` provided as the start of an argument in a way consistent with a path, it will expand it to your home directory.  
Note that the expansion of `~` is an absolute path, and only the leading `~` is expanded.  
This means, for example, `~/~` will be expanded to `/home/hacker/~` rather than `/home/hacker/home/hacker`.  
`cd` will use your home directory as the default destination.

It is given that an absolute path to the target file is to be given as argument to `/challenge/run`.  
It is also given that the argument should be less than or equal to 3 characters before expanding (`~/` is a must for an absolute path in home directory, leaving us to choose a single letter for the filename). 

### Commands
`/challenge/run ~/t`
### Flag
`pwn.college{ATqwPnLkG7k6ZoEij0Ry6-0oIYB.dNzM4QDLyUzM2czW}`