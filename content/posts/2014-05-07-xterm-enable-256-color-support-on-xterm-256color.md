---
title: 'xterm : enable 256 color support on : xterm-256color'
author: Vigas Deep
type: post
date: 2014-05-06T19:47:08+00:00
url: /2014/05/07/xterm-enable-256-color-support-on-xterm-256color/
dsq_thread_id:
  - 4474813270
categories:
  - Linux
  - Mutt
  - Tutorial
tags:
  - colorful terminal
  - MUTT
  - xterm
  - xterm-256color

---
You might need 256 bit color support in your various terminal applications like vim, mutt, mplayer, htop and others. Below are the instructions to enable 256 bit color support.

Pretty quick, issue command in your terminal

<pre>$ export TERM=xterm-256color
</pre>

To make it permanant, add the same to your .bashrc or .zshrc file, according to the shell you&#8217;re using.  
Test the output with

<pre>(x=`tput op` y=`printf %76s`;for i in {0..256};do o=00$i;echo -e ${o:${#o}-3:3} `tput setaf $i;tput setab $i`${y// /=}$x;done)
</pre>

That&#8217;s it, enjoy colors !