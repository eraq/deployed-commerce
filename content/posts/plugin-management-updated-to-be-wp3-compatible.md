---
title: "Plugin Management Updated to be WP3 Compatible"
date: 2010-08-12
draft: false
---

*Originally published on erikshosting.com. Archived here.*

---

Plugin Management vs Plugin Commander, With WordPress MU Or Multi-Site

Plugin Management is far superior to Plugin Commander,

– The Problem is, Plugin Management is not WordPress 3 compatible.. Until Now!

So, I was recently working on a clients site. They were using the new wp3 and total commander. I prefer the wpmu dev teams plugin management plugin as I can disable a user from being able to activate a certain plugin.

So this client had a plugin that allowed php to be accepted in text widgets. now this is obviously a large security hole, and should only be available to the super admin (i.e Me). But with wp3, or plugin commander, you cant disable it from the plugin menu! A sub-blog administrator can go to the plugins menu and choose to enable the php widget! BIG problem. So I looked on different threads and found the only advice was ‘disable the plugin menu’, but what if you want your users to be able to enable certain plugins but not others? my users can enable facebook connect, nextgen gallery, twitter connect, etc, etc, but cannot enable any php allowed widgets, or any other unsecure plugins because i am using plugin mangement on wp3!

If this is exciting to you its because the wpmu team says ‘its difficult to find time for things that are free..’ meaning they havnt updated the plugin for wp3 yet. So, i went ahead and did it myself.

basically, wpmu-admin.php was replaced with ms-admin.php. So i made some minor corrections to the php, and voila! WP3 Compatible Plugin Management Plugin!

To Install:

Add the .php to /wp-content/mu-plugins/

IMPORTANT! Requires:

WP 3+

Use the Older Version for anything under wordpress 3.0
