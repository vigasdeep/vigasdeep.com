---
title: MUTT – encrypting password with GNUpg
author: Vigas Deep
type: post
date: 2012-06-08T10:25:55+00:00
url: /2012/06/08/mutt-encrypting-password-with-gnupg/
dsq_thread_id:
  - 4469713916
categories:
  - GnuPG
  - Linux
  - Mutt
  - Tutorial
tags:
  - Encrypt
  - GNUpg
  - MUTT The ultimate email client
  - Password

---
To encrypt password with mutt, we will be using GNUpg, install it :

<pre>For Debian based : $ sudo apt-get install gnupg gnupg-agent
For RPM based : $ sudo yum install gnupg gnupg-agent
</pre>

after installing it you need to generate an encryption key by using following.

<pre>gpg --gen-key
</pre>

Select appropriate options. Enter you name, email and passphare when it asks. Do not forget your passphrase.  
now create a file .pass place it in your home folder, I am placing it here :

<pre>touch ~/.mutt/.pass
</pre>

contents fo following file should be :

<pre>GMail:&lt;use tab>mySecretPassowrd
</pre>

encrypt it by using:

<pre>cd ~/.mutt
gpg --encrypt .pass
</pre>

Now you will see a file is created as .pass.gpg , if it is there, you can delete orignal .pass file. After this step you have to make changes to .muttrc file. Append the following by doing appropriate changes

<pre>set imap_pass = `gpg -d ~/.mutt/.pass.gpg | awk '/GMail:/ {print $2}'`
</pre>

NOTE : if imap\_pass and smtp\_pass are defined anywhere else, you have to remove them or comment those two lines like this :

<pre>#&lt;s>set imap_pass = ""&lt;/s>
#&lt;s>set smtp_pass = ""&lt;/s>
</pre>

Thats it, now you can start mutt and it will ask the passphrase for your key, and will never irritate you again 🙂  
Good Luck.