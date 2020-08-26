---
title: Editing Ubuntu Menu
author: Vigas Deep
type: post
date: 2011-03-24T16:51:16+00:00
url: /2011/03/24/editing-ubuntu-menu/
dsq_thread_id:
  - 2668036740
categories:
  - Ubuntu
tags:
  - Menu Editing
  - Ubuntu 10.04 LTS

---
Hello Everyone !

Okay, today I&#8217;am going to show how to edit menus in ubuntu 10.04 LTS.

Yesterday I was facing the problem that my application menu in the menu bar not showing the child nodes/options on clicking, I found a solution for this problem and I want to share this with you guys.

<p style="text-align: center;">
  <a href="https://wp.vigasdeep.com/wp-content/uploads/2011/03/before.jpg"><img class="size-full wp-image-28 aligncenter" title="application menu not working." src="https://wp.vigasdeep.com/wp-content/uploads/2011/03/before.jpg" alt="application menu not working." width="471" height="263" srcset="https://wp.vigasdeep.com/wp-content/uploads/2011/03/before.jpg 471w, https://wp.vigasdeep.com/wp-content/uploads/2011/03/before-300x167.jpg 300w" sizes="(max-width: 471px) 100vw, 471px" /></a>
</p>

<p style="text-align: center;">
  Here , checkout the application menu, no options are appearing. So to make it work goto the following directory and look for the files mentioned below.
</p>

`/usr/share/app-install/desktop`

 `1. Menu Editor<br />
2. Main Menu`

visuals for these files look like ..

firstly for the menu editor.

<p style="text-align: center;">
  <a href="https://wp.vigasdeep.com/wp-content/uploads/2011/03/Screenshot-Edit-Menus.jpg"><img class="size-full wp-image-30 aligncenter" title="Screenshot-Edit Menus" src="https://wp.vigasdeep.com/wp-content/uploads/2011/03/Screenshot-Edit-Menus.jpg" alt="Menu Editor " width="492" height="348" srcset="https://wp.vigasdeep.com/wp-content/uploads/2011/03/Screenshot-Edit-Menus.jpg 615w, https://wp.vigasdeep.com/wp-content/uploads/2011/03/Screenshot-Edit-Menus-300x212.jpg 300w" sizes="(max-width: 492px) 100vw, 492px" /></a>
</p>

secondly the  Main Menu

<p style="text-align: center;">
  <a href="https://wp.vigasdeep.com/wp-content/uploads/2011/03/Screenshot-Main-Menu.jpg"><img class="size-full wp-image-31 aligncenter" title="Screenshot-Main Menu" src="https://wp.vigasdeep.com/wp-content/uploads/2011/03/Screenshot-Main-Menu.jpg" alt="edit the main menus." width="472" height="371" srcset="https://wp.vigasdeep.com/wp-content/uploads/2011/03/Screenshot-Main-Menu.jpg 675w, https://wp.vigasdeep.com/wp-content/uploads/2011/03/Screenshot-Main-Menu-300x235.jpg 300w" sizes="(max-width: 472px) 100vw, 472px" /></a>
</p>

Firstly, you must select the options in the Menu Editor, if they are not select in the Menu Editor, they cannot be shown. Then after select the options in the Main Menu. I did the same and I got it working.

<p style="text-align: center;">
  <a href="https://wp.vigasdeep.com/wp-content/uploads/2011/03/done.jpg"><img class="size-full wp-image-32 aligncenter" title="done" src="https://wp.vigasdeep.com/wp-content/uploads/2011/03/done.jpg" alt="" width="295" height="376" srcset="https://wp.vigasdeep.com/wp-content/uploads/2011/03/done.jpg 295w, https://wp.vigasdeep.com/wp-content/uploads/2011/03/done-235x300.jpg 235w" sizes="(max-width: 295px) 100vw, 295px" /></a>
</p>

Okay, thats all for now.  
Happy Menu Editing.  
Good Day !

~ Vigas Deep