# Intro To Arguments
The challenge asks you to invoke the commands.
## My Solve
Flag: pwn.college{4_nkpds_dPZyr1_vkLQYuoRTNCv.QX3-YjM1wCM3AzNzEzW}

To solve this, I first used the whoami command to check the current user. Afterwards, I simply executed the hello program without any arguments, which successfully printed the flag to the terminal.

```
hacker@hello~intro-to-commands:~$ whoami
hacker
hacker@hello~intro-to-commands:~$ hello
Success! Here is your flag:
pwn.college{4_nkpds_dPZyr1_vkLQYuoRTNCv.QX3YjM1wCM3AzNzEzW}
```

## What I Learned
I learned that the whoami command shows the current username.

## References
None.

# Intro To Arguments
The challenge asks you to invoke the 'echo' and 'hello' commands with different arguments to obtain respective results.
## My Solve
Flag: pwn.college{8yVf40kJCDaZBu31EvwbUtRcKrK.QX4YjM1wCMxAzNzEzW}

This challenge required providing specific arguments to programs in the terminal. I first used the echo command to understand how arguments work. Running echo Hello passes one argument and prints "Hello", while echo Hello Hackers! passes two arguments and prints both. Based on this understanding, I ran the hello program with hackers as its argument. This was the correct input to solve the challenge and retrieve the flag.

```
hacker@hello~intro-to-arguments:~$ echo Hello
Hello
hacker@hello~intro-to-arguments:~$ echo Hello Hackers!
Hello Hackers!
hacker@hello~intro-to-arguments:~$ hello hackers
Success! Here is your flag:
pwn.college{8yVf40kJCDaZBu31EvwbUtRcKrK.QX4YjM1wCMxAzNzEzW}
```

## What I Learned
Through this task, I understood that Linux programs can accept a variable number of command-line arguments and that these inputs directly influence the program's output.

## References
None

# Intro To Arguments
The challenge asks you to use the up and down arrow keys to get the history of the terminal.
## My Solve
Flag: pwn.college{0zGI9SFGGu9QTRPtcUAWK0AE7sv.0lNzEzNxwCM3AzNzEzW}
This challenge required using the up arrow key to get the flag, which was stored in the terminal's history. This was the correct input to solve the challenge and retrieve the flag.

```
hacker@hello~command-history:~$ the flag is pwn.college{0zGI9SFGGu9QTRPtcUAWK0AE7sv.0lNzEzNxwCM3AzNzEzW}
```

## What I Learned
Through this task, I understood that the terminal stores the commands in the history and can be retrieved easily by using the arrow keys, rather than typing them again.
## References
None

# Intro To Arguments
The challenge asks you to invoke a program by providing its path on the command line.
## My Solve
Flag: pwn.college{wbVS9HDiroBGIh7nNgSM4UshJm7.QX4cTO0wCM3AzNzEzW}

This challenge required invoking a program by providing its path on the command line. In this case, we'll be giving the exact path, starting from /, so the path would be /pwn.
This style of path, one that starts with the root directory, is referred to as an "absolute path".

```
hacker@paths~the-root:~$ /pwn
BOOM!!!
Here is your flag:
pwn.college{wbVS9HDiroBGIh7nNgSM4UshJm7.QX4cTO0wCM3AzNzEzW}
```

## What I Learned
Through this task, I understood that the filesystem starts at /. Under that, there is a whole mess of other directories, configuration files, and programs. We can invoke the /filename, which would give the contents of it.

## References
None

# Intro To Arguments
The challenge asks you to invoke a program that is itself in a directory by providing its path on the command line.
## My Solve
Flag: pwn.college{0P9ojnZnZOGxtjVRkFpnJ1ssVXb.QX1QTN0wCM3AzNzEzW}

This challenge required invoking a program by providing its path on the command line. In this case, we'll be starting from /, then open the 'challenge' directory, where we further access the 'run' program. So, the path would be /challenge/run.

```
hacker@paths~program-and-absolute-paths:~$ /challenge/run
Correct!!!
/challenge/run is an absolute path! Here is your flag:
pwn.college{0P9ojnZnZOGxtjVRkFpnJ1ssVXb.QX1QTN0wCM3AzNzEzW}
```

## What I Learned
Through this task, I understood that the filesystem starts at /. Under that, there is a whole mess of other directories, configuration files, and programs. We can invoke the /directory/filename, which would give the contents of it.

## References
None

# Intro To Arguments
The challenge asks you to change the directory using 'cd' command.
## My Solve
Flag: pwn.college{I4asR9rjwGx3eyHhr7YwD76mp6I.QX2QTN0wCM3AzNzEzW}

This challenge required invoking a program by first changing the directory using 'cd' and then opening the specific file by providing its path on the command line.

```
hacker@paths~position-thy-self:~$ /challenge/run
Incorrect...
You are not currently in the /sys/kernel directory.
Please use the `cd` utility to change directory appropriately.
hacker@paths~position-thy-self:~$ cd /sys/kernel
hacker@paths~position-thy-self:/sys/kernel$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{I4asR9rjwGx3eyHhr7YwD76mp6I.QX2QTN0wCM3AzNzEzW}
```

## What I Learned
Through this task, I understood that the Linux filesystem has tons of directories with tons of files. You can navigate around directories by using the 'cd' (change directory) command and passing a path to it as an argument.

## References
None

# Intro To Arguments
The challenge asks you to change the directory and further navigate till the required file using 'cd' command.
## My Solve
Flag: pwn.college{g3j0xP6hdoCLFcCdVQaaV8JXbw2.QX3QTN0wCM3AzNzEzW}

This challenge required invoking a program by first changing the directory by putting the exact path of the file using 'cd' and then opening the specific file by providing its path on the command line.

```
hacker@paths~position-elsewhere:~$ /challenge/run
Incorrect...
You are not currently in the /usr/share/zoneinfo/posix/Asia directory.
Please use the `cd` utility to change directory appropriately.
hacker@paths~position-elsewhere:~$ cd /usr/share/zoneinfo/posix/Asia
hacker@paths~position-elsewhere:/usr/share/zoneinfo/posix/Asia$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{g3j0xP6hdoCLFcCdVQaaV8JXbw2.QX3QTN0wCM3AzNzEzW}
```

## What I Learned
Through this task, I understood that we can get to the file by exactly going through the path using the 'cd' prompt.

## References
None

# Intro To Arguments
The challenge asks you to invoke a program by providing its path on the command line.
## My Solve
Flag: pwn.college{UQesoZK3_ePyokH1QSYiZqrHNHa.QX4QTN0wCM3AzNzEzW}

This challenge required invoking a program by providing its path on the command line. In this case, we'll be giving the exact path.

```
hacker@paths~position-yet-elsewhere:~$ /challenge/run
Incorrect...
You are not currently in the /var/lib/apt/lists directory.
Please use the `cd` utility to change directory appropriately.
hacker@paths~position-yet-elsewhere:~$ cd /var/lib/apt/lists
hacker@paths~position-yet-elsewhere:/var/lib/apt/lists$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{UQesoZK3_ePyokH1QSYiZqrHNHa.QX4QTN0wCM3AzNzEzW}
```

## What I Learned
Through this task, I understood that there is a whole mess of other directories, configuration files, and programs. We can invoke the /filename, which would give the contents of it. Change directories using 'cd' prompt.

## References
None

# Intro To Arguments
The challenge requires running an executable using a relative path instead of an absolute one.
## My Solve
Flag: pwn.college{srPKKur444UUhtIi8uHby3NgrCi.QX5QTN0wCM3AzNzEzW}

I needed to understand the difference between an absolute path and a relative path. An absolute path always starts from the root directory (e.g., /challenge/run), while a relative path starts from your current working directory.
The task was to run the executable located at /challenge/run from the root directory (/) using a relative path. I started by changing my current working directory to the root directory with the command cd /. From the root directory, the relative path to the executable is simply challenge/run. Executing this path successfully ran the program and gave me the flag.

```
hacker@paths~implicit-relative-paths-from-:~$ cd /
hacker@paths~implicit-relative-paths-from-:/$ challenge/run
Correct!!!
challenge/run is a relative path, invoked from the right directory!
Here is your flag:
pwn.college{srPKKur444UUhtIi8uHby3NgrCi.QX5QTN0wCM3AzNzEzW}
```

## What I Learned
Through this task, I understood that this challenge demonstrated that the interpretation of a relative path depends entirely on your current working directory (cwd).

## References
None

# Intro To Arguments
This challenge introduces the concept of using '.' a dot, in relative paths to explicitly refer to the current directory.
## My Solve
Flag: pwn.college{QlYxjvnCPe1qlJjt8rg1NZ2Yt0n.QXwUTN0wCM3AzNzEzW}

I first changed my location to the root directory by typing cd /. From there, I needed to run the executable located at /challenge/run. Instead of just typing challenge/run, I used the more explicit relative path ./challenge/run. This command tells the shell: "Starting from the current directory (.), go into the challenge directory and execute the file named run." This approach worked and printed the flag.

```
hacker@paths~explicit-relative-paths-from-:~$ cd /
hacker@paths~explicit-relative-paths-from-:/$ ./challenge/run
Correct!!!
./challenge/run is a relative path, invoked from the right directory!
Here is your flag:
pwn.college{QlYxjvnCPe1qlJjt8rg1NZ2Yt0n.QXwUTN0wCM3AzNzEzW}
```

## What I Learned
Through this task, I understood that there is a shorthand for the current working directory. Using './' at the beginning of a path is a common and explicit way to tell the shell to look for a file or directory starting from the current location.
## References
None

# Intro To Arguments
This challenge demonstrates why you must use a relative path like './' to run an executable file located in your current directory.
## My Solve
Flag: pwn.college{Qo8Hew4kfZQSv6H6BrYAyAiwUxq.QXxUTN0wCM3AzNzEzW}

My first step was to navigate there with cd /challenge. By using the relative path './run'. This command worked perfectly and gave me the flag.

```
hacker@paths~implicit-relative-path:~$ cd /challenge
hacker@paths~implicit-relative-path:/challenge$ ./run
Correct!!!
./run is a relative path, invoked from the right directory!
Here is your flag:
pwn.college{Qo8Hew4kfZQSv6H6BrYAyAiwUxq.QXxUTN0wCM3AzNzEzW}
```

## What I Learned
Through this task, I understood that './' is the standard and necessary way to execute a program that resides in your current working directory.

## References
None

# Intro To Arguments
This challenge involved using the tilde (~) character as a shorthand to create a valid file path that meets specific length and location constraints.
## My Solve
Flag: pwn.college{kFZXcG8hLxVYbKdngT5sV-dkcGl.QXzMDO0wCM3AzNzEzW}

This challenge required invoking a program by providing its path on the command line. In this case, we'll be giving the exact path, starting from /, so the path would be /pwn.
This style of path, one that starts with the root directory, is referred to as an "absolute path".

```
hacker@paths~home-sweet-home:~$ /challenge/run ~/a
Writing the file to /home/hacker/a!
... and reading it back to you:
pwn.college{kFZXcG8hLxVYbKdngT5sV-dkcGl.QXzMDO0wCM3AzNzEzW}
```

## What I Learned
Through this task, I understood that the filesystem starts at /. Under that, there is a whole mess of other directories, configuration files, and programs. We can invoke the /filename which would give the conents of it.

## References
None
