# File Globbing


## Matching with *
### Description
Starting from your home directory, change your directory to `/challenge`, but use globbing to keep the argument you pass to `cd` to at most four characters! Once you're there, run `/challenge/run` for the flag!
### Approach
>**Notes:** When it encounters a `*` character in any argument, the shell will treat it as "wildcard" and try to replace that argument with any files that match the pattern.
>The `*` matches any part of the filename except for `/` or a leading `.` character.
### Commands
```
cd /cha*
/challenge/run
```
### Flag
`pwn.college{0ppP_5VkzN_Hm_t1scPDUeRFRbk.dFjM4QDLyUzM2czW}`

## Matching with ?
### Description
Starting from your home directory, change your directory to `/challenge`, but use the `?` character instead of `c` and `l` in the argument to `cd`! Once you're there, run `/challenge/run` for the flag!
### Approach
>**Notes**: When it encounters a `?` character in any argument, the shell will treat it as single-character wildcard. This works like `*`, but only matches one character.
### Commands
```
cd /?ha??enge
/challenge/run
```
### Flag
`pwn.college{gWtymkKHg5dpIvhbZWZd3K8S7PM.dJjM4QDLyUzM2czW}`

## Matching with []
### Description
We've placed a bunch of files in `/challenge/files`. Change your working directory to `/challenge/files` and run `/challenge/run` with a single argument that bracket-globs into `file_b`, `file_a`, `file_s`, and `file_h`!
### Approach
>**Notes**: The square brackes are, essentially, a limited form of `?`, in that instead of matching any character, `[]` is a wildcard for some subset of potential characters, specified within the brackets.
### Commands
```
cd /challenge/files
/challenge/run file_[bash]
```
### Flag
`pwn.college{8MvMlLgCgtekqhT25kBkSdrn0GN.dNjM4QDLyUzM2czW}`

## Matching paths with []
### Description
We've placed a bunch of files in `/challenge/files`. Starting from your home directory, run `/challenge/run` with a single argument that bracket-globs into the absolute paths to the `file_b`, `file_a`, `file_s`, and `file_h` files!

### Commands
`/challenge/run /challenge/files/file_[bash]`
### Flag
`pwn.college{EXuXFrpYnh8pMuA2D34mxKmOlzi.dRjM4QDLyUzM2czW}`

## Mixing Globs
### Description
Now, let's put the previous levels together! We put a few happy, but diversely-named files in `/challenge/files`. Go `cd` there and, using the globbing you've learned, write a single, short (6 characters or less) glob that will match the files "challenging", "educational", and "pwning"!
### Approach
Inorder to get only the three given words as result in a glob of minimum characters, we can use [cep]*, since no other word starts with these letters(unique identification).  
There is a `run` file in the `challenge` directory, which on execution with the glob as an argument, gives the flag.  
### Commands
```
cd /challenge/files
ls [cep]*
cd ..
cd files
/challenge/run [cep]*
``` 
### Flag
`pwn.college{YaTX6x1wQC_OJKxCzzbojyzsvUP.dVjM4QDLyUzM2czW}`

## Exclusionary Globbing
### Description
Go forth to `/challenge/files` and run `/challenge/run` with all files that don't start with `p`, `w`, or `n`!
### Approach
>**Notes**: If the first character in the brackets is a `!` or (in newer versions of bash) a `^`, the glob inverts, and that bracket instance matches characters that aren't listed.  
### Commands
```
cd /challenge/files
/challenge/run [!pwn]*
```
### Flag
`pwn.college{o7GwgWssukbpkrWtYtce7MX7ASQ.dZjM4QDLyUzM2czW}`