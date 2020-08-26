---
title: Installing and Configuring mSMTP
author: Vigas Deep
type: post
date: 2014-05-05T22:49:57+00:00
url: /2014/05/06/installing-and-configuring-msmtp/
dsq_thread_id:
  - 4469711721
categories:
  - GnuPG
  - Linux
  - Mutt
  - Personal
  - Tutorial
tags:
  - mails
  - mSMTP
  - SMTP CLIENT

---
mSMTP is an SMTP client which can be used with various applications and scripts such as Mutt, Php, Python etc

Remember, we will do everything as a sudo user and NOT root. 

Install the **msmtp** and **ca-certificates** packages.

<pre>For Arch
$ sudo pacman -S msmtp ca-certificates
</pre>

<pre>For Debian/Ubuntu
$ sudo apt-get install msmtp ca-certificates
</pre>

<pre>For Fedora/Rhel/CentOS
$ sudo yum install msmtp ca-certificates
</pre>

Create a new .msmtprc file in your home directory and open it with your favourite editor. VIM neerds alert! (If you don&#8217;t know what this means, never mind. Just open the file.)

<pre>$ vim ~/.msmtmrc

</pre>

Copy following text into the .msmtprc file. If you have only one email ID, keep the default section, if you have more then two, add more accordingly. 

<pre>account default
host smtp.gmail.com
from email@youremailhost.com
auth on
port 587
user email@gmail.com
password MySecret
logfile ~/.msmtp.log
tls on
tls_starttls on
tls_trust_file /etc/ssl/certs/ca-certificates.crt


account custom
tls off
tls_starttls off
host smtp.youremailhost.com
from email@youremailhost.com
auth yes 
port 25
user email@youremailhost.com
passwordeval gpg -q --for-your-eyes-only --no-tty -d .mutt/.pass.gpg | awk '/email@youremailhost.com:/ {print $2}'
logfile ~/.msmtp.log
</pre>

As you can see I have two examples one with simple password and one with encrypted password. You can use **password** variable for basic use, as used for default account in .msmtprc file. If you don&#8217;t want your friends to see your password, who use your computer, and more specifically your user, then you should definately use **passwordeval** variable. **passwordeval** variable tells the msmtp to fetch password from an encryped gpg file. More details on <a href="https://wp.vigasdeep.com/mutt-encrypting-password-with-gnupg/" title="MUTT – encrypting password with GNUpg" target="_blank">Encrypting password in with GnuPG</a>, of course you need to see what you want from that link.

Test your configuration with following command

<pre>echo -e "Subject: Test Mail\r\n\r\nThis is a test mail" |msmtp --debug --from=default -t username@gmail.com
</pre>

It probably won&#8217;t work 😉 Change permissions of .msmtprc file then.

<pre>chmod 600 .msmtprc
</pre>

Doesn&#8217;t work? Apply common sense!

Still not working? poke me !