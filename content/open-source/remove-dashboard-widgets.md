---
title: "Remove All WordPress Dashboard Widgets Sitewide (WPMU 2.9+ and WP3)"
date: 2010-07-15
draft: false
tags: ["wordpress", "wpmu", "wp3", "dashboard"]
description: "Drop-in mu-plugin that removes all default WordPress dashboard widgets across an entire multi-site network on creation, compatible with WPMU 2.9+ and WP3."
---

Are you trying to customize the WordPress dashboard across all sites on a WPMU or WP3 multi-site network?

Most plugin solutions for this operate on a per-blog basis, which means you have to configure each site manually. Most code snippet solutions are outdated, and many get things like the Recent Drafts widget wrong. Recent Drafts is a "side" meta box, not a normal one, and a lot of scripts miss it entirely, so it persists even after everything else is removed.

White Label CMS looked promising but requires per-site configuration, which is a deal breaker on a large network.

The Incsub remove dashboard widgets plugin was the closest, but it does not remove all widgets. I updated it to catch everything, and made it compatible with both WP 2.9 and WP3.

Drop it in `/wp-content/mu-plugins/` and every new blog created on the network comes up with a clean dashboard, no configuration needed per site.

## Why You Might Want This

Combined with the New Blog Defaults plugin, Admin Menu Editor, and Dashboard CMS, you get a completely configured backend for your clients on deployment, without touching each site individually.

## Installation

Drop the plugin file into `/wp-content/mu-plugins/`. It auto-activates network-wide.

## Source

[github.com/eraq/wordpress-remove-dashboard-widgets](https://github.com/eraq/wordpress-remove-dashboard-widgets)
