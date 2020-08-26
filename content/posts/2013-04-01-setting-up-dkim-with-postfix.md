---
title: Setting up openDKIM with Postfix (+ Troubleshooting)
author: Vigas Deep
type: post
date: 2013-03-31T21:49:42+00:00
url: /2013/04/01/setting-up-dkim-with-postfix/
dsq_thread_id:
  - 4486883578
categories:
  - Linux
  - Tutorial
  - Ubuntu
tags:
  - DKIM
  - DNS TXT
  - DomainKeys

---
### Introduction

DomainKeys Identified Mail, abbreviated as DKIM. It is a protocol which ensures that, the emails received are from right and authentic senders, and are not forged. DKIM uses public key cryptography [wiki link]. Most of the times when you deal with a mail server, emails are unfortunately going into spam, because your DNS does not have a DomainKey record, which authenticates the emails coming from your domain.

### Requirements 

  1. I assume you are familiar with **Debian** based distrubution.
  2. You are having **postfix** mail server, this guide deals with postfix only.
  3. You have knowledge of basic linux commands

### Installation 

You can simply issue issue the following command to install openDKIM.

<pre>sudo aptitude install opendkim opendkim-tools dkim-filter
</pre>

### Configuration

Two configuration files of DKIM.

<pre>/etc/opendkim.conf
/etc/default/opendkim 
/etc/default/dkim-filter
</pre>

Firstly edit, **/etc/opendkim.conf** , Make sure your file do have these. Just edit &#8220;Domain&#8221; and &#8220;Selector&#8221;.

<pre>Domain                  vigasdeep.com #Use your domain here
KeyFile                 /etc/mail/dkim.key # We will generate this key later on
Selector                mail #this can be anything

# DomainKey is combined with "Selector" and "Domain", including an extra string "_domainkey"
# For Example mail._domainkey.vigasdeep.com

# Common settings. See dkim-filter.conf(5) for more information.
AutoRestart             yes
Background              yes
Canonicalization        relaxed/relaxed
DNSTimeout              5
Mode                    sv
SignatureAlgorithm      rsa-sha256
SubDomains              no
X-Header                no

</pre>

After that, edit **/etc/default/dkim-filter** and make sure it have following

<pre>DAEMON_OPTS="-l -o DKIM-Signature,X-DKIM"
DAEMON_OPTS="$DAEMON_OPTS -d vigasdeep.com -k /etc/mail/dkim.key -s mail"
SOCKET="inet:8891@localhost"
</pre>

Now we&#8217;ll edit **/etc/postfix/main.cf** file. Append following text into the file.

<pre># DKIM
milter_default_action = accept
milter_protocol = 2
smtpd_milters = inet:localhost:8891
non_smtpd_milters = inet:localhost:8891
</pre>

Thats all for the Configuration.

### Generate Public/Private key for DKIM 

This command with generate a public/private key pair. Replace &#8220;mail&#8221; with your own selector, and &#8220;vigasdeep.com&#8221; with your domain name.

<pre>opendkim-genkey -t -s mail -d vigasdeep.com
</pre>

After this, place the private key to its right place at **/etc/mail/dkim.key**

<pre>cp mail.private /etc/mail/dkim.key  
# here <strong>mail</strong> refers to the selector
</pre>

Thats it. 

Optionally, you can also create a public/private key pair from **<a href="http://dkimcore.org/tools/" title="DKIM public/private key generator" target="_blank">http://dkimcore.org/tools/</a>**. Change Selector accordingly into **/etc/opendkim.conf** file.

If you have generated the keys on the web, then create a new file **/etc/mail/dkim.key** and paste private key into it.

### Adding DNS (txt record) for domainkey

Adding the DNS entry is the most crucial part, please be patient and read carefully. When you created public/private key pair. Use public key for DNS entry. Login to your domain&#8217;s control panel, change DNS Settings, and add a TXT record. TXT record will ask you for two things. **Host** and **Data**.

Host will be ( change accordingly for your case )

<pre>mail._domainkey.vigasdeep.com
## [Selector]._domainkey.[domain.com]
</pre>

and data would be something like

<pre>"v=DKIM1;=rsa; t=y; p=MIGfMA0GCSqGSIb3DQEBAQUAA4GNADCBiQKBgQC8O7fJSx/nbZfzy75pfMnSO57Y0/xyIQQfrWUFwo2PXIamDSII7KB83u0MBeSrt1TPAnSmcRlKIurEBD8xF1Um8cnM/D2W5BlPqKTiII9CHLNEiCKYJiG1EuB+5Wl47UCHnmRaX3+PrbB/r1AWEmT+8cNbz4FW60mQaEIHBFsgwIDAQAB"
</pre>

Add the entry, and you&#8217;re done. Now we will test it out.

### Starting DKIM and Troubleshooting

<pre>sudo service opendkim start
</pre>

If you&#8217;re not able to send email, probably there is something wrong with the configuration. Check the mail logs.

<pre>grep -i dkim /var/log/mail.log
</pre>

Check if DKIM is working correctly at <a href="http://dkimcore.org/tools/keycheck.html" title="DKIM Key Check" target="_blank"><strong>http://dkimcore.org/tools/keycheck.html</strong></a>

Facing problems ? Post comment Or Hire me, I&#8217;ll be back after my &#8220;Double-Tikki&#8221; Burger. Hah !