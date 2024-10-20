# Processes and Jobs

## Listing processes
### Description
In this level, I have once again renamed `/challenge/run` to a random filename, and this time made it so that you cannot `ls` the `/challenge` directory! But I also launched it, so can find it in the running process list, figure out the filename, and relaunch it directly for the flag!
### Approach
>**Notes**:   
`ps` command: Lists running processes in the terminal.  
`ps -ef`: Shows all processes with detailed info (standard format).  
`ps aux`: Lists processes with CPU and memory usage (BSD format).  
Common columns:  
`PID`: Process ID.
`TTY`: Terminal of the process.
`TIME`: CPU time used.
`STIME/START`: start time of the process  
`CMD/COMMAND`: What process is doing.
`ps -ef` also includes: `PPID` (Parent Process ID, (who started the process)).
`ps aux` also includes: `%CPU and %MEM` (resource usage).

Redirecting the output of `ps` to a file solves the issue of the commands getting truncated.  
### Commands
```
ps aux > command
cat command
/challenge/6577-run-27751
```
### Flag
`pwn.college{4GpfaZ_Q3Q3h9afP1ba8XxDFHSk.dhzM4QDLyUzM2czW}`

## Killing Processes
### Description
In this challenge, `/challenge/run` will refuse to run while `/challenge/dont_run` is running! You must find the `dont_run` process and kill it. If you fail, `pwn.college` will disavow all knowledge of your mission.
### Approach
>**Notes**: 
`kill` command: Terminates processes using their PID.  
To find PID: `ps aux | grep <process_name>`  
Syntax: `kill <PID>`  
To check: Use `ps` again to see if the process is gone  
### Commands
```
ps aux | grep /challenge/dont_run
kill 73
ps aux | grep ?challenge/dont_run
/challenge/run
```
### Flag
`pwn.college{gLFQz6RwStETOG7kKiVEgiCq-Vu.dJDN4QDLyUzM2czW}`

## Interrupting Processes
### Description
 `/challenge/run` will refuse to give you the flag until you interrupt it.
### Approach
>**Notes**:   
`Ctrl-C`: Interrupts and stops a process in the terminal.  
Sends `SIGINT` signal: Tells the process to exit cleanly.  
Use case: When a process is running in the terminal and needs to be stopped quickly.  
Faster than kill for foreground processes.  
### Commands
```
/challenge/run
<Ctrl+C>
```
### Flag
`pwn.college{swGqAKyFuWU_NRHB3_ufCjsiQzn.dNDN4QDLyUzM2czW}`

## Suspending processes
### Description
This level's `run` wants to see another copy of itself running and using the same terminal. How? Use the terminal to launch it, then suspend it, then launch another copy while the first is suspended!
### Approach
>**Notes**:   
`Ctrl-Z`: Suspends a process and moves it to the background.  
Sends `SIGTSTP` signal: Pauses the process without killing it.  
Use `jobs` command to view paused processes.
Useful when you want to pause and resume later instead of killing the process.
### Commands
```
/challenge/run
<Ctrl+Z>
/challenge/run
```
### Flag
`pwn.college{gFZp7K7BpN07vxeD46Nlor_EdLK.dVDN4QDLyUzM2czW}`

## Resuming Processes
### Description
This challenge's run needs you to suspend it, then resume it.
### Approach
>**Notes**:  
`fg`: Resumes suspended processes and puts them in the foreground.  
Use `jobs` to list suspended/background processes.
To resume a specific process: `fg %<job_number>`
Brings process back so you can interact with it in the terminal.
### Commands
```
/challenge/run
<Ctrl+Z>
fg
```
### Flag
`pwn.college{cNxPOyaXur9N6oI0tCRh0Oq-BUJ.dZDN4QDLyUzM2czW}`

## Backgrounding processes
### Description
This level's `run` wants to see another copy of itself running, not suspended, and using the same terminal. How? Use the terminal to launch it, then suspend it, then background it with `bg` and launch another copy while the first is running in the background!
### Approach
>**Notes**:  
`bg`: Resumes suspended processes in the background.  
Use `jobs`: To list suspended or running background processes.  
Run specific process: `bg %<job_number>`  
Keeps process running in the background while freeing up your terminal for other commands.  
### Commands
```
/challenge/run
<Ctrl+Z>
bg
/challenge/run
```
### Flag
`pwn.college{0Kxncc--uf_mq9hOgJ2FjQWSuA2.ddDN4QDLyUzM2czW}`

## Foregrounding processes
### Commands
```
/challenge/run
<Ctrl+Z>
bg
fg
```
### Flag
`pwn.college{c3eS7kunnidfV8C8_05NJ8n3rRb.dhDN4QDLyUzM2czW}`

## Starting background processes
### Description
Launch `/challenge/run` backgrounded for the flag
### Commands
`/challenge/run &`
### Flag
`pwn.college{Ee6cgHh5zGvITMtzHZnTeIyZsA9.dlDN4QDLyUzM2czW}`

## Process Exit Codes
### Description
In this challenge, you must retrieve the exit code returned by `/challenge/get-code` and then `run /challenge/submit-code` with that error code as an argument.
### Approach
>**Notes**:  
Exit code: A number that indicates if a command succeeded or failed.  
`0` = Success, Non-zero = Failure (usually `1`).  
Check exit code: Use `echo $?` to see the exit code of the last command.  
Helps in debugging or controlling script logic based on success/failure.  
### Commands
```
/challenge/get-code
/challenge/submit-code 177
```
### Flag
`pwn.college{Qy-MehD49bs_zhXUhDl-D-RtoxT.dljN4UDLyUzM2czW}`