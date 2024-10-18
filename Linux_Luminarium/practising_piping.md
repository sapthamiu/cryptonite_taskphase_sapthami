# Practising Piping


## Redirecting Output
### Description
In this challenge, you must use this input redirection to write the word `PWN` (all uppercase) to the filename `COLLEGE` (all uppercase).
### Approach
>**Notes**: `echo hi > asdf`
>This will redirect the output of `echo hi` (which will be hi) to the file `asdf`. You can then use a program such as `cat` to output this file.
### Commands
`echo PWN > COLLEGE`
### Flag
`pwn.college{Y7_CETgOe99veTFzh3LGj8ao1KM.dRjN1QDLyUzM2czW}`

## Redirecting more output
### Description
In this level, `/challenge/run` will once more give you a flag, but only if you redirect its output to the file myflag. Your flag will, of course, end up in the myflag file!
### Approach
### Commands
```
/challenge/run > myflag
cat myflag
```
### Flag
`pwn.college{wHh5DcX5eZoJAXRASEEyYg-rwMP.dVjN1QDLyUzM2czW}`

## Appending Output
### Description
Run `/challenge/run` with an append-mode redirect of the output to the file `/home/hacker/the-flag`. The practice will write the first half of the flag to the file, and the second half to `stdout` if `stdout` is redirected to the file. If you properly redirect in append-mode, the second half will be appended to the first, but if you redirect in truncation mode (`>`), the second half will overwrite the first and you won't get the flag!
### Approach
### Commands
```
/challenge/run >> /home/hacker/the-flag
cat /home/hacker/the-flag
```
### Flag
`pwn.college{8mGKpq_L2KAXxk1Af5zZe0z8ULN.ddDM5QDLyUzM2czW}`

## Redirecting Errors
### Description
In this challenge, you will need to redirect the output of `/challenge/run`, like before, to `myflag`, 
and the "errors" (in our case, the instructions) to `instructions`.  
You'll notice that nothing will be printed to the terminal, because you have redirected everything! 
You can find the instructions/feedback in `instructions` and the flag in `myflag` when you successfully pull this off!
### Approach
>**Notes**: A File Descriptor (FD) is a number that describes a communication channel in Linux.  
>We're already familiar with three:
FD 0: Standard Input
FD 1: Standard Output
FD 2: Standard Error
### Commands
```
/challenge/run > myflag 2> instructions
cat myflag
```
### Flag
`pwn.college{EIPyMdpqgsB5dUVeWdkZtHxC7s0.ddjN1QDLyUzM2czW}`

## Redirecting Input
### Description
In this level, we will practice using  `/challenge/run`, which will require you to redirect the `PWN` file to it 
and have the `PWN` file contain the value `COLLEGE`!  
To write that value to the `PWN` file, recall the prior challenge on output redirection from `echo`!
### Approach
First write the word `COLLEGE` into the file `PWN`  
Then redirect it to `/challenge/run`
### Commands
```
echo COLLEGE > PWN
/challenge/run < PWN
```
### Flag
`pwn.college{kJtJo6DdNHhReixfm4g4n1PTW8Y.dBzN1QDLyUzM2czW}`

## Grepping Stored Results
### Description
In preparation for more complex levels, we want you to:

Redirect the output of `/challenge/run` to `/tmp/data.txt`.
This will result in a hundred thousand lines of text, with one of them being the flag, in `/tmp/data.txt`.
Grep that for the flag!
### Approach
As given in the description
### Commands
```
/challenge/run > /tmp/data.txt
grep pwn.college /tmp/data.txt
```
### Flag
`pwn.college{sApZtJOvbKXS4dFAGlGEHxwMS8l.dhTM4QDLyUzM2czW}`

## Grepping live output
### Description
`/challenge/run` will output a hundred thousand lines of text, including the flag. Grep for the flag!
### Approach
>Syntax: `stdout | stdin `
The output of `/challenge/run` should be searched for the flag.  
### Commands
`/challenge/run | grep pwn.college`
### Flag
`pwn.college{46AflWwgxcB2YdWWSBXHzIbxLfP.dlTM4QDLyUzM2czW}`

## Grepping Errors
### Description
This level will overwhelm you with output too, but this time on standard error. Grep through it to find the flag!
### Approach
>**Notes**: The `|` operator redirects only standard output to another program, and there is no `2|` form of the operator!
>The shell has a `>&` operator, which redirects a file descriptor to another file descriptor. 
### Commands
`/challenge/run 2>& 1 | grep pwn.college`
### Flag
`pwn.college{Y8IUzfQPl5aED_Wl4ABHxkE4Fet.dVDM5QDLyUzM2czW}`

## Duplicating piped data with tee
### Description
This process `/challenge/pwn` must be piped into `/challenge/college`, but you'll need to intercept the data to see what `pwn` needs from you!
### Approach
>Syntax: `stdout | tee <file1> <file2> ...`
### Commands
```
/challenge/pwn | tee test | /challenge/college
cat test
/challenge/pwn --secret 8iiCc-TO | /challenge/college
```
### Flag
`pwn.college{8iiCc-TO3geHTKykLIus9N9NTNL.dFjM5QDLyUzM2czW}`

## Writing to Multiple programs
### Description
In this challenge, we have `/challenge/hack`, `/challenge/the`, and `/challenge/planet`. Run the `/challenge/hack` command, and duplicate its output as input to both the `/challenge/the` and the `/challenge/planet` commands!
### Commands
`/challenge/hack | tee >(/challenge/planet) | /challenge/the`
### Flag
`pwn.college{YXy49plD0cpHEKMgwhstSRn-C63.dBDO0UDLyUzM2czW}`

## Split piping stderr and stdout
### Description
In this challenge, you have:

`/challenge/hack`: this produces data on stdout and stderr
`/challenge/the`: you must redirect `hack`'s stderr to this program
`/challenge/planet`: you must redirect `hack`'s stdout to this program  
Go get the flag!
### Approach
We need to redirect output of `/challenge/hack` as input into `/challenge/planet` and its error into `/challenge/the`
### Commands
`/challenge/hack 2> >(/challenge/the) > >(/challenge/planet)`
### Flag
`pwn.college{oe3FZvpXPW-jkMxabYYbHZgwavv.dFDNwYDLyUzM2czW}`

