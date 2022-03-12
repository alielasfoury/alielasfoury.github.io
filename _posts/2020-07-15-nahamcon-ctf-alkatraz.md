---
title: nahamcon-ctf-alkatraz
post_title: Alkatraz Writeup - NahamCon CTF
categories:
  - writeups
tags:
  - ctf
  - writeup
  - nahamcon
  - bash
  - linux
  - misc
  - restricted_shell
---

This is a write-up for Alkatraz challenge from NahamCon CTF.

![image](/assets/images/writeups/nahamcon-ctf/{{ page.title | remove: "nahamcon-ctf-" }}/1.png)

Here is another service running on port 50024, so lets connect to that port.

After connecting, nothing is displayed but the connection still open, So what could be guessed here is that it's a shell. So by running `ls` command to list files, a `flag.txt` file is listed. But when I tried to display it's contents, it gave me the below error.

![image](/assets/images/writeups/nahamcon-ctf/{{ page.title | remove: "nahamcon-ctf-" }}/2.png)

it shows that the shell is `/bin/rbash` which is a restricted shell, that restricts some of the capabilities available to an interactive user session.

More info about Restricted shells: <https://en.wikipedia.org/wiki/Restricted_shell>

After spending a lot of time googling to bypass the restricted shell to read the contents of the flag.txt file, all the techniques failed but the below one just worked and I finally got the flag

![image](/assets/images/writeups/nahamcon-ctf/{{ page.title | remove: "nahamcon-ctf-" }}/3.png)

`flag{congrats_you_just_escaped_alkatraz}`
