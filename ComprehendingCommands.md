# Intro To `cat`
The challenge introduces the `cat` command, a fundamental utility in Linux used for reading and displaying file contents.
## My Solve
Flag: pwn.college{UQsf41TxFrPNagJTNq2doJrCv_k.QXxcTN0wCM3AzNzEzW}

I used the `cat` command followed by the filename. The command read the file's contents and printed them directly to the terminal, revealing the flag.

```
hacker@commands~cat-not-the-pet-but-the-command:~$ cat flag
pwn.college{UQsf41TxFrPNagJTNq2doJrCv_k.QXxcTN0wCM3AzNzEzW}
```

## What I Learned
I learned the primary function of the `cat` command, which is to display the contents of a file. I also understood that its name, short for "concatenate," hints at its ability to combine and display multiple files sequentially if given more than one argument. This challenge focused on its most basic and frequent application: viewing a single file.

## References
None


# Intro to Absolute Paths
This challenge focuses on using the cat command with an absolute path to read a file.
## My Solve
Flag: pwn.college{E3YrrKAwr3ZG67XoKKL259UyzTW.QX5ETO0wCM3AzNzEzW}

Unlike the previous level, where the flag was in my home directory, this time it is located in the absolute path /flag. By providing this full path to the cat command, I could read the file's contents.

```
hacker@commands~catting-absolute-paths:~$ cat /flag
pwn.college{E3YrrKAwr3ZG67XoKKL259UyzTW.QX5ETO0wCM3AzNzEzW}
```

## What I Learned
I learned how to use absolute paths to access files. While a relative path depends on your current directory, an absolute path is a fixed address that works universally across the system.

## References
None
