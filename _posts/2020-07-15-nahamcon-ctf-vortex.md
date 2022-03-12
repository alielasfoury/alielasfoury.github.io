---
title: nahamcon-ctf-vortex
post_title: Vortex Writeup - NahamCon CTF
categories:
  - writeups
tags:
  - ctf
  - writeup
  - nahamcon
  - bash
  - linux
  - misc
---

This is a writeup for Vortex challenge from NahamCon CTF.

![image](/assets/images/writeups/nahamcon-ctf/{{ page.title | remove: "nahamcon-ctf-" }}/1.png)

What we have for this challenge is a service running on port 50017, so lets connect to that port using netcat.

`nc jh2i.com 50017`

After connecting to that port, it continuously thrown an enourmous amount of non-readable characters to the standard output.

![image](/assets/images/writeups/nahamcon-ctf/{{ page.title | remove: "nahamcon-ctf-" }}/2.png)

So, let's connect again but this time we will pass all these non-readable characters to the strings command to get the printable characters then pipe the output to grep command to filter the flag string. It just took about 30 seconds to get the flag. Once it's found, just stop the command process by pressing `ctrl + c`.

![image](/assets/images/writeups/nahamcon-ctf/{{ page.title | remove: "nahamcon-ctf-" }}/3.png)

`flag{more_text_in_the_vortex}`
