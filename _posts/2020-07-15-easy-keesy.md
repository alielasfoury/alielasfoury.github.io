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

This is a write-up for Easy Keesy challenge from NahamCon CTF.

![image](/assets/images/writeups/nahamcon-ctf/{{ page.title}}/1.png)

In this challenge we have a file. After we download the file, the first thing we should do is checking its type with file command.

![image](/assets/images/writeups/nahamcon-ctf/{{ page.title}}/2.png)

Actually, I didn't even know what is Keepass password database 2.x KDBX file. So, I googled it and found it's just a database file for an open-source password manager called KeePass. Then I tried to get a tool to open it. I found a command line tool callend `kpcli` - A command line interface to KeePass database files. But, It asked for a master password!

![image](/assets/images/writeups/nahamcon-ctf/{{ page.title}}/3.png)

Again, after some googling, I found a way to crack the kdbx file password-hash with `hashcat` famous tool.

Check this link:
<https://madcityhacker.com/2018/11/04/cracking-keepass-databases-with-hashcat/>

The first step is to extract the hash out of the KeePass database file. We will use John the Ripper tool `keepass2john` to extract the password-hash out of the database file.

![image](/assets/images/writeups/nahamcon-ctf/{{ page.title}}/4.png)

Now we have extracted the hash in a file named `easy_keesy_hash` and it's ready to be cracked using Hashcat. But before we proceed with cracking the password with hashcat, we first need to delete the file name from the hash value as shown in the image.

![image](/assets/images/writeups/nahamcon-ctf/{{ page.title}}/5.png)

It will be like that:

![image](/assets/images/writeups/nahamcon-ctf/{{ page.title}}/6.png)

Now we are ready to let hashcat crack the password.

![image](/assets/images/writeups/nahamcon-ctf/{{ page.title}}/7.png)

You can check `hashcat` man page from the terminal to know more about it and how to use it. 

The password has been cracked and it is 'monkeys'.

Now we have the password let's go back to `kpcli` to open the KDBX file with the master password we just cracked.

After opening the file successfuly and navigating through the database file we can get the flag saved as a password entry.

![image](/assets/images/writeups/nahamcon-ctf/{{ page.title}}/8.png)

`flag{jtr_found_the_keys_to_kingdom}`
