---
title: 'Running server on Dynamic IP  : How to : DDNS'
author: Vigas Deep
type: post
date: 2012-05-05T16:56:33+00:00
url: /2012/05/05/running-server-on-dynamic-ip-how-to-ddns/
dsq_thread_id:
  - 3325026806
categories:
  - Network
  - Tutorial
tags:
  - DDNS
  - Dynamic DDNS
  - Dynamic IP to static IP

---
In this post, I will show you how to run any server while having dynamic IP in your home network. Its pretty simpler than you think. The concept behind it is DDNS, dynamic domain name server. There are many DDNS service providers you can choose any of them. I will suggest, make your account on http://dnsdynamic.org , which is a free DDNS provider, and is also operate able from web client. Create a domain in manage section of above website, run the web client for the domain you created, do not close your web bowser.<figure id="attachment_127" style="width: 800px" class="wp-caption alignleft">

[<img class="size-full wp-image-127" title="ddns_vigas-deep" src="https://wp.vigasdeep.com/wp-content/uploads/2012/05/ddns_vigas-deep.jpg" alt="DDNS Process" width="800" height="600" srcset="https://wp.vigasdeep.com/wp-content/uploads/2012/05/ddns_vigas-deep.jpg 800w, https://wp.vigasdeep.com/wp-content/uploads/2012/05/ddns_vigas-deep-300x225.jpg 300w" sizes="(max-width: 767px) 89vw, (max-width: 1000px) 54vw, (max-width: 1071px) 543px, 580px" />][1]<figcaption class="wp-caption-text">DDNS Process</figcaption></figure> 

As you always keep web client open, you IP address will be know to the DDNS server, so as it will forward request for your domain to your Dynamic IP. The next work is of your router, so you want to make a web server you have to forward all port 80 requests to you specified IP of your Desktop/Server. Similarly you can install SSH, FTP, TELNET servers, just by changing entries in the router, virtual server configuration.

To configure your router, you need to login to your router configuration wizard, and afterwards add an entry for your IP address, with port number accordingly. For more configuration wizard for your router, visit reference sheet of your router.

Enjoy free and private home servers. Good Luck.

Thanks.

&nbsp;

 [1]: https://wp.vigasdeep.com/wp-content/uploads/2012/05/ddns_vigas-deep.jpg