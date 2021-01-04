---
title: nahamcon-ctf-pang
post_title: Pang Writeup - NahamCon CTF
categories:
  - writeups
tags:
  - ctf
  - writeup
  - nahamcon
  - bash
  - misc
---

This is a write-up for Pang challenge from NahamCon CTF.

![image](/assets/images/writeups/nahamcon-ctf/{{ page.title | remove: "nahamcon-ctf-" }}/1.png)

What we got in this challenge is a file. After downloading the file and checking its type, we found it's a png image.

![image](/assets/images/writeups/nahamcon-ctf/{{ page.title | remove: "nahamcon-ctf-" }}/2.png)

But if we tried to open it with any image viewer, it gives the below error.

![image](/assets/images/writeups/nahamcon-ctf/{{ page.title | remove: "nahamcon-ctf-" }}/3.png)

Error: `Fatal error reading PNG image file: IHDR: CRC error`

I googled the above error and found that the png image is missing something and needs a repair. Then, I searched for a tool to repair the png image and I found a tool on github to check and repair png images which I found very useful.

<https://github.com/sherlly/PCRT>

![image](/assets/images/writeups/nahamcon-ctf/{{ page.title | remove: "nahamcon-ctf-" }}/4.png)

After running the tool on the image, it found errors and prompted to repair it and finally it repaired the image.

![image](/assets/images/writeups/nahamcon-ctf/{{ page.title | remove: "nahamcon-ctf-" }}/5.png)

Let's see the new repaired image `output.png`

![image](/assets/images/writeups/nahamcon-ctf/{{ page.title | remove: "nahamcon-ctf-" }}/6.png)

Yes, it has the flag and we can run `image2text` tool mentioned below to get the text out of the image. It's not that accurate, but at least you won't rewrite this long flag from the beginning, just a few characters to write or replace.

<https://github.com/prabhakar267/image2text>

![image](/assets/images/writeups/nahamcon-ctf/{{ page.title | remove: "nahamcon-ctf-" }}/7.png)

`flag{wham_bam_thank_you_for_the_flag _maam}`
