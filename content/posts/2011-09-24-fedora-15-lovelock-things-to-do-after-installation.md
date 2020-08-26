---
title: Fedora 15 (LoveLock) – Things to do after installation
author: Vigas Deep
type: post
date: 2011-09-24T09:32:59+00:00
url: /2011/09/24/fedora-15-lovelock-things-to-do-after-installation/
dsq_thread_id:
  - 4639765252
categories:
  - Fedora 15 (LoveLock)
  - Linux
tags:
  - 64 bit
  - Adobe Flash player
  - Broadcom wireless Drivers
  - F15
  - Fedora 15
  - GNOME 3
  - LoveLock
  - Nvidia Graphic Drivers

---
Recently I shifted from ubuntu 11.04 to fedora 15 (64 Bit), the graphics of fedora are pretty nice. As Fedora is redhat based, so its very different from ubuntu and hard to operate likely for basic users. I faced many problem regarding the installing the basic software, I found solutions by searching so hereby I share with everyone.

### **<span style="text-decoration: underline;">1) Adobe Flash Player only for 64 bit</span>**.

**Download ->**

`wget <a href="http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_2_p3_64bit_linux_111710.tar.gz">http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_2_p3_64bit_linux_111710.tar.gz</a>`

**Extract ->**

`tar xzvf flashplayer10_2_p3_64bit_linux_111710.tar.gz`

**Move to mozilla plugins folder ->**

`su -c 'cp libflashplayer.so /usr/lib64/mozilla/plugins/'`

The solution will work only for firefox, **if you also use Google Chrome**, you need to do an extra step after this

`sudo ln -s /usr/lib64/mozilla/plugin/libflashplayer.so /opt/google/chrome/plugins`

Restart your browsers and Hope it works.

### **<span style="text-decoration: underline;">2) Nvidia Graphic Drivers</span>**

First of all, **add rpmfusion repositories ->**

`su -c 'yum localinstall --nogpgcheck http://download1.rpmfusion.org/free/fedora/rpmfusion-free-release-stable.noarch.rpm http://download1.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-release-stable.noarch.rpm'`

**Install the Driver ->**

`su -c "yum install -y nvidia-settings nvidia-kmod"`

**REMEMBER, Do not Reboot**, one step left, or you will face a Blank Screen ->

`su -c "nvidia-xconfig"`

after this to ensure that computer will run properly again, we will recheck ->

`sudo gedit /bot/grub/grub.conf`

look for **rdblacklist=nouveau nouveau.modeset=0** in the file, if you found it, then it is okay, otherwise add code in the end of the file and make sure it is not commented ( # is used for comments).

Now **you can reboot** your machine, use this for configuring your graphic settings ->  
`su -c "nvidia-xconfig"`

### **<span style="text-decoration: underline;">3) Broadcom Wireless Drivers</span>**

**Adding the Repositories**, both free and non-free ->

`su -c 'rpm -Uvh http://download1.rpmfusion.org/free/fedora/rpmfusion-free-release-stable.noarch.rpm'`

`su -c 'rpm -Uvh http://download1.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-release-stable.noarch.rpm'`

**Update ->**

`sudo yum update`

**Install Wireless Drivers**

`sudo yum install kmod-wl`

Restart your system, Hope this works for you, worked for mine too !

Regards,