---
title: 'WordPress : Website for logged in users only'
author: Vigas Deep
type: post
date: 2012-08-12T23:19:46+00:00
url: /2012/08/13/wordpress-website-for-logged-in-users-only/
dsq_thread_id:
  - 4577872024
categories:
  - Uncategorized

---
If you want to hide your wordpress website, so that, only logged in users may access it. So, here&#8217;s the quick fix.

append following code into your **wp-blog-header.php file** right below **wp();** 

<pre>//****************************************************//        
/////////////////////////// Require login to view website
get_currentuserinfo();
global $user_ID;
if ($user_ID == '')
{
        header('Location: wp-login.php');
}
////////////////////////// Require login to view website
//*****************************************************//
</pre>

Thats it. Simple enough ?