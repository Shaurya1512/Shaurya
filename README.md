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
