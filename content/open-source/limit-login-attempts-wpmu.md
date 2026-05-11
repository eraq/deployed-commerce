---
title: "Limit Login Attempts WPMU Friendly + Optimized"
date: 2010-07-14
draft: false
tags: ["wordpress", "wpmu", "wp3", "security"]
description: "WordPress MU and multi-site compatible update to the Limit Login Attempts plugin (v1.6.2) by Johan Eenfeldt, with sitewide defaults and admin-only settings visibility."
---

I spent some time reworking the Limit Login Attempts plugin (v1.6.2) by Johan Eenfeldt to be more WordPress Multi-Site friendly. The original plugin works well on WP MS 3.3.1+, but needed a few adjustments to behave properly network-wide.

The author's code is exceptionally well documented, which made this straightforward. Variables at the top of the file are clearly noted, making it easy to set the defaults you want before network activation.

## What I Changed

The settings I adjusted for my installs:

- Login attempts reduced to 4
- Lockout log set to `log, email`
- Email notification after 1 lockout
- Individual settings pages visible to admins only
- Notification emails sent to the network contact address

I then used the Plugin Manager to auto-activate the plugin for all users sitewide. Any newly created blogs automatically get the plugin with these settings, and since the menu is restricted, users cannot modify them.

## Installation

Network activate. That is all.

## Source

[github.com/eraq/wordpress-limit-login-attempts-wpmu](https://github.com/eraq/wordpress-limit-login-attempts-wpmu)
