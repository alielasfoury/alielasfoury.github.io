---
title: nahamcon-ctf-metameme
categories:
  - writeups
post_title: Metameme Writeup - NahamCon CTF
tags:
  - ctf
  - writeup
  - bash
---

This is a write-up for Metameme challenge from NahamCon CTF.

![image](/assets/images/writeups/nahamcon-ctf/{{ page.title | remove: "nahamcon-ctf-" }}/01.png)

Again, we have just a file for this challenge and the file is an image.

![image](/assets/images/writeups/nahamcon-ctf/{{ page.title | remove: "nahamcon-ctf-" }}/02.png)

Mostly there would be some hidden data inside that image. So, let's use `exiftool` to see the meta information of the image so we can get anything important.

![image](/assets/images/writeups/nahamcon-ctf/{{ page.title | remove: "nahamcon-ctf-" }}/03.png)

dadaaa, the flag is lying down there! Another easy challenge!

`flag{N0t_7h3_4cTuaL_Cr3At0r}`

Also, we could have used strings command to see the printable characters in the image file.

![image](/assets/images/writeups/nahamcon-ctf/{{ page.title | remove: "nahamcon-ctf-" }}/04.png)
