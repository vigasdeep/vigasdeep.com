---
title: 'Broadcom wireless problem : SOLVED'
author: Vigas Deep
type: post
date: 2012-08-28T04:10:09+00:00
url: /2012/08/28/broadcom-wireless-problem-solved/
categories:
  - Tutorial
tags:
  - Broadcom
  - fix
  - wireless

---
Most of Broadcom chips in laptop give problems in connecting to wireless signals, so here is the tested easy fix:

<pre># apt-get remove bcmwl-kernel-source</pre>

You may get it working 🙂 Reboot.