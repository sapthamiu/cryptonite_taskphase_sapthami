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
In this challenge, I've put a hundred thousand lines of text into the `/challenge/data.txt` file. Grep it for the flag!

HINT: The flag always starts with the text `pwn.college`
### Approach
>**Notes**:   
>Syntax of `grep`: `grep SEARCH_STRING /path/to/file`  

Since the flag always starts with `pwn.college`, we can search for it in the given file using `grep` command.  
### Commands
`grep pwn.college /challenge/data.txt`
### Flag
`pwn.college{kw3yOji3mMrO5sDDJQtA9ytPlWZ.ddTM4QDLyUzM2czW}`

## Listing files
### Description
In this challenge, we've named `/challenge/run` with some random name! List the files in `/challenge` to find it.
### Approach
Use `ls` to find the files under `/challenge`.  
The `run` file has been renamed to `22530-renamed-run-4567`
### Commands
```
ls /challenge
/challenge/22530-renamed-run-4567
```
### Flag
`pwn.college{kKqwYMYeYWa3774q_PZe8hpWJtc.dhjM4QDLyUzM2czW}`

## Touching Files
### Description
In this level, please create two files: `/tmp/pwn` and `/tmp/college`, and run `/challenge/run` to get your flag!
### Approach
Create the two files and run the challenge as instructed.  
### Commands
```
touch /tmp/pwn
touch /tmp/college
/challenge/run
```
### Flag
`pwn.college{ABAx9OKdh5rw87QiaUKIugVcKJ2.dBzM4QDLyUzM2czW}`

## Removing files
### Description
This challenge will create a `delete_me` file in your home directory! Delete it, then run `/challenge/check`, which will make sure you've deleted it and then give you the flag!
### Approach
Instructions are clear in the description.  
We need to delete the given file using `rm` command.  
### Commands
```
rm delete_me
/challenge/check
```
### Flag
`pwn.college{Y6o8OqUpr7oXZuNcUJYuRMBwo4k.dZTOwUDLyUzM2czW}`

## Hidden Files
### Description
Go find the flag, hidden as a dot-prepended file in `/`.
### Approach
Upon using the `ls -a` command in the root folder, we get a file `.flag-221162043716653`.  
Reading this file gives the flag.  
### Commands
```
ls -a /
cat /.flag-221162043716653
```
### Flag
`pwn.college{s6VGkJ49YRj5yhlzs4u3LzY62Fl.dBTN4QDLyUzM2czW}`

## An Epic Filesystem Quest
### Description
In this challenge, I have hidden the flag! Here, you will use `ls` and `cat` to follow my breadcrumbs and find it! Here's how it'll work:

0. Your first clue is in `/`. Head on over there.
1. Look around with `ls`. There'll be a file named HINT or CLUE or something along those lines!
2. `cat` that file to read the clue!
Depending on what the clue says, head on over to the next directory (or don't!).
Follow the clues to the flag!

### Approach
Proceed according to the instructions in every clue
### Commands
```
cd /
ls
cat SNIPPET

cd  /usr/lib/python3/dist-packages/scipy/linalg/tests/data
ls
cat CUE

cd  /opt/capstone/tests/MC/AArch64
ls
cat GIST

cd  /opt/linux/linux-5.4/include/config/ext4/fs
ls
cat LEAD

ls /opt/linux/linux-5.4/fs/adfs
cat /opt/linux/linux-5.4/fs/adfs/TIP

ls -a  /opt/kropr/.git/objects/ea
cat  /opt/kropr/.git/objects/ea/.NOTE

ls /opt/linux/linux-5.4/Documentation/devicetree/bindings/media/i2c
cat /opt/linux/linux-5.4/Documentation/devicetree/bindings/media/i2c/NUGGET-TRAPPED

ls -a  /usr/share/racket/pkgs/drracket-plugin-lib/drracket/compiled
cat  /usr/share/racket/pkgs/drracket-plugin-lib/drracket/compiled/.MEMO

ls /usr/share/racket/collects/version
cat /usr/share/racket/collects/version/WHISPER
```
### Flag
`pwn.college{YsJNoVLmuRCpnU4Lp2Tbgl7F2t1.dljM4QDLyUzM2czW}`

## Making Directories
### Description
Go forth and create a `/tmp/pwn` directory and make a college file in it! Then run `/challenge/run`, which will check your solution and give you the flag!
### Approach
### Commands
```
mkdir /tmp/pwn
cd /tmp/pwn
touch college
/challenge/run
```
### Flag
`pwn.college{Ec8b0VrCPFqH4rSDjUr-sLkam9t.dFzM4QDLyUzM2czW}`

## Finding files
### Description
I've hidden the flag in a random directory on the filesystem. It's still called flag. Go find it!

Several notes. First, there are other files named flag on the filesystem. Don't panic if the first one you try doesn't have the actual flag in it.  
Second, there're plenty of places in the filesystem that are not accessible to a normal user. These will cause find to generate errors, but you can ignore those; we won't hide the flag there!  
Finally, find can take a while; be patient!
### Approach
search all the available directories 
### Commands
```
find / -name flag
ls /usr/local/lib/python3.8/dist-packages/pwnlib/flag
ls /usr/lib/R/library/tcltk/exec/flag
cat /usr/lib/R/library/tcltk/exec/flag
```
### Flag
`pwn.college{42c4DPpKshjQ_gbQK1yy16teaKJ.dJzM4QDLyUzM2czW}`

## Linking Files
### Description
In this challenge, we will learn about symbolic links (also also known as symlinks).  
In this level the flag is in `/flag`, but `/challenge/catflag` will instead read out `/home/hacker/not-the-flag`. Use the symlink, and fool it into giving you the flag!
### Approach
>**Notes**: If you want two programs to access the same data, but the programs expect that data to be in two different locations, we use `links`.  
>Two types: 1. hard link 2. soft(symbolic link)  
>A hard link is an alternate address that indexes that data  
>A soft/symbolic link contains the original file name. When you access the symbolic link, Linux will realize that it is a symbolic link, read the original file name, and then automatically access that file.  
>Syntax: `ln -s <original filepath> <link path>`
First create the symlink and then run `/challenge/catflag`  
### Commands
```
ln -s /flag /home/hacker/not-the-flag
/challenge/catflag
```
### Flag
`pwn.college{IBTWrHzP0YtUMa6WKQ9vGGfdpim.dlTM1UDLyUzM2czW}`