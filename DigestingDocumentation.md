# Reading Documentation for Arguments
This challenge serves as a basic exercise in reading a program's documentation to determine the correct command-line arguments to use. 
## My Solve
Flag: pwn.college{I4tw1HpGpPVlaI7RqgSghkSpkuf.QX0ITO0wCM3AzNzEzW}

The goal was to run the executable /challenge/challenge correctly to get the flag. The provided documentation was very clear: the program required the specific argument --giveflag. By simply appending this argument to the command, the program executed as intended and printed the flag.

```
hacker@man~learning-from-documentation:~$ /challenge/challenge
Incorrect usage! You must pass an argument to me (read the challenge 
description for details).
hacker@man~learning-from-documentation:~$ /challenge/challenge --giveflag
Correct argument! Here is your flag:
pwn.college{I4tw1HpGpPVlaI7RqgSghkSpkuf.QX0ITO0wCM3AzNzEzW}
```

## What I Learned
I learned how to correctly pass arguments to command-line programs based on their documentation. The key lesson was understanding the common pattern where an option (like --printfile) is followed by a value (like /flag). This syntax, command --option value, is used by a vast number of Linux tools, and knowing how to read documentation and apply it is a critical skill for using the command line effectively.

## References
None

# Using Command-Line Arguments
This challenge focuses on the fundamental concept of passing options and arguments to a command-line program. 💬
## My Solve
Flag: pwn.college{gqAgI67tPq8ekDPhqvBYNO5f1LS.QX1ITO0wCM3AzNzEzW}

The goal was to get the /challenge/challenge executable to print the flag. According to its documentation, the program required a --printfile argument, which in turn needed a file path to be specified immediately after it.
To solve this, I constructed the command exactly as the documentation described, providing the path to the standard flag file, /flag, as the argument for --printfile.

```
hacker@man~learning-complex-usage:~$ /challenge/challenge --printfile /flag
Correct argument! Here is the /flag file:
pwn.college{gqAgI67tPq8ekDPhqvBYNO5f1LS.QX1ITO0wCM3AzNzEzW}
```

## What I Learned
I learned how to correctly pass arguments to command-line programs based on their documentation. The key lesson was understanding the common pattern where an option (like --printfile) is followed by a value (like /flag). This syntax, command --option value, is used by a vast number of Linux tools, and knowing how to read documentation and apply it is a critical skill for using the command line effectively.

## References
None

# Reading Manual Pages with man
This challenge introduces the man (manual) command, the traditional way to access comprehensive documentation for command-line tools on Linux systems. 📖
## My Solve
Flag: pwn.college{8Wj3Hnc46vShf57cil4dd1ki-Mp.QX0EDO0wCM3AzNzEzW}

To solve this challenge, I needed to find a secret command-line option for the /challenge/challenge program. I used the man command to look up its documentation, which revealed the secret argument. After reading the manual, I quit the viewer and ran the program with the newly discovered option to get the flag.

```
hacker@man~reading-manuals:~$ man challenge
hacker@man~reading-manuals:~$ /challenge/challenge --jncvhf 834
Correct usage! Your flag: pwn.college{8Wj3Hnc46vShf57cil4dd1ki-Mp.QX0EDO0wCM3AzNzEzW}
```

## What I Learned
I learned that the man command is the primary way to access in-depth documentation for Linux commands. Unlike the often brief output from --help, man pages provide detailed information typically organized into standard sections like NAME, SYNOPSIS, and DESCRIPTION. Knowing how to open, read (using arrow keys), and quit (q) a man page is a fundamental skill for becoming proficient with the Linux command line.

## References
None

# Searching in man Pages
This challenge teaches how to efficiently navigate and find information within man pages by using the built-in search functionality. 🔎
## My Solve
Flag: pwn.college{opLr_VHUa6l6vY5wIhvNRZfNl17.QX1EDO0wCM3AzNzEzW}

To find the secret option in this challenge, I used the search feature within the man page instead of reading it from top to bottom. After opening the manual with man challenge, I pressed / to initiate a forward search and typed the keyword "flag". This instantly jumped me to the relevant section that described the secret command-line argument. After quitting the viewer, I used that argument to get the flag.

```
hacker@man~searching-manuals:~$ man challenge
hacker@man~searching-manuals:~$ /challenge/challenge --mncrcmj
Initializing...
Correct usage! Your flag: pwn.college{opLr_VHUa6l6vY5wIhvNRZfNl17.QX1EDO0wCM3AzNzEzW}
```

## What I Learned
I learned that man pages have a powerful built-in search function that makes finding specific information much faster. The key commands are:
/: Search forward through the text.
?: Search backward through the text.
n: Jump to the next search result.
N: Jump to the previous search result (Shift + n).
Using search is far more efficient than manually reading long documentation pages, especially when you know a keyword related to what you're looking for.

## References
None

# Searching for man Pages with man -k
This challenge teaches how to search the entire man page database for a keyword to find a manual page whose name you don't know. 🗃️
## My Solve
Flag: pwn.college{I7wZObzPQWgGDQ8xdij4_RxNR-p.QX2EDO0wCM3AzNzEzW}

This was a multi-step challenge. The man page for the executable was randomly named, so I couldn't open it directly. First, I read the manual for man itself by running man man. From this, I learned that the -k option could search the descriptions of all man pages for a keyword.
I then used man -k challenge to find the correct, randomly-named manual. Once I had its name, I could open it with man, find the secret argument, and use it with the /challenge/challenge executable to get the flag.

```
hacker@man~searching-for-manuals:~$ man -k challenge
wbzgxdijxp (1)       - print the flag!
hacker@man~searching-for-manuals:~$ man wbzgxdijxp
hacker@man~searching-for-manuals:~$ /challenge/challenge --wbzgxd 784
Correct usage! Your flag: pwn.college{I7wZObzPQWgGDQ8xdij4_RxNR-p.QX2EDO0wCM3AzNzEzW}
```

## What I Learned
I learned a powerful technique for discovering commands and documentation. By using man -k <keyword> (which is equivalent to the apropos command), I can search for man pages related to a topic, even if I don't know the exact command name. This is extremely useful when I know what I want to accomplish (e.g., "compress a file") but don't know the specific tool to use. It transforms man from just a reference manual into a command discovery tool.

## References
None

# Getting Help with --help
This challenge teaches how to get documentation directly from an executable by using the standard --help argument. 🙋
##My Solve
Flag: pwn.college{UiawbGFLk2zm28FqSCA9qmioLon.QX3IDO0wCM3AzNzEzW}

In this challenge, the documentation was not provided upfront. The goal was to discover the correct argument by asking the program for instructions itself. I used the standard --help flag, which prompted the executable to print its own usage information. This help message revealed the secret argument needed to get the flag, which I then used to solve the challenge.

```
hacker@man~helpful-programs:~$ /challenge/challenge --help
usage: a challenge to make you ask for help [-h] [--fortune] [-v] [-g GIVE_THE_FLAG] [-p]

optional arguments:
  -h, --help            show this help message and exit
  --fortune             read your fortune
  -v, --version         get the version number
  -g GIVE_THE_FLAG, --give-the-flag GIVE_THE_FLAG
                        get the flag, if given the correct value
  -p, --print-value     print the value that will cause the -g option to give you the flag
hacker@man~helpful-programs:~$ /challenge/challenge -p
The secret value is: 228
hacker@man~helpful-programs:~$ /challenge/challenge -g 228
Correct usage! Your flag: pwn.college{UiawbGFLk2zm28FqSCA9qmioLon.QX3IDO0wCM3AzNzEzW}
```

## What I Learned
I learned that the most direct way to understand a command-line program is often to ask it for help. Most programs adhere to the convention of accepting a --help (or sometimes -h) argument to display their own documentation, including a list of valid options and how to use them. This is the first thing I should try when encountering an unfamiliar command.

## References
None

# Getting Help for Shell Builtins
This challenge explains the difference between external programs and shell builtins and introduces the help command for getting documentation on the latter. 🐚
## My Solve
Flag: pwn.college{4LPERBJnGbwqOxWu__f2LCngNWD.QX0ETO0wCM3AzNzEzW}

In this challenge, the challenge command was a shell builtin, not a regular executable. This meant that man challenge and challenge --help would not work. The correct way to get its documentation was by using the help command built into the shell.
I ran help challenge, which printed the usage instructions and revealed the secret argument needed to get the flag. I then ran the command with that argument to complete the challenge.


```
hacker@man~help-for-builtins:~$ help challenge
challenge: challenge [--fortune] [--version] [--secret SECRET]
    This builtin command will read you the flag, given the right arguments!
    
    Options:
      --fortune         display a fortune
      --version         display the version
      --secret VALUE    prints the flag, if VALUE is correct

    You must be sure to provide the right value to --secret. That value
    is "4LPERBJn".
hacker@man~help-for-builtins:~$ /challenge/challenge --fortune
bash: /challenge/challenge: No such file or directory
hacker@man~help-for-builtins:~$ --fortune
bash: --fortune: command not found
hacker@man~help-for-builtins:~$ challenge --fortune
The gentlemen looked one another over with microscopic carelessness.
hacker@man~help-for-builtins:~$ challenge --version
I'm exactly the version I need to be!
hacker@man~help-for-builtins:~$ challenge --secret 4LPERBJn
Correct! Here is your flag!
pwn.college{4LPERBJnGbwqOxWu__f2LCngNWD.QX0ETO0wCM3AzNzEzW}
```

## What I Learned
I learned that not all commands are standalone programs; some are built into the shell itself for efficiency and are called builtins (e.g., cd, exit, echo). These builtins do not have their own man pages. To get documentation for them, you must use the shell's own help command. This is a key distinction for understanding how the shell works.

# References
None
