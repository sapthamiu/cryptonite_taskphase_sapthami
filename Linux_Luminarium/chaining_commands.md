# Chaining Commands

## Chaining with Semicolons
### Description
In this level, you must run `/challenge/pwn` and then `/challenge/college`, chaining them with a semicolon.  
### Commands
`/challenge/pwn; /challenge/college`
### Flag
`pwn.college{oB-Pt7vV62XpuDC9SyH04QrQ-aW.dVTN4QDLyUzM2czW}`

## Your First Shell Script
### Description
Same as last level, run `/challenge/pwn` and then `/challenge/college`, but this time in a shell script called `x.sh`, then run it with bash!
### Approach
First create a file called `x.sh` and write the commands to it.  
Then run the shellscript in another instance of the shell (bash).  
### Commands
```
cat > x.sh
/challenge/pwn
/challenge/college
<Ctrl+D>
bash x.sh
```
### Flag
`pwn.college{Qon4MsVm5sU2pTQidY0yZwKuibz.dFzN4QDLyUzM2czW}`

## Redirecting Script Output
### Description
In this level, we will practice piping (`|`) from your script to another program. Like before, you need to create a script that calls the `/challenge/pwn` command followed by the `/challenge/college` command, and pipe the output of the script into a single invocation of the `/challenge/solve` command!
### Commands
`bash x.sh | /challenge/solve`
### Flag
`pwn.college{krhdSePRq5EczQIWZaGataSccOR.dhTM5QDLyUzM2czW}`

## Executable Shell Scripts
### Description
Make a shellscript that will invoke `/challenge/solve`, make it executable, and run it without explicitly invoking `bash`!
### Approach
Create and write into the script, then change the file permissions with `chmod` and execute.  
### Commands
```
cat > solver.sh
/challenge/solve
<Ctrl+D>
chmod u+x solver.sh
./solver.sh
```
### Flag
`pwn.college{8D7Qls3ocjd3Q96M147b9YMOEVG.dRzNyUDLyUzM2czW}`