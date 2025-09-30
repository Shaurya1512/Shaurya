# Matching with `*`
This challenge introduces globbing, a feature that allows the shell to interpret special characters, such as *, to match filenames. 
## My Solve
Flag: pwn.college{Mbj09ihiC4gnYrknkBSW1V1nVwk.QXxIDO0wCM3AzNzEzW}

The goal was to change the directory to /challenge using a cd argument of four characters or fewer. The full path /challenge is too long. I used the * wildcard to create the short pattern /c*, which is only three characters. Since /challenge is the only directory in the root (/) that starts with the letter 'c', the shell correctly expanded this pattern to /challenge. After successfully changing directories, I ran the run executable to get the flag.

```
This challenge resets your working directory to /home/hacker unless you change 
directory properly...
This challenge resets your working directory to /home/hacker unless you change 
directory properly...
hacker@globbing~matching-with-:~$ cd /c*
hacker@globbing~matching-with-:/challenge$ ./run
You ran me with the working directory of /challenge! Here is your flag:
pwn.college{Mbj09ihiC4gnYrknkBSW1V1nVwk.QXxIDO0wCM3AzNzEzW}
```

## What I Learned
I learned that the shell performs globbing to expand patterns containing special characters into matching filenames. The * wildcard is the most common, matching any sequence of characters. This is an incredibly powerful tool for working with multiple files at once (e.g., rm *.tmp) or, as shown in this challenge, for creating a short and convenient way to specify a unique file or directory name.

## References
None

# Globbing with the `?` Wildcard
This challenge introduces the ? globbing character, which acts as a wildcard that matches exactly one character. 
## My Solve
Flag: pwn.college{gjIzng0gaUOzGaX3EkYnDKK0f5N.QXyIDO0wCM3AzNzEzW

The task was to navigate to the /challenge directory, but the cd command's argument had to use ? in place of the letters 'c' and 'l'. The ? wildcard matches any single character, so I constructed the pattern /?ha??enge to match /challenge.
The shell correctly expanded this pattern, allowing me to change into the correct directory. Once there, I executed the run program to get the flag.

```
This challenge resets your working directory to /home/hacker unless you change 
directory properly...
hacker@globbing~matching-with-:~$ cd /?ha??enge
hacker@globbing~matching-with-:/challenge$ ./run
You ran me with the working directory of /challenge! Here is your flag:
pwn.college{gjIzng0gaUOzGaX3EkYnDKK0f5N.QXyIDO0wCM3AzNzEzW}
```

## What I Learned
I learned that the ? wildcard is used in shell globbing to match exactly one of any character. This makes it more precise than the * wildcard, which matches any number of characters. The ? is useful when you need to match filenames that have a fixed length but vary by a few characters.
## References
None

# Globbing with Character Classes
This challenge introduces character classes using square brackets, a globbing feature that matches any single character from a specified set. 
## My Solve
Flag: pwn.college{QsWvmbqJX4R0d_Skoq8xOIp1X16.QXzIDO0wCM3AzNzEzW}

The task was to run argument that would expand to four specific files: file_b, file_a, file_s, and file_h. To do this, I used a character class that contained the unique final letter of each target file.
The pattern file_[bash] instructs the shell to find all files that start with file_ and are followed by exactly one character from the set b, a, s, or h. The shell expanded this single pattern into the four required filenames and passed them to the run program.

```
hacker@globbing~matching-with-:~$ cd /challenge/files
hacker@globbing~matching-with-:/challenge/files$ /challenge/run file_[bash]
You got it! Here is your flag!
pwn.college{QsWvmbqJX4R0d_Skoq8xOIp1X16.QXzIDO0wCM3AzNzEzW}
```

## What I Learned
I learned that square brackets [] create a character class in shell globbing, matching any single character that is explicitly listed inside them. This feature also supports ranges, such as [a-z] to match any lowercase letter or [0-9] to match any digit, making it useful for creating precise file matching patterns.

## References
None

# Matching paths with `[]`
This challenge demonstrates that globbing patterns can be applied to entire file paths, not just files in the current directory. 
## My Solve
Flag: pwn.college{wG9CHjh5NGYvI0HTkT6DMJqzlsr.QX0IDO0wCM3AzNzEzW}

The task was to run the /challenge/run program from my home directory with a single argument that expands into the absolute paths of four specific files located in /challenge/files.
The pattern /challenge/files/file_[bash] specified the absolute path to the files, with a character class [bash] to match the unique final letter of each target file. The shell expanded this single argument into the four required absolute paths and passed them to the program.

```
hacker@globbing~matching-paths-with-:~$ /challenge/run /challenge/files/file_[bash]
You got it! Here is your flag!
pwn.college{wG9CHjh5NGYvI0HTkT6DMJqzlsr.QX0IDO0wCM3AzNzEzW}
```

## What I Learned
I learned that globbing works on any part of a path. This makes globbing an extremely versatile tool for scripting and interacting with files located anywhere on the filesystem, regardless of your current working directory.

## References
None

# Multiple Globs
This challenge demonstrates how to use multiple * wildcards in a single pattern to match files containing a specific substring. 
## My Solve
Flag: pwn.college{E0ErAD8tsruliidiTExtUvUbCPp.0lM3kjNxwCM3AzNzEzW}

The goal was to provide a single, short (3 characters or less) globbing argument to the run program that would expand to all files in the directory containing the letter 'p'.
The solution was the pattern *p*. This three-character glob works because the first * matches any sequence of characters before the letter 'p', and the second * matches any sequence of characters after it. This effectively selects every filename that has a 'p' anywhere in it.

```
hacker@globbing~multiple-globs:~$ cd /challenge/files
hacker@globbing~multiple-globs:/challenge/files$ /challenge/run *p*
You got it! Here is your flag!
pwn.college{E0ErAD8tsruliidiTExtUvUbCPp.0lM3kjNxwCM3AzNzEzW}
```

## What I Learned
I learned to use the pattern *keyword* to perform a substring match. This is the standard way to find any file or directory that contains a specific word or character sequence anywhere in its name.

## References
None

# Mixing Globs
This challenge is a practical exercise in combining multiple globbing concepts to create a single, precise pattern that matches a specific set of files. 
## My Solve
Flag: pwn.college{UVLxwnY_OCrQdvZ68tMp4Dbnig6.QX1IDO0wCM3AzNzEzW}

The goal was to craft a single glob pattern, six characters or less, that would expand to match only "challenging", "educational", and "pwning".
The key was to identify the unique starting letter of each of the three files: c, e, and p. By creating a character class with these three letters, the pattern [cep]* perfectly isolates the target files. This glob tells the shell to match any file that begins with 'c', 'e', or 'p', followed by any number of other characters.

```
hacker@globbing~mixing-globs:~$ cd /challenge/files
hacker@globbing~mixing-globs:/challenge/files$ /challenge/run [cep]*
You got it! Here is your flag!
pwn.college{UVLxwnY_OCrQdvZ68tMp4Dbnig6.QX1IDO0wCM3AzNzEzW}
```
## What I Learned
I learned that when crafting a precise globbing pattern, finding the most restrictive common feature is crucial. In this case, the unique starting letter of each file was a much more reliable identifier than a common internal letter. Using a character class at the beginning of a pattern, like [cep]*, is a useful technique for selecting files from a specific, known set while excluding others.

## References
None

# Exclusionary Globbing
This challenge introduces negated character classes, a globbing feature used to match files that do not contain certain characters. 
## My Solve
Flag: pwn.college{ABPdmlB2MWmfCdfq75wj_T3WOqn.QX2IDO0wCM3AzNzEzW}

The task was to run an executable with an argument that expands to all files in the directory, except for those starting with 'p', 'w', or 'n'. To accomplish this, I used a negated character class. The pattern [^pwn]* tells the shell to match any file that begins with a character that is not 'p', 'w', or 'n', followed by any number of other characters. This successfully filtered out the unwanted files and passed the correct list to the run program.

```
hacker@globbing~exclusionary-globbing:~$ cd /challenge/files
hacker@globbing~exclusionary-globbing:/challenge/files$ /challenge/run [^pwn]*
You got it! Here is your flag!
pwn.college{ABPdmlB2MWmfCdfq75wj_T3WOqn.QX2IDO0wCM3AzNzEzW}
```

## What I Learned
I learned that placing a (^) or an exclamation mark (!) as the first character inside a globbing bracket ([]) inverts the match. Instead of matching any character inside the set, it matches any character not in the set. This is a technique for exclusion, allowing you to easily select all files except for a specific few.

## References
None

# Tab Completion
This challenge highlights the importance of using tab completion to ensure filenames are specified accurately, particularly when they may contain hidden or special characters. 
## My Solve
Flag: pwn.college{oYlsJlkJ2GDDpj_E6no7dXuKIke.0FN0EzNxwCM3AzNzEzW}

In this challenge, a file in `/challenge/` appeared to be named `pwncollege` when listed with `ls`. However, attempting to `cat` the file by typing its name manually resulted in a "No such file or directory" error. This was because the actual filename contained special, non-printable characters.
The solution was to type the beginning of the command, `cat /challenge/pwn`, and then press the `Tab` key. The shell automatically completed the filename with its correct, hidden characters, allowing the `cat` command to find and read the file successfully.

```
hacker@globbing~tab-completion:~$ ls /challenge
DESCRIPTION.md  pwncollege​
hacker@globbing~tab-completion:~$ cat /challenge/pwncollege​ 
pwn.college{oYlsJlkJ2GDDpj_E6no7dXuKIke.0FN0EzNxwCM3AzNzEzW}
```

## What I Learned
I learned that tab completion prevents typos and correctly handles complex filenames that include spaces, special symbols, or non-printable characters. This challenge showed that what you see in an `ls` listing might not be the exact sequence of characters in a filename, and using `Tab` is the most reliable way to specify a file path correctly.

## References
None

# Multiple Options for Tab Completion
This challenge explores how the shell uses tab completion to handle situations where multiple files match the typed prefix. 
## My Solve
Flag: pwn.college{8fU0LC1OgBwLSGovKE6mdhULYmf.0lN0EzNxwCM3AzNzEzW}

The goal was to locate and read a specific flag file within a directory containing many other files that shared a common prefix. To solve this, I relied on the multi-stage behavior of tab completion.
First, I changed the directory to `/challenge/files` then typed the beginning of the path, `cat p`, and pressed `Tab`. The shell completed the common part of all filenames, resulting in `cat pwn`. Pressing `Tab` a second time displayed a list of all possible completions. From this list, I identified the flag file and then opened it using cat to retrieve the flag.

```
hacker@globbing~multiple-options-for-tab-completion:~$ cd /challenge/files
hacker@globbing~multiple-options-for-tab-completion:/challenge/files$ cat pwn
pwn                    pwn-the-planet         pwncollege-flag        pwncollege-flyswatter  
pwn-college            pwncollege-family      pwncollege-flamingo    pwncollege-hacking     
hacker@globbing~multiple-options-for-tab-completion:/challenge/files$ cat pwncollege-flag
pwn.college{8fU0LC1OgBwLSGovKE6mdhULYmf.0lN0EzNxwCM3AzNzEzW}
```

## What I Learned
I learned how the shell handles tab completions, which is a crucial feature for navigating directories with many similarly named files. The key behavior is:

1.  First `Tab`: Completes the filename up to the longest common prefix.
2.  Second `Tab`: Lists all possible options that share that prefix.

## References
None

# Tab Completing Commands
This challenge demonstrates that tab completion works not only for file paths but also for command names.
## My Solve
Flag: pwn.college{I5Wvt08tvRZi_ET5cvpB9Owa7k5.0VN0EzNxwCM3AzNzEzW}

The goal was to find and execute a command that started with the prefix `pwncollege`. To do this, I first typed `pwncollege` at the shell prompt and pressed the `Tab` key. The shell automatically completed the full command name. After the name was completed, I pressed Enter to run the command and receive the flag.

```
hacker@globbing~tab-completion-on-commands:~$ pwncollege-25946 
Correct! Here is your flag:
pwn.college{I5Wvt08tvRZi_ET5cvpB9Owa7k5.0VN0EzNxwCM3AzNzEzW}
```

## What I Learned
I learned that tab completion applies to commands by searching for matching executables.

## References
None
