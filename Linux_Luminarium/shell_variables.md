# Shell Variables

## Printing Variables
### Description
Have your shell print out the `FLAG` variable and solve this challenge!
### Approach
`echo $<varname>` prints out a variable.  
### Commands
`echo $FLAG`
### Flag
`pwn.college{g8Vp-FazdDcbCwnitP2rU-EkUFE.ddTN1QDLyUzM2czW}`

## Setting variables
### Description
To solve this level, you must set the `PWN` variable to the value `COLLEGE`.
### Approach
>**Notes**: There are no spaces around the `=`.  
If you put spaces (e.g., `VAR = 1337`), the shell won't recognize a variable assignment and will, instead, try to run the `VAR` command (which does not exist).  
This uses `VAR` and not `$VAR`: the `$` is only prepended to access variables. In shell terms, this prepending of `$` triggers what is called variable expansion.
### Commands
`PWN=COLLEGE`
### Flag
`pwn.college{MGMecklHOkYUM_AxKOyksJ5s6KP.dlTN1QDLyUzM2czW}`

## Multi-Word Variables
### Description
In this level, you'll need to set the variable `PWN` to `COLLEGE YEAH`.
### Approach
>**Notes**: When the shell sees a space, it ends the variable assignment and interprets the next word as a command.  
eg. `VAR="1337 SAUCE"`.  To set VAR to 1337 SAUCE, you need to quote it.  
### Commands
`PWN="COLLEGE YEAH"`
### Flag
`pwn.college{Mh26FruzZAog5bPj0SFRgQOHHH9.dBjN1QDLyUzM2czW}`

## Exporting Variables
### Description
In this challenge, you must invoke `/challenge/run` with the `PWN` variable exported and set to the value `COLLEGE`, and the `COLLEGE` variable set to the value `PWN` but not exported (e.g., not inherited by `/challenge/run`). 
### Approach
First assign PWN to COLLEGE and export, then assign COLLEGE to PWN and invoke the challenge to confirm.  
### Commands
```
export PWN=COLLEGE
COLLEGE=PWN
/challenge/run
```
### Flag
`pwn.college{I6VR6f0dCwf6Bwknf6iXyx6eXEE.dJjN1QDLyUzM2czW}`

## Printing Exported Variables
### Description
Try the `env` command: it'll print out every exported variable set in your shell, and you can look through that output to find the `FLAG` variable!
### Approach
Pipe the output of `env` and `grep` for the flag.  
### Commands
`env | grep pwn.college`
### Flag
`pwn.college{IkdvoVDqV0PFN1cTZd_guJJqGky.dhTN1QDLyUzM2czW}`

## Storing Command Output
### Description
Read the output of the `/challenge/run` command directly into a variable called `PWN`, and it will contain the flag!
### Commands
```
PWN=$(/challenge/run)
echo $PWN
```
### Flag
`pwn.college{cIMObc1zK-LsAFH337yrGDNoQu0.dVzN0UDLyUzM2czW}`

## Reading Input
### Description
In this challenge, your job is to use `read` to set the `PWN` variable to the value `COLLEGE`. 
### Approach
>Syntax of read: `read -p "Text" <varname>`

### Commands
```
read PWN
COLLEGE
```
### Flag
`pwn.college{Y9kIotu5whEGiZ52RR1HZ2aS9JZ.dhzN1QDLyUzM2czW}`

## Reading Files
### Description
Read `/challenge/read_me` into the `PWN` environment variable, and we'll give you the flag! The `/challenge/read_me` will keep changing, so you'll need to read it right into the `PWN` variable with one command!
### Approach
>**Notes**: Two ways to read files:  
```
echo "text" > <filename>  
<varname>=$(cat <filename>)  
echo $<varname>
```

```
echo "text" > <filename>
read <varname> < <filename>
echo $<varname>
```
>The latter is better since here, the filename is refirected into stdin of read and when read reads into varname, it reads from the file.  

### Commands
`read PWN < /challenge/read_me`
### Flag
`pwn.college{stbMizxOolcU3-XF5L8eBENCpRy.dBjM4QDLyUzM2czW}`