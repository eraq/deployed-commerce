---
title: "Limit Login Attempts WPMU"
date: 2012-02-21
draft: false
---

*Originally published on erikshosting.com. Archived here.*

---

Limit Login Attempts WPMU Friendly + Optimized!

I use wordpress mu(3.3.1) and I just spent some time reworking the ‘Limit Login Attempts’ Plugin (1.6.2) by Johan Eenfeldt to be more WordPress MS friendly. I will mention that this plugin works FANTASTICLY with wordpress MS 3.3.1 + …. Other Mu users may find this usefull… A couple things…

first, I set the variables at the top of the plugins .php file i wanted to be global. The file is very well noted by the author, OMG thank you! Very easy to control what variables the plugin activates with thanks to great coding and thoughtful notation.

Then I used the plugin manager to auto-activate the plugin for all users sitewide.. that way any newly generated blogs will automatically activate the plugin with the settings I want, and having moved the menu, users cant modify them.

INSTALL:

Network activate

That is all

The settings I changed to my liking were;

login attempts set to 4,

lockout log settings changed to ‘log, email’

notify email after 1 lockout

changed individual settings pages to only be visible to admin

emails sent network contact email (pretty sure this is already built in)
