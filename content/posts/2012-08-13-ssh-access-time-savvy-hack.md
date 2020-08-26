---
title: 'SSH access : Time saVVy Hack'
author: Vigas Deep
type: post
date: 2012-08-12T22:51:23+00:00
url: /2012/08/13/ssh-access-time-savvy-hack/
dsq_thread_id:
  - 2823026568
categories:
  - Linux
  - Tutorial
tags:
  - Savy tech
  - SSH
  - SSH Fingerprint
  - SSH-keygen

---
If you deal with a lot of servers and SSH connections, then this post is a must read for you, welcome.

I will go through some easy tricks, which will make your SSH login to server without asking a things.

How to setup :

  1. Setup key based SSH access
  2. Command alias

Start with issuing following commands :

`$ ssh-keygen`

Then ssh-keygen will ask you the filename in which to store the generated key in ~/.ssh/YourFileName  
[<img src="https://wp.vigasdeep.com/wp-content/uploads/2012/08/Screenshot-10.png" alt="" title="Screenshot-10" width="632" height="422" class="alignleft size-full wp-image-168" srcset="https://wp.vigasdeep.com/wp-content/uploads/2012/08/Screenshot-10.png 632w, https://wp.vigasdeep.com/wp-content/uploads/2012/08/Screenshot-10-300x200.png 300w" sizes="(max-width: 632px) 100vw, 632px" />][1]  
Next, copy the key&#8217;s .pub file to the server, which you want to connect using ssh. 

`$ ssh-copy-id -i ~/.ssh/YourFileName.pub user@server.com`

now open you ~/.bashrc file, and add alias. Paste this code in the end of your .bashrc file, and change values accordingly

`alias conny='ssh user@server'`

Save and exit, thats it, you just run $ conny or any other name you wrote there. It will setup an SSH connection directly to the server.

 [1]: https://wp.vigasdeep.com/wp-content/uploads/2012/08/Screenshot-10.png