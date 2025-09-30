# Redirecting Output
This challenge introduces the concept of output redirection and to save it into a file using the `>` operator.
## My Solve
Flag: pwn.college{EnI45dVlVtw5YkdiBpEez8WdnrM.QX0YTN0wCM3AzNzEzW}

The goal was to create a file named `COLLEGE` containing the text `PWN`. To do this, I used the `echo` command to generate the string "PWN". Then, I used the `>` redirection operator to save the output of `echo` into the file `COLLEGE`. 

```
hacker@piping~redirecting-output:~$ echo hi > asdf
hacker@piping~redirecting-output:~$ cat asdf
hi
hacker@piping~redirecting-output:~$ echo PWN > COLLEGE
Correct! You successfully redirected 'PWN' to the file 'COLLEGE'! Here is your 
flag:
pwn.college{EnI45dVlVtw5YkdiBpEez8WdnrM.QX0YTN0wCM3AzNzEzW}
```

## What I Learned
I learned that the `>` operator is a feature for redirecting the standard output of any command into a file.

## References
None

# Redirecting More Output
This challenge shows that we can redirect the output of a command into another file.
## My Solve
Flag: pwn.college{MKWdqCgghiit8v98UT7cbNXGJul.QX1YTN0wCM3AzNzEzW}

The task was to redirect the output of the command `/challenge/run` to the file `myflag`, which was done by using the command `/challenge/run > myflag`. We needed to read the file contents using `cat myflag`, which gave us the flag.

```
hacker@piping~redirecting-more-output:~$ /challenge/run > myflag
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : myflag
[INFO] - the challenge will output a reward file if all the tests pass : /flag

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /flag file.

[TEST] You should have redirected my stdout to a file called myflag. Checking...

[PASS] The file at the other end of my stdout looks okay!
[PASS] Success! You have satisfied all execution requirements.
hacker@piping~redirecting-more-output:~$ cat myflag

[FLAG] Here is your flag:
[FLAG] pwn.college{MKWdqCgghiit8v98UT7cbNXGJul.QX1YTN0wCM3AzNzEzW}
```

## What I Learned
I learned that we can redirect the output of an echo command or any other command into a file.

## References
None

# Appending Output
This challenge introduces us to the use of the `>>` operator and the idea of appending instead of overwriting.
## My Solve
Flag: pwn.college{sFeCU9j3P1_MaxB3YRvzTCVREuM.QX3ATO0wCM3AzNzEzW}

```
hacker@piping~appending-output:~$ /challenge/run >> /home/hacker/the-flag
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : /home/hacker/the-flag

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] Good luck!

[TEST] You should have redirected my stdout to a file called /home/hacker/the-flag. Checking...

[HINT] File descriptors are inherited from the parent, unless the FD_CLOEXEC is set by the parent on the file descriptor.
[HINT] For security reasons, some programs, such as python, do this by default in certain cases. Be careful if you are
[HINT] creating and trying to pass in FDs in python.

[PASS] The file at the other end of my stdout looks okay!
[PASS] Success! You have satisfied all execution requirements.
I will write the flag in two parts to the file /home/hacker/the-flag! I'll do 
the first write directly to the file, and the second write, I'll do to stdout 
(if it's pointing at the file). If you redirect the output in append mode, the 
second write will append to (rather than overwrite) the first write, and you'll 
get the whole flag!

hacker@piping~appending-output:~$ cat the-flag
 | 
\|/ This is the first half:
 v 
pwn.college{sFeCU9j3P1_MaxB3YRvzTCVREuM.QX3ATO0wCM3AzNzEzW}
                              ^
     that is the second half /|\
                              |

If you only see the second half above, you redirected in *truncate* mode (>) 
rather than *append* mode (>>), and so the write of the second half to stdout 
overwrote the initial write of the first half directly to the file. Try append 
mode!
```

## What I Learned
I learned that if we always use the `>` operator, it will overwrite the file each time, making our data vulnerable to deletion. Instead, we use the `>>` command, which appends data to the existing content in the file.

## References
None

# Redirecting Errors
This challenge introduces File Descriptors (FDs) and demonstrates how to redirect the standard error using the `2>` operator.
## My Solve
Flag: pwn.college{g4AuHl4eHPgM9if_tRdEVhJ6Wi4.QX3YTN0wCM3AzNzEzW}

The goal was to run `/challenge/run` while capturing its normal output in myflag and its error into instructions. I accomplished this in a single command by using `> myflag` to redirect stdout and `2> instructions` to redirect stderr. After the command ran silently, I read the `myflag` file to get the flag.

```
hacker@piping~redirecting-errors:~$ /challenge/run > myflag 2> instructions
hacker@piping~redirecting-errors:~$ cat myflag

[FLAG] Here is your flag:
[FLAG] pwn.college{g4AuHl4eHPgM9if_tRdEVhJ6Wi4.QX3YTN0wCM3AzNzEzW}
```

## What I Learned
I learned that the shell manages a program's I/O through numbered channels called File Descriptors. The two most common output streams are FD 1 (stdout) and FD 2 (stderr). The `>` operator is a shortcut for `1>`, while `2>` specifically redirects the standard error stream. This allows you to separate a program's normal output from its status messages.

## References
None

# Redirecting Input
This challenge introduces input redirection, which uses the `<` operator to feed the contents of a file into a program's input.
## My Solve
Flag: pwn.college{Q-eyOksBy3QdDGaiLmpWHGpWrjd.QXwcTN0wCM3AzNzEzW}

First, I needed to create a file named `PWN` that contained the word `COLLEGE`. I did this using the output redirection command `echo COLLEGE > PWN`. 
Second, I had to run the `/challenge/run` program with the contents of the `PWN` file as its standard input. I used the `<` operator to redirect the file into the program, which successfully passed the check and printed the flag.

```
hacker@piping~redirecting-input:~$ echo COLLEGE > PWN
hacker@piping~redirecting-input:~$ /challenge/run < PWN
Reading from standard input...
Correct! You have redirected the PWN file into my standard input, and I read 
the value 'COLLEGE' out of it!
Here is your flag:
pwn.college{Q-eyOksBy3QdDGaiLmpWHGpWrjd.QXwcTN0wCM3AzNzEzW}
```

## What I Learned
I learned that the `<` operator redirects data into a program. It takes the content of a file and feeds it to a program's standard input.

## References
None

# Grepping Stored Results
This challenge combines output redirection (`>`) and file searching (`grep`).
## My Solve
Flag: pwn.college{wG2BxzAUc6csTGDXfjYVn7LYG_p.QX4EDO0wCM3AzNzEzW}

The task was to find a flag hidden within a very large output from the `/challenge/run` program. First, I ran the program and used the `>` operator to redirect its output into a file at `/tmp/data.txt`. Next, I used `grep` to search that file for the unique flag prefix, "pwn", which instantly located the line containing the flag.

```
hacker@piping~grepping-stored-results:~$ /challenge/run > /tmp/data.txt
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : /tmp/data.txt
[INFO] - the challenge will output a reward file if all the tests pass : /challenge/.data.txt

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /challenge/.data.txt file.

[TEST] You should have redirected my stdout to a file called /tmp/data.txt. Checking...

[HINT] File descriptors are inherited from the parent, unless the FD_CLOEXEC is set by the parent on the file descriptor.
[HINT] For security reasons, some programs, such as python, do this by default in certain cases. Be careful if you are
[HINT] creating and trying to pass in FDs in python.

[PASS] The file at the other end of my stdout looks okay!
[PASS] Success! You have satisfied all execution requirements.
hacker@piping~grepping-stored-results:~$ grep pwn < /tmp/data.txt
pwn
pwn.college{wG2BxzAUc6csTGDXfjYVn7LYG_p.QX4EDO0wCM3AzNzEzW}
pwned
pwning
pwns
```

## What I Learned
I learned how to chain commands together to perform a multi-step task.

## References
None

# Grepping Live Output
This challenge introduces the pipe (`|`) operator, which allows you to connect the standard output of one command directly to the standard input of another.
## My Solve
Flag: pwn.college{sdI2bRBDJ0hFbvuIB8f0W7OoTTs.QX5EDO0wCM3AzNzEzW}

The goal was to search the output of `/challenge/run` for the flag. Instead of using a temporary file like in the previous challenge, I used a pipe to send the output of `/challenge/run` directly to the `grep` command. This allowed me to filter the data in real-time and find the flag with a single command.

```
hacker@piping~grepping-live-output:~$ /challenge/run | grep pwn.college
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge checks for a specific process at the other end of stdout : grep
[INFO] - the challenge will output a reward file if all the tests pass : /challenge/.data.txt

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /challenge/.data.txt file.

[TEST] You should have redirected my stdout to another process. Checking...
[TEST] Performing checks on that process!

[INFO] The process' executable is /nix/store/8b4vn1iyn6kqiisjvlmv67d1c0p3j6wj-gnugrep-3.11/bin/grep.
[INFO] This might be different than expected because of symbolic links (for example, from /usr/bin/python to /usr/bin/python3 to /usr/bin/python3.8).
[INFO] To pass the checks, the executable must be grep.

[PASS] You have passed the checks on the process on the other end of my stdout!
[PASS] Success! You have satisfied all execution requirements.
pwn.college{sdI2bRBDJ0hFbvuIB8f0W7OoTTs.QX5EDO0wCM3AzNzEzW}
```

## What I Learned
I learned that the pipe (`|`) operator is a fundamental tool for creating command-line workflows. It connects the stdout of the command on its left to the stdin of the command on its right. This allows you to chain multiple commands together, processing data in stages without needing to save intermediate results to temporary files.

## References
None

# Grepping Errors
This challenge explains how to search or process a program's errors by redirecting it to standard output and then using a pipe.
## My Solve
Flag: pwn.college{oCssWkIcxRb8Vf78Q154m8P2Gwu.QX1ATO0wCM3AzNzEzW}

The task was to find a flag hidden in the standard error output of `/challenge/run`. Since the pipe `|` operator only sends stdout to the next command, I first had to merge stderr into stdout.
I used the redirection `2>&1` to send the contents of stderr (File Descriptor 2) to stdout (File Descriptor 1). Then, I piped this combined stream into `grep` to search for the flag pattern, all in a single command.

```
hacker@piping~grepping-errors:~$ /challenge/run 2>&1 | grep pwn.college
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge checks for a specific process at the other end of stderr : grep
[INFO] - the challenge will output a reward file if all the tests pass : /challenge/.data.txt

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /challenge/.data.txt file.

[TEST] You should have redirected my stderr to another process. Checking...
[TEST] Performing checks on that process!

[INFO] The process' executable is /nix/store/8b4vn1iyn6kqiisjvlmv67d1c0p3j6wj-gnugrep-3.11/bin/grep.
[INFO] This might be different than expected because of symbolic links (for example, from /usr/bin/python to /usr/bin/python3 to /usr/bin/python3.8).
[INFO] To pass the checks, the executable must be grep.

[PASS] You have passed the checks on the process on the other end of my stderr!
[PASS] Success! You have satisfied all execution requirements.
pwn.college{oCssWkIcxRb8Vf78Q154m8P2Gwu.QX1ATO0wCM3AzNzEzW}
```

## What I Learned
I learned that the `2>&1` syntax redirects standard error to standard output.

## References
None

# Filtering with Grep-v
This challenge introduces the `-v` option for the `grep` command, which negates the search to show only the lines that do not match a given pattern.
## My Solve
Flag: pwn.college{U_0rs2x2CXgTnJz8reFv_pbfVLM.0FOxEzNxwCM3AzNzEzW}

The program's output contained over 1000 decoy flags mixed in with the single real one. The key was that all decoy flags contained the word "DECOY". To find the real flag, I piped the program's output into `grep -v DECOY`. This command filtered **out** every line containing "DECOY", leaving only the one real flag to be printed to the terminal.

```
hacker@piping~filtering-with-grep-v:~$ /challenge/run | grep -v DECOY
pwn.college{U_0rs2x2CXgTnJz8reFv_pbfVLM.0FOxEzNxwCM3AzNzEzW}
```

## What I Learned
I learned that the `-v` option for `grep` inverts the search result. Instead of printing lines that match a pattern, it prints all the lines that do not match.

## References
None

# Duplicating Piped Data with Tee
This challenge introduces the `tee` command.
## My Solve
Flag: pwn.college{sG3QNtwrgiCZu7qfVn1K--BggXx.QXxITO0wCM3AzNzEzW}

The goal was to successfully pipe the output of `/challenge/pwn` into `/challenge/college`. First I used `tee` into the pipeline to inspect the data being passed. By running `/challenge/pwn | tee tmp.txt | /challenge/college`, I could see what the first program was sending. The `tmp.txt` file contained an error message indicating that `/challenge/pwn` required a specific argument. After providing the correct argument, the pipeline worked and gave me the flag.

```
hacker@piping~duplicating-piped-data-with-tee:~$ /challenge/pwn | tee tmp.txt | /challenge/college
Processing...
The input to 'college' does not contain the correct secret code! This code 
should be provided by the 'pwn' command. HINT: use 'tee' to intercept the 
output of 'pwn' and figure out what the code needs to be.
hacker@piping~duplicating-piped-data-with-tee:~$ cat tmp.txt
Usage: /challenge/pwn --secret [SECRET_ARG]

SECRET_ARG should be "sG3QNtwr"
hacker@piping~duplicating-piped-data-with-tee:~$ /challenge/pwn --secret sG3QNtwr | /challenge/college
Processing...
Correct! Passing secret value to /challenge/college...
Great job! Here is your flag:
pwn.college{sG3QNtwrgiCZu7qfVn1K--BggXx.QXxITO0wCM3AzNzEzW}
```

## What I Learned
I learned that `tee` is an essential command for debugging pipelines. It reads from standard input and writes the data to two places simultaneously, standard output and one or more specified files. 

## References
None

# Process Substitution For Input
This challenge introduces process substitution, a shell feature that allows the output of a command to be treated as a temporary file, which can then be used as an argument for another command.
## My Solve
Flag: pwn.college{sAzdbAc0EeKPp5_GCD_4mKoUrnX.0lNwMDOxwCM3AzNzEzW}

The goal was to find the difference between the outputs of two programs, `/challenge/print_decoys` and `/challenge/print_decoys_and_flag`. Instead of redirecting each output to a file and then running `diff`, I used process substitution.
The syntax `<(command)` runs the command and makes its output appear as a file. I used this to feed the outputs of both programs directly into `diff` in a single line. The `diff` command then reported the single line that was unique to the second program's output, which was the flag.

```
hacker@piping~process-substitution-for-input:~$ diff <(/challenge/print_decoys) <(/challenge/print_decoys_and_flag)
69a70
> pwn.college{sAzdbAc0EeKPp5_GCD_4mKoUrnX.0lNwMDOxwCM3AzNzEzW}
```

## What I Learned
I learned that process substitution (`<(command)`) is an important feature that presents the standard output of a command as a file.

## References
None

# Writing to Multiple Programs
This challenge introduces output process substitution, a feature that presents a command's standard input as a temporary file that other programs can write to.
## My Solve
Flag: pwn.college{0KJVXuq5e1qPvvRdMwIX00H1_pr.QXwgDN1wCM3AzNzEzW}

The goal was to run `/challenge/hack` and feed its output into both `/challenge/the` and `/challenge/planet` simultaneously. To do this, I constructed a pipeline using `tee` and process substitution.
The command `/challenge/hack | tee >(/challenge/the) | /challenge/planet`.

```
hacker@piping~writing-to-multiple-programs:~$ /challenge/hack | tee >(/challenge/the) | /challenge/planet
Congratulations, you have duplicated data into the input of two programs! Here 
is your flag:
pwn.college{0KJVXuq5e1qPvvRdMwIX00H1_pr.QXwgDN1wCM3AzNzEzW}
```

## What I Learned
I learned about output process substitution using the `>(command)` syntax. This feature presents a command's standard input as a writeable file-like object. 

## References
None

# Split Piping stdout and stderr
This challenge is the culmination of the redirection and pipes module, requiring you to simultaneously redirect a command's standard output and standard error to two different commands. 🌿
## My Solve
Flag: pwn.college{cAHFNNHehB3Wa52uXLjRFivxC8Z.QXxQDM2wCM3AzNzEzW}

The goal was to route the output of `/challenge/hack` such that its **stdout** went to `/challenge/planet` and its **stderr** went to `/challenge/the`.
I achieved this with a single, compound command. I used a standard pipe (`|`) to handle stdout, but before the pipe, I redirected stderr to a file. By using output process substitution (`>(/challenge/the)`), I made the `/challenge/the` command's input look like a file, which I could then redirect stderr into using `2>`. The parentheses `()` were used to group the first command and its stderr redirection together.

```
hacker@piping~split-piping-stderr-and-stdout:~$ (/challenge/hack 2> >(/challenge/the)) | /challenge/planet
Congratulations, you have learned a redirection technique that even experts 
struggle with! Here is your flag:
pwn.college{cAHFNNHehB3Wa52uXLjRFivxC8Z.QXxQDM2wCM3AzNzEzW}
```

## What I Learned
I learned how to combine pipes, file descriptor redirection, and process substitution to achieve complex I/O routing. The pattern **`(command_A 2> >(command_B)) | command_C`** is a technique that allows you to process a program's standard output and standard error streams with two separate commands simultaneously, demonstrating a mastery of shell data flow.

## References
None

