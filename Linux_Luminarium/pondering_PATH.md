# Pondering PATH

## The PATH variable
### Description
In this level, you will disrupt the operation of the `/challenge/run` program. This program will DELETE the flag file using the `rm` command. However, if it can't find the `rm` command, the flag will not be deleted, and the challenge will give it to you! Thus, you must make it so that `/challenge/run` also can't find the `rm` command!
### Approach
>**Notes**:  
PATH variable stores directories where the shell looks for programs.  
eg. `PATH="/bin:/usr/bin"`  
Commands cannot be found if the PATH is made empty(`PATH=""`)
### Commands
```
PATH=""
/challenge/run
```
### Flag
`pwn.college{ccZ7xicZzmRAU5M_pgSQehcVSAv.dZzNwUDLyUzM2czW}`

## Setting PATH
### Description
This level's `/challenge/run` will run the win command via its bare name, but this command exists in the `/challenge/more_commands/` directory, which is not initially in the PATH. The `win` command is the only thing that `/challenge/run` needs, so you can just overwrite `PATH` with that one directory.
### Commands
```
PATH="/challenge/more_commands"
/challenge/run
```
### Flag
`pwn.college{sQ5_gBEot2tCmbrZTiINQAEdQ1t.dVzNyUDLyUzM2czW}` 

## Adding Commands
### Description
Previously, the `win` command that `/challenge/run` executed was stored in `/challenge/more_commands`. This time, `win` does not exist! Recall the final level of Chaining Commands, and make a shell script called `win`, add its location to the `PATH`, and enable /challenge/run to find it!
### Approach
First create a script `win` and write the commands to read the flag in it.  
Then give execute permissions to the script and set the PATH to home directory.  
Now invoke `/challenge/run` which runs the win as a command.  
### Commands
```
cat > win
read flag < /flag
echo $flag
<Ctrl+D>
chmod a+x win
PATH="/home/hacker"
/challenge/run
```
### Flag
`pwn.college{E1t36i-rnRfV5teoNspbyeoopKZ.dZzNyUDLyUzM2czW}`

## Hijacking Commands
### Description
This challenge is almost the same as the first challenge in this module. Again, this challenge will delete the flag using the `rm` command. But unlike before, it will not print anything out for you.

How can you solve this? You know that `rm` is searched for in the directories listed in the `PATH` variable. You have experience creating the `win` command when the previous challenge needed it. What else can you create?
### Approach
Since we dont want the `rm` to delete the flag, we can create our own version of `rm` command that will read and print the flag instead.  
Replace the PATH variable with home directory to run this version instead of the actual `rm`.
### Commands
```
cat > rm
read flag < /flag
echo $flag
<Ctrl+D>
chmod a+x rm
PATH="/home/hacker"
/challenge/run
```
### Flag
`pwn.college{YrBBv_AB14t89Th-Wj-2Wy7LCRI.ddzNyUDLyUzM2czW}`