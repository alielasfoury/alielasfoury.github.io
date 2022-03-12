---
title: nahamcon-ctf-clisay
post_title: Clisay Writeup - NahamCon CTF
categories:
  - writeups
tags:
  - ctf
  - writeup
  - nahamcon
  - linux
  - bash
---

This is a write-up for Clisay challenge from NahamCon CTF.

![image](/assets/images/writeups/nahamcon-ctf/{{ page.title | remove: "nahamcon-ctf-" }}/01.png)

Let's download the file to see what we can do with it. Open up the terminal, then check the file type with the file command.

![image](/assets/images/writeups/nahamcon-ctf/{{ page.title | remove: "nahamcon-ctf-" }}/02.png)

It's just an executable file and if we run `ls -la` on the terminal to see the permissions of the file, we would see that it's not executable. So, let's give it the executable permission bit and try to run it.

`chmod +x clisay`

Now it's executable, let's run it.

![image](/assets/images/writeups/nahamcon-ctf/{{ page.title | remove: "nahamcon-ctf-" }}/03.png)

It just outputs some strings. let's see if it contains any interesting printable characters with the `strings` command tool.

![image](/assets/images/writeups/nahamcon-ctf/{{ page.title | remove: "nahamcon-ctf-" }}/04.png)

Done, We can easily notice the flag. It is splited into two halfs. We can use grep to extract its halfs then rejoin them again.

![image](/assets/images/writeups/nahamcon-ctf/{{ page.title | remove: "nahamcon-ctf-" }}/05.png)

If you don't like to copy and paste the two halfs XD, You can simply run the below line on the terminal.

![image](/assets/images/writeups/nahamcon-ctf/{{ page.title | remove: "nahamcon-ctf-" }}/06.png)

`flag{Y0u_c4n_r3Ad_M1nd5}`
