---
title: "Dashboard CMS Updated for WP2.9+, WPMU2.9+, and WP3"
date: 2010-07-15
draft: false
tags: ["wordpress", "wpmu", "wp3", "dashboard"]
description: "WP3 compatibility update to the Dashboard CMS plugin, merged with user privilege checks from a WP3-native version to produce a single build compatible with WP2.9+ through WP3."
---

Dashboard CMS is a plugin that replaces the default WordPress dashboard with large, easy buttons, making the admin area much more approachable for clients. I have it auto-activated on my WPMU 2.9 sites and network-activated on my WP3 installs.

The problem is it was not WP3 compatible. I found a WP3 version that added user privilege checks before showing each button, but it dropped backward compatibility with legacy installs. I merged the two files together using `get_version()` to determine which code path to execute.

The result handles WP2.9+, WPMU2.9, and WordPress 3, and checks user permission level before displaying each button.

## Source

[github.com/eraq/wordpress-dashboard-cms](https://github.com/eraq/wordpress-dashboard-cms)
