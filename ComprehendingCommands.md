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

# Absolute Path of Complex Directories
This challenge requires the use of absolute paths by accessing a file in a complex directory without the ability to navigate to it first.
## My Solve
Flag: pwn.college{IsfOCuxUwF_nPcjnNa09TppDWcY.QXwITO0wCM3AzNzEzW}

In this scenario, the flag was hidden in a deeply nested directory, and the cd command was disabled. I used the cat command with the file's complete absolute path. This meant specifying the entire directory structure from the root (/) down to the flag file itself.

```
You cannot use the 'cd' command in this level, and must retrieve the flag by 
absolute path. Plus, I hid the flag in a different directory! You can find it 
in the file /lib/terminfo/x/flag. Go cat it out **without** cding into that 
directory!
hacker@commands~more-catting-practice:~$ cat /lib/terminfo/x/flag
pwn.college{IsfOCuxUwF_nPcjnNa09TppDWcY.QXwITO0wCM3AzNzEzW}
```

## What I Learned
I learned that even if navigation commands like cd are restricted, you can still interact with any file as long as you know its full location.

## References
None

# Intro to grep
This challenge introduces grep, a powerful command-line utility used to search for specific text patterns within files. 
## My Solve
Flag: pwn.college{kQclodXAGt6FgpTXbX0u4nDTPw2.QX3EDO0wCM3AzNzEzW}

The task was to find a flag hidden inside /challenge/data.txt, a massive file with 100,000 lines. Reading it with cat would have been overwhelming. Instead, I used grep to search for the flag's unique prefix. Since all flags start with pwn.college, I used that as my search string to instantly filter the file and print only the line containing the flag.

```
hacker@commands~grepping-for-a-needle-in-a-haystack:~$ grep pwn.college /challenge/data.txt
pwn.college{kQclodXAGt6FgpTXbX0u4nDTPw2.QX3EDO0wCM3AzNzEzW}
```

## What I Learned
I learned the basic and most common use of the grep command: searching a file for lines that contain a specific string. Grep allows you to quickly go through large amounts of data to find exactly what you need.

## References
None

# Intro to diff
This challenge introduces the diff command, which is used to compare two files and display the lines that are different between them. 
## My Solve
Flag: pwn.college{UlDx4ccvoGUO4ddDgpuVsNR8Ggj.01MwMDOxwCM3AzNzEzW}

The challenge presented two files, one with 100 decoy flags and a second with the same 100 decoys with the real flag. Manually comparing them would be tedious. Instead, I used the diff command to compare /challenge/decoys_only.txt and /challenge/decoys_and_real.txt. The output immediately highlighted the single line that was added to the second file, which was the real flag.

```
hacker@commands~comparing-files:~$ diff /challenge/decoys_only.txt /challenge/decoys_and_real.txt
26a27
> pwn.college{UlDx4ccvoGUO4ddDgpuVsNR8Ggj.01MwMDOxwCM3AzNzEzW}
```

## What I Learned
I learned how to use the diff command to efficiently find differences between two text files. I can now interpret its output to understand what lines have been changed.

## References
None

# Intro To `ls`
This challenge introduces the ls command, which is used to list the contents of a directory.
## My Solve
Flag: pwn.college{chZPi-zsYyy-hYx3WbebKfS6sGB.QX4IDO0wCM3AzNzEzW}

This challenge required us to find and run an executable in /challenge that had been given a random name. So I used the ls command to inspect the directory's contents. Running ls /challenge revealed the name of the executable. After discovering the filename, I executed it using its full path to retrieve the flag.

```
hacker@commands~listing-files:~$ ls /challenge
31762-renamed-run-8364  DESCRIPTION.md
hacker@commands~listing-files:~$ cat /challenge/ DESCRIPTION.md
cat: /challenge/: Is a directory
cat: DESCRIPTION.md: No such file or directory
hacker@commands~listing-files:~$ /challenge/31762-renamed-run-8364
Yahaha, you found me! Here is your flag:
pwn.college{chZPi-zsYyy-hYx3WbebKfS6sGB.QX4IDO0wCM3AzNzEzW}
```

## What I Learned
I learned that the ls command is the primary tool for exploring the filesystem from the command line. It's essential for discovering files and directories when their names are unknown. You can use it with a path to list the contents of a specific directory or run it without arguments to list the contents of your current working directory.

## References
None

# Intro to touch
This challenge introduces the touch command, a simple utility for creating new, empty files. 
## My Solve
Flag: pwn.college{sF60s1QCoPYGAtphbjKJRwIXGA2.QXwMDO0wCM3AzNzEzW}

The task was to create two specific files, /tmp/pwn and /tmp/college. I used the touch command to do this. By providing both file paths as arguments in a single command, I created them simultaneously. After creating the files, I executed /challenge/run to complete the challenge and receive the flag.

```
hacker@commands~touching-files:~$ touch /tmp/pwn /tmp/college
hacker@commands~touching-files:~$ /challenge/run
Success! Here is your flag:
pwn.college{sF60s1QCoPYGAtphbjKJRwIXGA2.QXwMDO0wCM3AzNzEzW}
```

## What I Learned
I learned that touch is the standard command for quickly creating empty files. A key takeaway is that you can create multiple files at once by listing them after the command. The primary purpose of touch is actually to update a file's modification, creating the file only if it doesn't already exist.

## References
None

# Intro To 'rm'
This challenge introduces the 'rm' command, the standard utility for deleting files in Linux. 
## My Solve
Flag: pwn.college{EaNw8mqFhOrr9FBY6ewwRm3ijVn.QX2kDM1wCM3AzNzEzW}

The task was to delete a file named delete_me that was placed in my home directory. I used the ls command to check the files present in home directory, then the rm command followed by the delete_me to accomplish this. After the file was successfully deleted, I ran the /challenge/check program, which verified the file's removal and rewarded me with the flag.

```
hacker@commands~removing-files:~$ ls
Desktop  a  delete_me
hacker@commands~removing-files:~$ rm delete_me
hacker@commands~removing-files:~$ ls
Desktop  a
hacker@commands~removing-files:~$ /challenge/check
Excellent removal. Here is your reward:
pwn.college{EaNw8mqFhOrr9FBY6ewwRm3ijVn.QX2kDM1wCM3AzNzEzW}
```

## What I Learned
I learned that rm is the command to use for deleting files. Once a file is deleted with rm, it can't be restored, so it's essential to be absolutely certain before using it.

## References
None

# Intro to mv
This challenge introduces the mv command, which is used to move or rename files and directories.
## My Solve
Flag: pwn.college{cSYOwZkTP_fxhdEbTpV5UtzWB6o.0VOxEzNxwCM3AzNzEzW}

The goal was to move the file located at /flag to a new destination, /tmp/hack-the-planet. To do this, I used the mv command, providing the source path (/flag) as the first argument and the destination path (/tmp/hack-the-planet) as the second. After successfully moving the file, I ran /challenge/check to verify the action and get the flag.

```
hacker@commands~moving-files:~$ mv /flag /tmp/hack-the-planet
Correct! Performing 'mv /flag /tmp/hack-the-planet'.
hacker@commands~moving-files:~$ /challenge/check
Congrats! You successfully moved the flag to /tmp/hack-the-planet! Here it is:
pwn.college{cSYOwZkTP_fxhdEbTpV5UtzWB6o.0VOxEzNxwCM3AzNzEzW}
```

## What I Learned
I learned that the mv command handles both moving and renaming files. If you specify a different directory as the destination, the file is moved.

## References
None

# Intro To 'ls -a'
This challenge introduces the concept of hidden "dotfiles" in Linux and the use of the -a flag with ls to reveal them. 
## My Solve
Flag: pwn.college{kFZXcG8hLxVYbKdngT5sV-dkcGl.QXzMDO0wCM3AzNzEzW}

The task was to find a flag that was hidden in the root directory (/). Files in Linux that begin with a dot (.) are hidden by default from the ls command. To find the flag, I used ls -a /. The -a (all) flag instructed ls to list every file, including the hidden dotfile containing the flag. Once its name was revealed, I used cat to read its contents.

```

```

## What I Learned
I learned that Linux uses a simple convention for hidden files: any file or directory starting with a . is considered hidden. These "dotfiles" are often used to store user-specific configuration and settings to avoid cluttering the home directory. The key takeaway is that the -a flag with ls is essential for viewing a complete listing of a directory's contents.

## References
None

# Filesystem Quest
This challenge was a practical test that combined the cd, ls, and cat commands to navigate the filesystem and follow a trail of clues. 
## My Solve
Flag: pwn.college{AGqQONMGnhVsU7NwGgQNPkzTPXm.QX5IDO0wCM3AzNzEzW}

The challenge was a scavenger hunt starting in the root directory (/). The process involved a simple, repeatable workflow:
Use ls to look for a clue file (e.g., HINT, CLUE.txt).
Use cat to read the contents of that file.
Use cd to move to the new directory indicated by the clue.
I followed this trail of breadcrumbs through several directories. Each clue led me closer to the final destination until I found a file containing the flag.

```
hacker@commands~an-epic-filesystem-quest:~$ cd /
hacker@commands~an-epic-filesystem-quest:/$ ls
HINT  bin  boot  challenge  dev  etc  flag  home  lib  lib32  lib64  libx32  media  mnt  nix  opt  proc  root  run  sbin  srv  sys  tmp  usr  var
hacker@commands~an-epic-filesystem-quest:/$ cat HINT
Yahaha, you found me!
The next clue is in: /opt/linux/linux-5.4/sound/pci/echoaudio

The next clue is **delayed** --- it will not become readable until you enter the directory with 'cd'.
hacker@commands~an-epic-filesystem-quest:/$ cd /opt/linux/linux-5.4/sound/pci/echoaudio
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/sound/pci/echoaudio$ ls
BRIEF          darla24.c      echoaudio.h      gina20.c      indigo_dsp.c          indigodjx_dsp.c  layla20.c      mia_dsp.c
Makefile       darla24_dsp.c  echoaudio_3g.c   gina20_dsp.c  indigo_express_dsp.c  indigoio.c       layla20_dsp.c  midi.c
built-in.a     echo3g.c       echoaudio_dsp.c  gina24.c      indigodj.c            indigoio_dsp.c   layla24.c      mona.c
darla20.c      echo3g_dsp.c   echoaudio_dsp.h  gina24_dsp.c  indigodj_dsp.c        indigoiox.c      layla24_dsp.c  mona_dsp.c
darla20_dsp.c  echoaudio.c    echoaudio_gml.c  indigo.c      indigodjx.c           indigoiox_dsp.c  mia.c
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/sound/pci/echoaudio$ cat BRIEF
Yahaha, you found me!
The next clue is in: /usr/share/racket/pkgs/slideshow-lib/slideshow/fullscreen

The next clue is **delayed** --- it will not become readable until you enter the directory with 'cd'.
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/sound/pci/echoaudio$ cd /usr/share/racket/pkgs/slideshow-lib/slideshow/fullscreen
hacker@commands~an-epic-filesystem-quest:/usr/share/racket/pkgs/slideshow-lib/slideshow/fullscreen$ ls
NOTE  base.rkt  compiled
hacker@commands~an-epic-filesystem-quest:/usr/share/racket/pkgs/slideshow-lib/slideshow/fullscreen$ cat NOTE
Tubular find!
The next clue is in: /usr/share/doc/libpcre3-dev

Watch out! The next clue is **trapped**. You'll need to read it out without 'cd'ing into the directory; otherwise, the clue will self destruct!

hacker@commands~an-epic-filesystem-quest:/usr/share/racket/pkgs/slideshow-lib/slideshow/fullscreen$ ls /usr/share/doc/libpcre3-dev
CLUE-TRAPPED  changelog.Debian.gz  copyright  examples
hacker@commands~an-epic-filesystem-quest:/usr/share/racket/pkgs/slideshow-lib/slideshow/fullscreen$ cat /usr/share/doc/libpcre3-dev/CLUE-TRAPPED
Tubular find!
The next clue is in: /opt/linux/linux-5.4/include/config/arch/use/builtin
hacker@commands~an-epic-filesystem-quest:/usr/share/racket/pkgs/slideshow-lib/slideshow/fullscreen$ ls /opt/linux/linux-5.4/include/config/arch/use/builtin
SNIPPET  bswap.h
hacker@commands~an-epic-filesystem-quest:/usr/share/racket/pkgs/slideshow-lib/slideshow/fullscreen$ cat /opt/linux/linux-5.4/include/config/arch/u
se/builtin/SNIPPET
Yahaha, you found me!
The next clue is in: /opt/splitmind/.git/logs/refs/remotes/origin
hacker@commands~an-epic-filesystem-quest:/usr/share/racket/pkgs/slideshow-lib/slideshow/fullscreen$ ls /opt/splitmind/.git/logs/refs/remotes/origin
HEAD  INFO
hacker@commands~an-epic-filesystem-quest:/usr/share/racket/pkgs/slideshow-lib/slideshow/fullscreen$ cat /opt/splitmind/.git/logs/refs/remotes/origin/INFO
Yahaha, you found me!
The next clue is in: /usr/local/lib/python3.8/dist-packages/jedi/third_party/typeshed/third_party/2/six/moves/urllib

The next clue is **hidden** --- its filename starts with a '.' character. You'll need to look for it using special options to 'ls'.
hacker@commands~an-epic-filesystem-quest:/usr/share/racket/pkgs/slideshow-lib/slideshow/fullscreen$ ls /usr/local/lib/python3.8/dist-packages/jedi/third_party/typeshed/third_party/2/six/moves/urllib -a
.  ..  .TRACE  __init__.pyi  error.pyi  parse.pyi  request.pyi  response.pyi  robotparser.pyi
hacker@commands~an-epic-filesystem-quest:/usr/share/racket/pkgs/slideshow-lib/slideshow/fullscreen$ cat /usr/local/lib/python3.8/dist-packages/jed
i/third_party/typeshed/third_party/2/six/moves/urllib/.TRACE
Lucky listing!
The next clue is in: /etc/apport

The next clue is **delayed** --- it will not become readable until you enter the directory with 'cd'.
hacker@commands~an-epic-filesystem-quest:/usr/share/racket/pkgs/slideshow-lib/slideshow/fullscreen$ cd /etc/apport
hacker@commands~an-epic-filesystem-quest:/etc/apport$ ls
TEASER  blacklist.d  native-origins.d
hacker@commands~an-epic-filesystem-quest:/etc/apport$ cat TEASER
Great sleuthing!
The next clue is in: /usr/lib/ruby/2.7.0/bundler/templates/newgem

The next clue is **hidden** --- its filename starts with a '.' character. You'll need to look for it using special options to 'ls'.
hacker@commands~an-epic-filesystem-quest:/etc/apport$ ls /usr/lib/ruby/2.7.0/bundler/templates/newgem -a
.   .EVIDENCE              Gemfile.tt      README.md.tt  bin  ext           lib                rspec.tt  test
..  CODE_OF_CONDUCT.md.tt  LICENSE.txt.tt  Rakefile.tt   exe  gitignore.tt  newgem.gemspec.tt  spec      travis.yml.tt
hacker@commands~an-epic-filesystem-quest:/etc/apport$ cat /usr/lib/ruby/2.7.0/bundler/templates/newgem/.EVIDENCE
CONGRATULATIONS! Your perserverence has paid off, and you have found the flag!
It is: pwn.college{AGqQONMGnhVsU7NwGgQNPkzTPXm.QX5IDO0wCM3AzNzEzW}
```

## What I Learned
This challenge solidified my understanding of how to combine the most fundamental Linux commands to effectively explore and navigate the filesystem. It demonstrated a core workflow for finding information when you don't know its exact location beforehand.

## References
None

# Creating Directories with mkdir
This challenge introduces the mkdir (make directory) command, which is used to create new directories in the filesystem. 
## My Solve
Flag: pwn.college{Mkdir_M4k3s_D1r3ct0ri3s_!}

The task had two parts: first, create a directory named pwn inside the /tmp directory, and second, create a file named college inside that new /tmp/pwn directory. I used the mkdir command to create the directory and then the touch command with the full path to create the file inside it. Finally, I ran /challenge/run to verify my work and get the flag.

```
hacker@dojo:~$ mkdir /tmp/pwn

hacker@dojo:~$ touch /tmp/pwn/college

hacker@dojo:~$ /challenge/run
Success! Here is your flag:
pwn.college{Mkdir_M4k3s_D1r3ct0ri3s_!}
```

## What I Learned
I learned that mkdir is the fundamental command for creating new directories.

## References
None
