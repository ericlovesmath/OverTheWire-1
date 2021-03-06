# OverTheWire

My notes for games available on https://overthewire.org/wargames/

The wargames offered by the OverTheWire community can help you to learn and practice security concepts in the form of fun-filled games.

## Natas Wargame

Natas teaches the basics of serverside web-security.

Each level of natas consists of its own website located at `http://natasX.natas.labs.overthewire.org`, where X is the level number. There is no SSH login. To access a level, enter the username for that level (e.g. natas0 for level 0) and its password.

Each level has access to the password of the next level. Your job is to somehow obtain that next password and level up. All passwords are also stored in `/etc/natas_webpass/`. E.g. the password for `natas5` is stored in the file `/etc/natas_webpass/natas5` and only readable by `natas4` and `natas5`.

### Level 0

A page displaying that `You can find the password for the next level on this page.`

### Level 1

A webpage that displays the message `You can find the password for the next level on this page, but right clicking has been blocked!`

### Level 2, Level 3

A webpage that displays the message: `There is nothing on this page`.

### Level 4

A webpage with the following message:

```
Access disallowed. You are visiting from "" while authorized users should come only from "http://natas5.natas.labs.overthewire.org/"
```

### Level 5

A webpage with the following message:

`Access disallowed. You are not logged in`

## Leviathan Wargame

Leviathan is a wargame that has been rescued from the demise of `intruded.net`, previously hosted on `leviathan.intruded.net`. Big thanks to `adc`, `morla` and `reth` for their help in resurrecting this game!

What follows below is the original description of leviathan, copied from intruded.net:

```
Summary:
Difficulty:     1/10
Levels:         8
Platform:   Linux/x86

Author:
Anders Tonfeldt

Special Thanks:
We would like to thank AstroMonk for coming up with a replacement idea for the last level,
deadfood for finding a leveljump and Coi for finding a non-planned vulnerability.

Description:
This wargame doesn't require any knowledge about programming - just a bit of common
sense and some knowledge about basic *nix commands. We had no idea that it'd be this
hard to make an interesting wargame that wouldn't require programming abilities from
the players. Hopefully we made an interesting challenge for the new ones.
```

### Level 0, Level 1

`hidden`: There is no information for this level, intentionally.

## Bandit Wargame

### Level 0

Using SSH

### Level 0 -> Level 1

SSH to different user on same server with `ssh bandit1@localhost`

### Level 1

Reading contents of file with a dash name `-`

### Level 2

Reading contents of file with spaces in the filename

### Level 3

Viewing hidden files with `ls -a`

### Level 4

Looping over a list of files, check for human readable file using `file` command

### Level 5

Finding a file based on given requirements:

1. human-readable
1. 1033 bytes in size
1. not executable

### Level 6

Finding a password file stored _somewhere on the server_ and has the following properties:

1. Owned by user `bandit7`
1. Owned by group `bandit6`
1. 33 bytes in size

### Level 7

Finding a password stored in the file `data.txt` next to the word `millionth`

### Level 8

Finding a line of text (password) in `data.txt` that only occurs once

### Level 9

Finding a password in `data.txt` that is one of the few human-readable strings, preceded by several `=` characters

### Level 10

Finding a password in `data.txt`that contains base64 encoded data

### Level 11

Finding a password in `data.txt`, where all lowercase (a-z) and uppercase (A-Z) letters have been rotated by 13 positions (ROT13 algorithm)

### Level 12

Finding a password stored in the file `data.txt`, which is a hexdump of a file that has been repeatedly compressed. (Used commands: `mkdir`, `cp`, `mv`, `file`, `xxd` `bzip2`, `gzip`, `tar`)

### Level 13

The password for the next level is stored in `/etc/bandit_pass/bandit14` and can only be read by user `bandit14`. For this level, you don’t get the next password, but you get a private SSH key that can be used to log into the next level.

### Level 14

The password for the next level can be retrieved by submitting the password of the current level to port 30000 on `localhost`.

### Level 15

The password for the next level can be retrieved by submitting the password of the current level to port 30001 on localhost using SSL encryption.

Helpful note: Getting “HEARTBEATING” and “Read R BLOCK”? Use -ign_eof and read the “CONNECTED COMMANDS” section in the manpage. Next to ‘R’ and ‘Q’, the ‘B’ command also works in this version of that command…

### Level 16

The credentials for the next level can be retrieved by submitting the password of the current level to a port on `localhost` in the range 31000 to 32000.

First find out which of these ports have a server listening on them. Then find out which of those speak SSL and which don’t. There is only 1 server that will give the next credentials, the others will simply send back to you whatever you send to it.

### Level 17

There are 2 files in the homedirectory: `passwords.old` and `passwords.new`. The password for the next level is in `passwords.new` and is the only line that has been changed between `passwords.old` and `passwords.new`

`NOTE`: if you have solved this level and see ‘Byebye!’ when trying to log into `bandit18`, this is related to the next level, `bandit19`

### Level 18

The password for the next level is stored in a file `readme` in the home directory. Unfortunately, someone has modified .bashrc to log you out when you log in with SSH.

### Level 19

To gain access to the next level, you should use the `setuid` binary in the home directory. Execute it without arguments to find out how to use it. The password for this level can be found in the usual place (`/etc/bandit_pass`), after you have used the setuid binary.

### Level 20

There is a `setuid` binary in the home directory that does the following: it makes a connection to `localhost` on the port you specify as a commandline argument. It then reads a line of text from the connection and compares it to the password in the previous level (`bandit20`). If the password is correct, it will transmit the password for the next level (`bandit21`).

### Level 21

A program is running automatically at regular intervals from `cron`, the time-based job scheduler. Look in `/etc/cron.d/` for the configuration and see what command is being executed.

### Level 22

A program is running automatically at regular intervals from `cron`, the time-based job scheduler. Look in `/etc/cron.d/` for the configuration and see what command is being executed.

NOTE: Looking at shell scripts written by other people is a very useful skill. The script for this level is intentionally made easy to read. If you are having problems understanding what it does, try executing it to see the debug information it prints.

### Level 23

A program is running automatically at regular intervals from `cron`, the time-based job scheduler. Look in `/etc/cron.d/` for the configuration and see what command is being executed.

NOTE: This level requires you to create your own first shell-script. This is a very big step and you should be proud of yourself when you beat this level!

NOTE 2: Keep in mind that your shell script is removed once executed, so you may want to keep a copy around…

### Level 24

A daemon is listening on port `30002` and will give you the password for `bandit25` if given the password for `bandit24` and a secret numeric 4-digit pincode. There is no way to retrieve the pincode except by going through all of the 10000 combinations, called brute-forcing.

### Level 25

Logging in to `bandit26` from `bandit25` should be fairly easy… The shell for user `bandit26` is not `/bin/bash`, but something else. Find out what it is, how it works and how to break out of it.

### Level 26

The shell for user `bandit26` is not `/bin/bash`, but something else. Find out what it is, how it works and how to break out of it.

Good job getting a shell! Now hurry and grab the password for bandit27!

### Level 27

There is a git repository at `ssh://bandit27-git@localhost/home/bandit27-git/repo`. The password for the user `bandit27-git` is the same as for the user `bandit27`.

Clone the repository and find the password for the next level.

### Level 28

There is a git repository at `ssh://bandit28-git@localhost/home/bandit28-git/repo`. The password for the user `bandit28-git` is the same as for the user `bandit28`.

Clone the repository and find the password for the next level.

### Level 29

There is a git repository at `ssh://bandit29-git@localhost/home/bandit29-git/repo`. The password for the user `bandit29-git` is the same as for the user `bandit29`.

Clone the repository and find the password for the next level.

### Level 30

There is a git repository at `ssh://bandit30-git@localhost/home/bandit30-git/repo`. The password for the user `bandit30-git` is the same as for the user `bandit30`.

Clone the repository and find the password for the next level.

### Level 31

There is a git repository at `ssh://bandit31-git@localhost/home/bandit31-git/repo`. The password for the user `bandit31-git` is the same as for the user `bandit31`.

Clone the repository and find the password for the next level.

### Level 32

After all this git stuff its time for another escape. Good luck!

```console
WELCOME TO THE UPPERCASE SHELL
>> ls
sh: 1: LS: not found
```

# Markdown

1. [Code highlight in Markdown](https://stackoverflow.com/a/52586193)
1. [Markdown Reference](https://guides.github.com/features/mastering-markdown/)

# References

1. [Linux Man Pages](https://linux.die.net/man/)
1. [GNU binutils: Collection of binary tools](https://www.gnu.org/software/binutils/)
   1. Install via `sudo apt install binutils`
1. [Searching Through Man Page](https://askubuntu.com/a/20753)
1. [What does `~/` mean?](https://askubuntu.com/a/85150)
1. [Shell Scripting: Loops](https://www.shellscript.sh/loops.html)
1. [Piping and Redirection](https://ryanstutorials.net/linuxtutorial/piping.php)
1. [Base64 (MDN Web Docs Glossary)](https://developer.mozilla.org/en-US/docs/Glossary/Base64)
1. [How does tr '[a-z]' '[n-za-m]' work?](https://unix.stackexchange.com/a/19774)
1. [What is SSL?](https://www.ssl.com/faqs/faq-what-is-ssl/)
1. [s_client](https://linux.die.net/man/1/s_client)
1. [Running Nmap on WSL](https://exploits.run/nmap-wsl/)
1. [Nmap Cheat Sheet](https://hackertarget.com/nmap-cheatsheet-a-quick-reference-guide/)
1. [Linux diff command](https://www.computerhope.com/unix/udiff.htm)
1. [Setuid](https://www.computerhope.com/jargon/s/setuid.htm)
1. [/dev/null](https://www.journaldev.com/35489/dev-null-in-linux)
1. [Advanced Bash Scripting Guide: Chapter 20. I/O Redirection](http://www.tldp.org/LDP/abs/html/io-redirection.html)
1. [Linux cut command](https://www.computerhope.com/unix/ucut.htm)
1. [Bash Assign Output of Shell Command to Variable](https://www.cyberciti.biz/faq/unix-linux-bsd-appleosx-bash-assign-variable-command-output/)
1. [Bash scripting cheatsheet](https://devhints.io/bash)
1. [How to create a sequence with leading zeroes using brace expansion](https://unix.stackexchange.com/a/60259)
1. [Understanding the /etc/passwd file format](https://www.cyberciti.biz/faq/understanding-etcpasswd-file-format/)
1. [`more`(1) - Linux man page](https://linux.die.net/man/1/more)
1. [How to run Unix commands from within Vim?](https://superuser.com/a/285506)
1. [Vim Commands Cheat Sheet](https://www.fprintf.net/vimCheatSheet.html)
1. [What are the differences between local branch, local tracking branch, remote branch and remote tracking branch?](https://stackoverflow.com/a/16408515)
1. [Git tag](https://www.atlassian.com/git/tutorials/inspecting-a-repository/git-tag)
1. [Git Show](https://www.atlassian.com/git/tutorials/git-show)
1. [.gitignore](https://www.atlassian.com/git/tutorials/saving-changes/gitignore)
1. [sh(1) - Linux man page](https://linux.die.net/man/1/sh)
1. [Spying on Running Programs (strace. ltrace, system calls vs library calls)](https://www.youtube.com/watch?v=2AmP7Pse4U0)
