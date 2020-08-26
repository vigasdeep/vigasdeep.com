---
title: Troubleshoot Huawei E398 On Manjaro Linux
author: Vigas Deep
type: post
date: 2014-05-04T19:15:58+00:00
url: /2014/05/05/troubleshoot-huawei-e398-on-manjaro-linux/
dsq_thread_id:
  - 4470073332
categories:
  - Linux
  - Tutorial
tags:
  - arch
  - E398
  - Manjaro
  - Tata Photon
  - usb_modswitch

---
Its been days, my Tata Photon Plus device, E398 was not working properly on my favourite linux distro, Manjaro. So today I found some time to dig it and solve the problem.

Problem was that, My modem was showing up lsusb but was not getting detected by wvdial or dmesg.

<pre>$ lsusb
Bus 002 Device 009: ID 12d1:1505 Huawei Technologies Co., Ltd. E398 LTE/UMTS/GSM Modem/Networkcard</pre>

First of all, install following packages.

Here, note down following.  
Vendor ID = **12d1**  
Product ID = **1505**

Now install these packages.

<pre># pacman -S usb_modeswitch modemmanager wvdial ppp
</pre>

Edit this file after installing the packages

<pre>vim /lib/udev/rules.d/40-usb_modeswitch.rules
</pre>

Append following lines at the end, and replace Vendor ID and Product ID accordingly.

<pre>#Huawei E398
ATTR{idVendor}=="12d1", ATTR{idProduct}=="1505", RUN+="usb_modeswitch '%b/%k'"
</pre>

Issue following command to test

<pre># usb_modeswitch -v 12d1 -p 1505 -V 12d1 -P 1506 -M "55534243123456780000000000000011062000000100000000000000000000" 
</pre>

If everything goes right issue this command using your product and vendor ID.

<pre>modprobe option vendor=0x12d1 product=0x1506
</pre>

Replug the Modem, It will work like a charm. Keep me posted if you face any problems. 

Cheers !