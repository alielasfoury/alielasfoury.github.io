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

<img src="/assets/images/writeups/nahamcon-ctf/localghost/localghost01.png">

This is a web challenge so we should go check the mentioned URL in the browser.

<http://jh2i.com:50003>

<img src="/assets/images/writeups/nahamcon-ctf/localghost/localghost02.png">

The first thing we are going to do is to view the page source.

In the page source there are two javascript files referenced.

The first one is related to code.jquery.com so its not related to the challenge.

The second one is a relative path so its interesting, let's click on the file path to see it's content.

<img src="/assets/images/writeups/nahamcon-ctf/localghost/localghost03.png">

Or we can just open inspect elements from the browser then open the debugger and see the javascript files loaded.

The content of the file is an encoded javascript code.

We can simply click on Pretty print source to see the code in a better way

<img  src="/assets/images/writeups/nahamcon-ctf/localghost/localghost04.png">

Now we should see the code in a better way but some of it still encoded and obfuscated. So we have another option to decode and deobfuscate the code using online tool <https://beautifier.io/>

Copy the encoded JS code the paste it inside the text box in beautifier.io then click on Beautify code

<img src="/assets/images/writeups/nahamcon-ctf/localghost/localghost05.png">

After the code has been beautified, the first thing you can notice is that it sets a localStorage item which called flag and it's content is the output of the atob('somestringhere') fuction

<img src="/assets/images/writeups/nahamcon-ctf/localghost/localghost06.png">

Lets go to the browser and open the Storage Inspector then choose the Local Storage and finally you will find the flag item and it's content

Or we can simply open the browser console and write the below line of code:

window.localStorage.getItem('flag')

<img src="/assets/images/writeups/nahamcon-ctf/localghost/localghost07.png">
