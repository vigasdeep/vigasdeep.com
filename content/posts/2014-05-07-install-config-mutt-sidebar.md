---
title: Install + Config mutt-sidebar
author: Vigas Deep
type: post
date: 2014-05-06T20:06:18+00:00
url: /2014/05/07/install-config-mutt-sidebar/
dsq_thread_id:
  - 4468071994
categories:
  - Arch Linux
  - Linux
  - Mutt
  - Tutorial
  - Ubuntu
tags:
  - email folders
  - MUTT
  - sidebar

---
Hello everyone !

Lets make mutt more intersting by adding sidebar in mutt. Install it

<pre>For ubuntu
$ sudo apt-get install mutt-patched
</pre>

<pre>For Arch
$ sudo pacman -S package-query yaourt
$ sudo yaourt -S mutt-sidebar
</pre>

Add following to your .muttrc file and make changes accordingly.

<pre>#change width accordingly
set sidebar_width=30

#Visible at first, then change its value to yes
set sidebar_visible=no

set sidebar_delim='|'
set sidebar_sort=yes
mailboxes =inbox =ml
mailboxes =inbox =ml
bind index CP sidebar-prev
bind index CN sidebar-next
bind index CO sidebar-open
bind pager CP sidebar-prev
bind pager CN sidebar-next
bind pager CO sidebar-open
macro index b '&lt;enter-command>toggle sidebar_visible&lt;enter>'
macro pager b '&lt;enter-command>toggle sidebar_visible&lt;enter>'
bind index B bounce-message
</pre>

Shortcuts to use

<pre>CP = Previous folder in sidebar
CN = Next folder in sidebar
CO = Open Selected folder in sidebar
b = toggle sidebar
</pre>

If you want to change shortcuts, then change the values in .muttrc file accordingly.  
Enjoy your new mutt sidebar. 😛