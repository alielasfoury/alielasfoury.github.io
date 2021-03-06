---
title: nahamcon-ctf-uggc
post_title: UGGC Writeup - NahamCon CTF
categories:
  - writeups
tags:
  - ctf
  - writeup
  - nahamcon
  - web
  - rot13
---

This is a write-up for UGGC challenge from NahamCon CTF.

![image](/assets/images/writeups/nahamcon-ctf/{{ page.title | remove: "nahamcon-ctf-" }}/1.png)

<http://jh2i.com:50018>

This is an easy web challenge. Once I opened the above URL, I found a simple login page.

![image](/assets/images/writeups/nahamcon-ctf/{{ page.title | remove: "nahamcon-ctf-" }}/2.png)

After taking a look at the page source I found nothing interesting.

![image](/assets/images/writeups/nahamcon-ctf/{{ page.title | remove: "nahamcon-ctf-" }}/3.png)

So, lets try to login with any name and see what happens. I entered 'hello' as a username and clicked on login, and the response came up with a page saying that only admin can see the flag and a cookie-item named user with value 'uryyb'.

![image](/assets/images/writeups/nahamcon-ctf/{{ page.title | remove: "nahamcon-ctf-" }}/4.png)

So, let's go back again and login with 'admin' as a username. After trying to log in with 'admin', it responded that login as admin has been disabled!

![image](/assets/images/writeups/nahamcon-ctf/{{ page.title | remove: "nahamcon-ctf-" }}/5.png)

The only thing we have right now is the cookie-item named 'user'. The value of 'user' item is mostly encrypted, so we can take that value and try to decrypt it.

The first thing that came to my mind is that the value is mostly encrypted with [ROT13](https://en.wikipedia.org/wiki/ROT13). I tried to decrypt it using <https://rot13.com>

![image](/assets/images/writeups/nahamcon-ctf/{{ page.title | remove: "nahamcon-ctf-" }}/6.png)

And yes its ROT13 encrypted indeed and the output is 'hello' which is the username we tried to log in with before. So lets try to encrypt 'admin', Then get the encrypted output and change the value of the cookie-item 'user' with the encrypted value of 'admin' and resend the request/refresh the page and see what happens.

![image](/assets/images/writeups/nahamcon-ctf/{{ page.title | remove: "nahamcon-ctf-" }}/7.png)

Yeah, it worked and we finally captured the flag.

![image](/assets/images/writeups/nahamcon-ctf/{{ page.title | remove: "nahamcon-ctf-" }}/8.png)

`flag{H4cK_aLL_7H3_C0okI3s}`
