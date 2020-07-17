---
title: localghost
post_title: Localghost Writeup - NahamCon CTF
author: alielasfoury
categories:
- blog
- writeups
- NahamConCTF
tags:
- ctf
- writeup
- nahamcon
- web
---

This is a write-up for Localghost web challenge from NahamCon CTF.

![image](/assets/images/writeups/nahamcon-ctf/{{ page.title}}/1.png)

This is a web challenge, so the first thing we should so is go check the mentioned URL in the browser.

<http://jh2i.com:50003>

![image](/assets/images/writeups/nahamcon-ctf/{{ page.title}}/2.png)

The first thing we are going to do is to view the page source. In the page source there are two javascript files referenced. The first one is related to `code.jquery.com` so its not related to the challenge. But the second one is a relative path so its interesting, let's click on the file path to see it's content.

![image](/assets/images/writeups/nahamcon-ctf/{{ page.title}}/3.png)

Or we can just open inspect elements from the browser then open the debugger tool and see the javascript files loaded. The content of the file is an encoded javascript code. We can simply click on Pretty print source to see the code in a better way.

![image](/assets/images/writeups/nahamcon-ctf/{{ page.title}}/4.png)

Now we should see the code in a better way but some of it still encoded and obfuscated. So we have another option to decode and deobfuscate the code using online tool <https://beautifier.io/>. Copy the encoded JS code the paste it inside the text box in <https://beautifier.io/> then click on Beautify code.

![image](/assets/images/writeups/nahamcon-ctf/{{ page.title}}/5.png)

After the code has been beautified, the first thing you can notice is that it sets a localStorage item which called flag and it's content is the output of the `atob('somestringhere')` fuction.

![image](/assets/images/writeups/nahamcon-ctf/{{ page.title}}/6.png)

Lets go to the browser and open the Storage Inspector then choose the Local Storage and finally you will find the flag item and it's content.

Or we can simply open the browser console and write the below line of JavaScript code:

`window.localStorage.getItem('flag')`

![image](/assets/images/writeups/nahamcon-ctf/{{ page.title}}/7.png)

`JCTF{spoooooky_ghosts_in_storage}`
