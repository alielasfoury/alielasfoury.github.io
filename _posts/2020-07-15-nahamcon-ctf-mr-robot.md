---
title: nahamcon-ctf-mr-robot
post_title: Mr Robot Writeup - NahamCon CTF
categories:
  - writeups
tags:
  - ctf
  - writeup
  - nahamcon
  - web
---

This is a write-up for Mr Robot challenge from NahamCon CTF.

![image](/assets/images/writeups/nahamcon-ctf/{{ page.title | remove: "nahamcon-ctf-" }}/1.png)

In this challenge we have got a URL. The first thing to do is to open the URL in the browser. Let's go to <http://jh2i.com:50032>

![image](/assets/images/writeups/nahamcon-ctf/{{ page.title | remove: "nahamcon-ctf-" }}/2.png)

It's just a simple website with an image of Mr. Robot and some text. If we displayed the page source, we will not find anything interesting. Even, there isn't any script file loaded in the page.

![image](/assets/images/writeups/nahamcon-ctf/{{ page.title | remove: "nahamcon-ctf-" }}/3.png)

Let's look if the website has a `robots.txt` file to get any information from it.

But once we open it, we found the flag. Yeah it's so easy XD.

![image](/assets/images/writeups/nahamcon-ctf/{{ page.title | remove: "nahamcon-ctf-" }}/4.png)

`flag{welcome_to_robots.txt}`
