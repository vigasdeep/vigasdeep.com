---
title: Console booting in Linux
author: Vigas Deep
type: post
date: 2013-02-05T17:52:09+00:00
url: /2013/02/05/console-booting-in-linux/
dsq_thread_id:
  - 4639765183
categories:
  - Linux
  - Tutorial
  - Ubuntu
tags:
  - boot
  - cinnamon
  - command line
  - Console boot
  - gnome-classic
  - grub
  - Linux
  - startx

---
Usually all the linux distributions do start the graphical environment automatically. Its good, but it becomes little pain of linux nerds, they want to use it in there own ways. So this is a simple trick which will enable you to boot in console mode with help of Grub.

You just need to edit the following file.  
`</p>
<pre>
/etc/default/grub
</pre>
<p>`

And the find the following line  
`</p>
<pre>
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
</pre>
<p>`

and replace it with following.

`</p>
<pre>
GRUB_CMDLINE_LINUX_DEFAULT="text"
</pre>
<p>`

Save the file and then execute following command in the command window ( Terminal / Console ).  
`</p>
<pre>
sudo update-grub
</pre>
<p>`  
Thats is, next time you are going to boot in console mode. But, next thing is how run the graphical console.

Just do this, and it will run you default graphical manager.  
`</p>
<pre>
startx
</pre>
<p>`

If you wish to do some other Graphical desktop then you have to create and .xinitrc file inside your home directory.

**Few examples of .xinitrc files :  
**  
Example 1 : For cinnamon desktop environment.  
`</p>
<pre>
#!/bin/sh
#exec gnome-session
exec gnome-session --session=cinnamon
</pre>
<p>`

Example 2 : For gnome classic.  
`</p>
<pre>
#!/bin/sh
#exec gnome-session
exec gnome-session --session=gnome-classic
</pre>
<p>`

Enjoy tweaking.