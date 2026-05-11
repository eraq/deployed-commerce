---
title: "Plugin Management Updated to be WP3 Compatible"
date: 2010-07-13
draft: false
tags: ["wordpress", "wpmu", "wp3", "plugin-management"]
description: "WP3 compatibility update to the WPMU Dev Plugin Management plugin, which allows network admins to control which plugins sub-blog admins can activate."
---

Plugin Management is far superior to Plugin Commander for WordPress MU and multi-site installs. The problem is, Plugin Management was not WordPress 3 compatible. Until this update.

## The Problem

I was working on a client site running WP3 with a plugin that allowed PHP to be accepted in text widgets. That is a significant security hole, and it should only be available to the super admin. With WP3 and Plugin Commander, you cannot disable it from the plugin menu. A sub-blog administrator can simply go to the plugins menu and activate the PHP widget plugin.

Plugin Management solves this by letting you control exactly which plugins sub-blog admins can enable. My users could activate Facebook Connect, NextGen Gallery, or Twitter Connect, but not PHP widget plugins or anything else I flagged as restricted. The WPMU team had not updated Plugin Management for WP3, so I did it myself.

The fix was straightforward. In WP3, `wpmu-admin.php` was replaced with `ms-admin.php`. A few minor corrections to the PHP and it works.

## Installation

Drop `mp-plugin-manager.php` into `/wp-content/mu-plugins/`.

**Requires WP3+.** Use the older version for anything below WordPress 3.0.

## Source

[github.com/eraq/wordpress-plugin-management](https://github.com/eraq/wordpress-plugin-management)
