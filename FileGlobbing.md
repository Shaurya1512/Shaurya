# Introduction to Globbing: The * Wildcard
This challenge introduces globbing, a feature where the shell interprets special characters like * as wildcards to match filenames. 
## My Solve
Flag: pwn.college{Mbj09ihiC4gnYrknkBSW1V1nVwk.QXxIDO0wCM3AzNzEzW}

The goal was to change the directory to /challenge using a cd argument of four characters or less. The full path /challenge is too long. I used the * wildcard to create the short pattern /c*, which is only three characters. Since /challenge is the only directory in the root (/) that starts with the letter 'c', the shell correctly expanded this pattern to /challenge. After successfully changing directories, I ran the run executable to get the flag.

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

# Globbing with the ? Wildcard
This challenge introduces the ? globbing character, which acts as a wildcard that matches exactly one character. 
## My Solve
Flag: pwn.college{Qu3st10n_M4rks_M4tch_1_Ch4r}

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
I learned that the ? wildcard is used in shell globbing to match exactly one of any character. This makes it more precise than the * wildcard, which matches any number of characters. The ? is useful when you need to match filenames that have a fixed length but vary by a few characters, like image_0?.png which would match image_01.png through image_09.png but not image_10.png.

## References
None

