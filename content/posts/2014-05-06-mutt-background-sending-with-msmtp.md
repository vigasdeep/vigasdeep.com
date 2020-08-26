---
title: 'MUTT : Background sending with mSMTP'
author: Vigas Deep
type: post
date: 2014-05-05T23:08:25+00:00
url: /2014/05/06/mutt-background-sending-with-msmtp/
dsq_thread_id:
  - 4481977436
categories:
  - Linux
  - Mutt
  - Tutorial
tags:
  - mSMTP
  - MUTT
  - sendmail

---
I am regular mutt user. Here is a good fix to remove waiting while the mutt interacts with the SMTP server to send an email. Previously I used a local mail server, now I am going to use mSMTP which is a SMTP Client just like mutt. We will let the mSMTP do the sending part in the background and will keep reading mails in the mutt, Sounds <span style="color: #33cccc;">cool</span>, eh ?

At First, Do <a title="Installing and Configuring mSMTP" href="https://wp.vigasdeep.com/installing-and-configuring-msmtp/" target="_blank">Install and Configure mSMTP</a>, don&#8217;t worry its a quick one.

Open your **.muttrc** file, <span style="color: #ff0000;">remove smtp_url</span> variable, or comment it.

<pre>#set smtp_url = "smtp://vigas@csiom.com@csiom.com"
</pre>

Append following, change things accordingly.

<pre>#sets path to msmtp command
set sendmail="/usr/bin/msmtp"
set envelope_from=yes

#Tells mSMTP to use which block of address to send the email
macro generic "1" ":set from=email@gmail.com"

#Background sending, Hurray !
set sendmail_wait=-1
</pre>

That&#8217;s it guys !

Feel free to share problems, if any. I&#8217;ll be back after some sleep.