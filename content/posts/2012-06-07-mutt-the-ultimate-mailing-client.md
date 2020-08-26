---
title: MUTT – The Ultimate Mailing Client
author: Vigas Deep
type: post
date: 2012-06-07T15:54:55+00:00
url: /2012/06/07/mutt-the-ultimate-mailing-client/
dsq_thread_id:
  - 4469971567
categories:
  - Linux
  - Mutt
  - Tutorial
tags:
  - basic muttrc
  - MUTT
  - MUTT The ultimate email client
  - muttrc

---
<p style="text-align: left;">
  Mutt is a small but very powerful text-based mail client for Unix operating systems. The current stable public release version is 1.4.2.3; the current development release version is 1.5.21. For more information, refer : <a title="Mutt" href="http://mutt.org" target="_blank">http://mutt.org</a>
</p>

<p style="text-align: left;">
  <a href="https://wp.vigasdeep.com/wp-content/uploads/2012/06/mutt.png"><img title="mutt" src="https://wp.vigasdeep.com/wp-content/uploads/2012/06/mutt.png" alt="" width="724" height="463" /></a>
</p>

<p style="text-align: left;">
  First of all,
</p>

### [Download][1] Needed files.

<p style="text-align: left;">
  Next, Installing Mutt.
</p>

<pre>for Debian based : $ sudo apt-get install mutt urlview
for RPM based : $ sudo yum install mutt urlview</pre>

Thats it, mutt is installed, next you need to have a .muttrc configuration file now. Firstly execute following commands :

<pre>$ mkdir ~/.mutt
$ mkdir ~/.mutt/cache
$ mkdir ~/.mutt/cache/{bodies,headers}
$ touch ~/.mutt/certificates</pre>

Now look for muttrc file in the tar.gz archive, make changes according to your user,password and set your favourite editor to to compose messages. Place this file into your home directory and rename to **.muttrc** . Now you&#8217;re done, start mutt with :

<pre>$ mutt</pre>

Basic usage :

**enter** : To open a message and scroll down in a message  
**i** : To get back to all messages screen  
 **backspace** : To scroll up in a message  
**r** : To reply a message  
**m** : To compose  
**y** : To send composed email  
**left arrow** : To go to previous message in reading screen  
**right arrow** : To go to next message in reading screen  
**c** then **?** : To go to gmail folder list

That all for now, use &#8220;?&#8221; at any screen for help menu. Let your mouse, have some sleep ;-).

All email clients suck, this one just sucks less ~ Mutt.  
Happy Mutting !

 [1]: https://wp.vigasdeep.com/wp-content/uploads/2012/06/muttrc.tar.gz "Mutt files"