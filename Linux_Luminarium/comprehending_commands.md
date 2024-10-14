# Comprehending Commands

## cat: not the pet, but the command!
### Description
In this challenge, I will copy the flag to the `flag` file in your home directory (where your shell starts). Go read it with `cat`!
### Approach
>**Notes**:
>1. `cat <filename>` will read the content of files  
>2. `cat <filename1> <filename2>...<filename_n>` will concatenate multiple files  
>3. `cat` will read input from terminal and output it  

Read the flag file given in the home directory using `cat` command.  
### Commands
`cat flag`
### Flag
`pwn.college{YtEVJhAxxPKNN6jmS1UFuumSYeb.dFzN1QDLyUzM2czW}`

## catting absolute paths
### Description
In this level, I will not copy it to your home directory, but I will make it readable. You can read it with cat at its absolute path: `/flag`.
### Approach
Use absolute pathing to access the flag file.  
### Commands
`cat /flag`
### Flag
`pwn.college{8WTku3mzvxxWCeTi-jxCfHjw51k.dlTM5QDLyUzM2czW}`

## more catting practice
### Description
In this level, I'll put the flag in some crazy directory, and I will not allow you to change directories with `cd`, so no `cat flag` for you. You must retrieve the flag by absolute path, wherever it is.
### Approach
On entering the challenge, it says that the flag is located in the file `/usr/share/icons/flag`.

### Commands
`cat /usr/share/icons/flag`
### Flag
`pwn.college{AL3YmuMv5i9tUih4DRvu3xoy81W.dBjM5QDLyUzM2czW}`

## grepping for a needle in a haystack
### Description
### Approach
### Commands
### Flag