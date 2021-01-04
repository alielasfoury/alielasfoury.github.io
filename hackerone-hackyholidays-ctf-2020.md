---
title: hackerone-hackyholidays-ctf-2020
categories:
  - writeups
post_title: HackerOne Hacky Holidays CTF 2020 Write-up
post_thumbnail: assets/images/writeups/hackerone-hackyholidays-ctf-2020/grinch.png
---

https://hackyholidays.h1ctf.com/

### First Flag:

After enumerating the main web page for hackyholidays.h1ctf.com, the first flag is found exposed at the robots.txt file on the server.

https://hackyholidays.h1ctf.com/robots.txt

![]({{ 'assets/images/writeups/hackerone/hackyholidays-h1-ctf-2020/1.png' | relative_url }})

**`flag{48104912-28b0-494a-9995-a203d1e261e7}`**

Also another endpoint https://hackyholidays.h1ctf.com/s3cr3t-ar3a is found exposed in the robots.txt file
