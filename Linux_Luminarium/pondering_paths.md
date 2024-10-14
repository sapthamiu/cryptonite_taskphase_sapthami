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
