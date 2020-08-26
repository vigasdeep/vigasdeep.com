---
title: Ubuntu 12.10 – Maximizing Battery Backup
author: Vigas Deep
type: post
date: 2012-11-11T17:05:35+00:00
url: /2012/11/11/ubuntu-12-10-maximizing-battery-backup/
categories:
  - Linux
  - Tutorial
  - Ubuntu
tags:
  - Disks
  - Jupiter Applet
  - PowerTOP

---
Here is a quick tutorial, to maximize battery backup of your laptop. This is based on ubuntu 12.10, which has many improved feature which you need to tweak to improve the backup.  
[<img src="https://wp.vigasdeep.com/wp-content/uploads/2012/11/Backup-time.jpg" caption="Backup Time" border="1" alt="" title="Backup time" width="325" height="230" class="alignleft size-full wp-image-205" srcset="https://wp.vigasdeep.com/wp-content/uploads/2012/11/Backup-time.jpg 325w, https://wp.vigasdeep.com/wp-content/uploads/2012/11/Backup-time-300x212.jpg 300w" sizes="(max-width: 325px) 100vw, 325px" />][1]

Tools used are :  
1. &#8220;Disks&#8221; 3.6.1  
2. [Jupiter Applet][2]  
3. PowerTop 

Disks, This program comes default with ubuntu 12.10, it has many improved features this time. One important feature is, it also controls HDD Drive speed, which can end up in maximizing performance to battery.  
[<img src="https://wp.vigasdeep.com/wp-content/uploads/2012/11/Disks-Program.jpg" border="1" alt="" title="Disks Program" width="679" height="267" class="alignleft size-full wp-image-206" srcset="https://wp.vigasdeep.com/wp-content/uploads/2012/11/Disks-Program.jpg 679w, https://wp.vigasdeep.com/wp-content/uploads/2012/11/Disks-Program-300x117.jpg 300w" sizes="(max-width: 679px) 100vw, 679px" />][3]

After opening the Drive Settings, It shows power managements options for HDD. You can set power as low as possible to increase the Drive speed.

[<img src="https://wp.vigasdeep.com/wp-content/uploads/2012/11/Power-Settings.jpg" alt="" title="Power Settings" width="645" height="593" class="alignleft size-full wp-image-208" srcset="https://wp.vigasdeep.com/wp-content/uploads/2012/11/Power-Settings.jpg 645w, https://wp.vigasdeep.com/wp-content/uploads/2012/11/Power-Settings-300x275.jpg 300w" sizes="(max-width: 645px) 100vw, 645px" />][4]

Next is, Jupiter applet, <a href="http://www.webupd8.org/2010/07/jupiter-ubuntu-ppa-hardware-and-power.html" title="install it from here" target="_blank"></a>, after installing, start the jupiter applet and change power settings to Power Saving Mode.

[<img src="https://wp.vigasdeep.com/wp-content/uploads/2012/11/Power-Saving-Mode.jpg" border="1" alt="" title="Power Saving Mode" width="419" height="356" class="alignleft size-full wp-image-207" srcset="https://wp.vigasdeep.com/wp-content/uploads/2012/11/Power-Saving-Mode.jpg 419w, https://wp.vigasdeep.com/wp-content/uploads/2012/11/Power-Saving-Mode-300x254.jpg 300w" sizes="(max-width: 419px) 100vw, 419px" />][5]

Next and the last is, PowerTOP, install it by typing the terminal.

<pre>$ sudo apt-get install powertop</pre>

After installing it, give command in the terminal. 

<pre>$ sudo powertop </pre>

Your application will start running, switch screens with left and right arrow, and get into &#8220;Tuneable Tab&#8221; and change all setting which are bad.

[<img src="https://wp.vigasdeep.com/wp-content/uploads/2012/11/powerTOP.jpg" alt="" title="powerTOP" width="723" height="432" border="1" class="alignleft size-full wp-image-209" srcset="https://wp.vigasdeep.com/wp-content/uploads/2012/11/powerTOP.jpg 723w, https://wp.vigasdeep.com/wp-content/uploads/2012/11/powerTOP-300x179.jpg 300w" sizes="(max-width: 723px) 100vw, 723px" />][6]

Thats what made my battery backup approximately 80 minutes more then my normal battery backup, Thanks for reading, I hope you find this post helpful.

 [1]: https://wp.vigasdeep.com/wp-content/uploads/2012/11/Backup-time.jpg
 [2]: http://jupiterapplet.org/
 [3]: https://wp.vigasdeep.com/wp-content/uploads/2012/11/Disks-Program.jpg
 [4]: https://wp.vigasdeep.com/wp-content/uploads/2012/11/Power-Settings.jpg
 [5]: https://wp.vigasdeep.com/wp-content/uploads/2012/11/Power-Saving-Mode.jpg
 [6]: https://wp.vigasdeep.com/wp-content/uploads/2012/11/powerTOP.jpg