# Digesting Documentation

## Learning from Documentation
### Description
The program for this challenge is `/challenge/challenge`, and you'll need to invoke it properly in order for it to give you the flag. Let's pretend that this is its documentation:

Welcome to the documentation for `/challenge/challenge`! To properly run this program, you will need to pass it the argument of `--giveflag`. Good luck!

Given that knowledge, go get the flag!
### Commands
`/challenge/challenge --giveflag`
### Flag
`pwn.college{06-CpkpvD7Peoq8aXkbxDE-AfKV.dRjM5QDLyUzM2czW}`

## Learning Complex Usage
### Description
Here is this level's documentation for `/challenge/challenge`:

Welcome to the documentation for `/challenge/challenge`! This program allows you to print arbitrary files to the terminal, when given the `--printfile` argument. The argument to the `--printfile` argument is the path of the flag to read. For example, `/challenge/challenge --printfile /challenge/DESCRIPTION.md` will print out the description of the level!

Given that documentation, go get the flag!
### Commands
`challenge/challenge --printfile /flag`
### Flag
`pwn.college{4ZmTT5XvZ9AWnLbc5qYS-z5sVax.dVjM5QDLyUzM2czW}`

## Reading manuals
### Description
The challenge in this level has a secret option that, when you use it, will cause the challenge to print the flag. You must learn this option through the man page for `challenge`!
### Approach
Go according to the instructions in the manual page. 
### Commands
```
man challenge
/challenge/challenge --sxbetz 242
```
### Flag
` pwn.college{sNXS2x4WQb2etz2Ubhh5biF_nZ7.dRTM4QDLyUzM2czW}`

## Searching Manuals
### Description
Find the option that will give you the flag by reading the `challenge` man page.
### Approach
>**Notes**: You can scroll man pages with the arrow keys (and PgUp/PgDn) and search with `/`. After searching, you can hit `n` to go to the next result and `N` to go to the previous result. Instead of `/`, you can use `?` to search backwards!
Look for the word `flag` in the man page 
### Commands
```
man challenge
/flag 
```
### Flag
` pwn.college{shffFFkr2nWfRj59-rEjCIz6M6y.dVTM4QDLyUzM2czW}`

## Searching for Manuals
### Description
This level is tricky: it hides the manpage for the challenge by randomizing its name. Luckily, all of the man pages are gathered in a searchable database, so you'll be able to search the man page database to find the hidden challenge man page! To figure out how to search for the right man page, read the `man` page manpage by doing: `man man`!
### Approach
On reading the man page, it is clear that `-K` option will let us search for the page using keywords.  

### Commands
```
man -K challenge
/challenge/challenge --khxugg 817
```
### Flag
`pwn.college{8UkhxJ1N7QVuggs-6jHUmBrf4Hq.dZTM4QDLyUzM2czW}`

## Helpful Programs
### Description
In this level, you will practice reading a program's documentation with --help. Try it out!
### Approach
>**Notes:** Some programs don't have a man page, but might tell you how to run them if invoked with a special argument. Usually, this argument is `--help`, but it can often be `-h` or, in rare cases, `-?`, `help`, or other esoteric values like `/?` (though that latter is more frequently encountered on Windows).
### Commands
```
/challenge/challenge --help
/challenge/challenge -p
/challenge/challenge -g 749
```
### Flag
`pwn.college{MkLR7H4cDylVGTS928zYz_Knh3r.ddjM4QDLyUzM2czW}`

## Help for Builtins
### Description
In this challenge, we'll practice using help to look up `help` for builtins. This challenge's `challenge` command is a shell builtin, rather than a program. Like before, you need to lookup its help to figure out the secret value to pass to it!
### Approach
>**Notes**: Some commands, rather than being programs with man pages and help options, are built into the shell itself. These are called builtins. Builtins are invoked just like commands, but the shell handles them internally instead of launching other programs. You can get a list of shell builtins by running the builtin `help`
### Commands
```
help challenge
challenge --secret MRBQJ9IL
```
### Flag
`pwn.college{MRBQJ9ILJMTnoe4x3jeKeiwiUlU.dRTM5QDLyUzM2czW}`
