# Printing Variables
This challenge demonstrates how to print their contents using the `echo` command and the `$` prefix. 
## My Solve
Flag: pwn.college{UlXRtLfSejcxUzYDRTa1UdGD6bP.QX3UTN0wCM3AzNzEzW}

The flag for this challenge was stored in a shell variable named `FLAG`. To display its value, I used the `echo` command and `$` prefix for the variable FLAG.

```
hacker@variables~printing-variables:~$ echo $FLAG
pwn.college{UlXRtLfSejcxUzYDRTa1UdGD6bP.QX3UTN0wCM3AzNzEzW}
```

## What I Learned
I learned that to access the value stored in a variable, you must prefix its name with (`$`).

## References
None

# Setting Variables
This challenge demonstrates how to assign values to variables. 
## My Solve
Flag: pwn.college{4iLqeQFlrJUaQFVsHSEGOlz9v3N.QX5UTN0wCM3AzNzEzW}

I had to directly equate the variable with its value, without keeping spaces, so the command was Variable=Value, which, on execution, gave the flag.

```
hacker@variables~setting-variables:~$ PWN=COLLEGE
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{4iLqeQFlrJUaQFVsHSEGOlz9v3N.QX5UTN0wCM3AzNzEzW}
```

## What I Learned
I learned to assign value to a variable.

## References
None

# Multi Word Variables
This challenge demonstrates how to assign multi-word values to variables. 
## My Solve
Flag: pwn.college{Y9Nh0JDo-vHlDwbUbKF7bE1XItJ.QXwYTN0wCM3AzNzEzW}

I had to use quoting to equate the multi-word value with its variable, so the command was Variable="Multi Word Value", which, on execution, gave the flag.

```
hacker@variables~multi-word-variables:~$ PWN="COLLEGE YEAH"
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{Y9Nh0JDo-vHlDwbUbKF7bE1XItJ.QXwYTN0wCM3AzNzEzW}
```

## What I Learned
I learned to assign a multi-word value to a variable.

## References
None

# Exporting Variables
This challenge illustrates the distinction between local shell variables and environment variables.
## My Solve
Flag: pwn.college{kY1n2CbpGiKsTtEgO5JLHcTCuNj.QXyYTN0wCM3AzNzEzW}

The challenge required setting two variables with different scopes before running the program. The `PWN` variable needed to be visible to the `/challenge/run` process, so I used `export` to make it an environment variable. The `COLLEGE` variable needed to be hidden from the program, so I set it as a normal local variable.

```
hacker@variables~exporting-variables:~$ COLLEGE=PWN
You've set the COLLEGE variable to the proper value!
hacker@variables~exporting-variables:~$ export PWN=COLLEGE
You've set the PWN variable to the proper value!
You've set the COLLEGE variable to the proper value!
hacker@variables~exporting-variables:~$ /challenge/run
CORRECT!
You have exported PWN=COLLEGE and set, but not exported, COLLEGE=PWN. Great 
job! Here is your flag:
pwn.college{kY1n2CbpGiKsTtEgO5JLHcTCuNj.QXyYTN0wCM3AzNzEzW}
You've set the PWN variable to the proper value!
You've set the COLLEGE variable to the proper value!
```

## What I Learned
I learned the distinction between two types of variables:

  * Local Variables (`VAR=...`): These are confined to the shell session in which they are created.
  * Environment Variables (`export VAR=...`): These are passed to any new processes (child processes) started from that shell. The `export` command is what makes a variable part of the environment.

## References
None

# Printing Exported Variables
This challenge introduces the `env` command, which is used to display a list of all currently set environment variables.
## My Solve
Flag: pwn.college{w118p4uDBsJX1vDzAEF4K6VaHjY.QX4UTN0wCM3AzNzEzW}

The flag was stored as an environment variable, so I used the `env` command to list all exported variables. To avoid manually searching through the entire list, I piped the output of `env` directly into `grep` to filter for the line containing the `FLAG` variable.

```
hacker@variables~printing-exported-variables:~$ env | grep FLAG
FLAG=pwn.college{w118p4uDBsJX1vDzAEF4K6VaHjY.QX4UTN0wCM3AzNzEzW}
```

## What I Learned
I learned that the `env` command provides a clean list of all variables that have been exported into the current environment. Piping its output to `grep` is a very efficient way to check the value of a specific environment variable.

## References
None

# Storing Command Output
This challenge introduces command substitution, a shell feature that allows you to capture the output of a command and store it in a variable. 
## My Solve
Flag: pwn.college{EQgj5HcUiEfnwR4RAyK_3CWUj3u.QX1cDN1wCM3AzNzEzW}

The task was to execute the `/challenge/run` program and save its output directly into a variable named `PWN`. I used the command substitution syntax `PWN=$(/challenge/run)` to accomplish this. This command ran the program, captured its standard output, and assigned it to the `PWN` variable. I then used `echo` to print the contents of the variable and reveal the flag.

```
hacker@variables~storing-command-output:~$ PWN=$(/challenge/run)
Congratulations! You have read the flag into the PWN variable. Now print it out 
and submit it!
hacker@variables~storing-command-output:~$ echo $PWN
pwn.college{EQgj5HcUiEfnwR4RAyK_3CWUj3u.QX1cDN1wCM3AzNzEzW}
```

## What I Learned
I learned that the `$(command)` syntax performs command substitution. The shell executes the command inside the parentheses and replaces the entire `$(...)` expression with the command's standard output. This is an essential technique for scripting, as it allows you to store the results of one command for later use in another.

## References
None

# Reading Input
This challenge introduces the `read`, which is used to read a line of text from standard input and assign it to a variable.
## My Solve
Flag: pwn.college{giJtUG_hnbV1k3T4qBWzaRID9ud.QX4cTN0wCM3AzNzEzW}

The goal was to set the shell variable `PWN` to the value `COLLEGE` using the `read` command. I executed `read PWN`, which caused the script to pause and wait for input. I then typed `COLLEGE` and pressed Enter. The `read` command captured this input and stored it in the `PWN` variable, satisfying the challenge's condition.

```
hacker@variables~reading-input:~$ read PWN
COLLEGE
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{giJtUG_hnbV1k3T4qBWzaRID9ud.QX4cTN0wCM3AzNzEzW}
```

## What I Learned
I learned that the `read` command is the standard way to make a shell script interactive. It pauses execution, reads a line of text from standard input (i.e., user keyboard input), and assigns the text to a specified variable.

## References
None

# Reading Files
This challenge demonstrates an efficient, shell-native method for reading  the contents of a file directly into a variable by combining the `read` command with input redirection. 
## My Solve
Flag: pwn.college{8byx0GEnZhk1jN4xVwIXBIbLHvT.QXwIDO0wCM3AzNzEzW}

The task was to read the contents of the file `/challenge/read_me` into the `PWN` variable. To do this efficiently without starting an external program like `cat`, I redirected the file directly into the standard input of the `read` command. This single command read the first line from the file and assigned it to the `PWN` variable, which was then validated by the checker.

```
hacker@variables~reading-files:~$ read PWN < /challenge/read_me
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{8byx0GEnZhk1jN4xVwIXBIbLHvT.QXwIDO0wCM3AzNzEzW}
```

## What I Learned
I learned that combining `read VAR < filename` is a highly efficient method for reading the first line of a file into a shell variable. 

## References
None
