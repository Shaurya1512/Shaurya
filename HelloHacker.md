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
