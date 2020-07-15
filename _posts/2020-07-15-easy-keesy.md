---
title: easy-keesy
post_title: Easy Keesy writeup - NahamCon CTF
categories:
- blog
- writeups
- NahamConCTF
tags:
- ctf
- writeup
- nahamcon
- bash
- password_cracking
- hashcat
---

This is a writeup for Easy Keesy challenge from NahamCon CTF.

![image](/assets/images/writeups/nahamcon-ctf/{{ page.title}}/1.png)

After we download the file, the first thing we should do is checking the file type

![image](/assets/images/writeups/nahamcon-ctf/{{ page.title}}/2.png)

Actually, I didn't even know what is Keepass password database 2.x KDBX file

so I googled it and found it's just a database file for an open-source password manager called KeePass. 

Then I tried to get a tool to open it. which is kpcli - A command line interface to KeePass database files.

and off course, It asked for a master password!

![image](/assets/images/writeups/nahamcon-ctf/{{ page.title}}/3.png)

After googling, I found a way to crack the kdbx file password hash with hashcat

https://madcityhacker.com/2018/11/04/cracking-keepass-databases-with-hashcat/

The first step is to extract the hash out of the KeePass database file

then we will use John the Ripper to extract the master password hash out of the database file

![image](/assets/images/writeups/nahamcon-ctf/{{ page.title}}/4.png)

We now have our extracted hash file  named easy_keesy_hash ready to be cracked. 

we will be using Hashcat for cracking the password

before we proceed with cracking the password with hashcat, we first need to delete the file name from the hash value

![image](/assets/images/writeups/nahamcon-ctf/{{ page.title}}/5.png)

it will be like that

![image](/assets/images/writeups/nahamcon-ctf/{{ page.title}}/6.png)

Now we are ready to let hashcat crack the password.

![image](/assets/images/writeups/nahamcon-ctf/{{ page.title}}/7.png)

we used --show to display the password which is monkeys

after cracking the password, let's go back to kpcli to open the KDBX file with the master password we just cracked

![image](/assets/images/writeups/nahamcon-ctf/{{ page.title}}/8.png)

after opening the file successfuly and navigating through the database file we can get the flag saved as a password entry

flag{jtr_found_the_keys_to_kingdom}
