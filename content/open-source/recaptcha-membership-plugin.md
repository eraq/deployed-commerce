---
title: "Add reCaptcha to the WPMU Dev Groups Membership Plugin"
date: 2012-12-01
draft: false
tags: ["wordpress", "wpmu", "recaptcha", "security", "membership"]
description: "A plugin that adds reCaptcha to the registration page of the WPMU Dev Groups Membership Plugin, with network-wide configuration options and CSS controls."
---

![reCaptcha on the Membership Plugin registration page](/images/open-source/recaptcha-membership-plugin.jpg)

Adds a reCaptcha field to the registration page of the WPMU Dev Groups Membership Plugin. Built for multi-site, with options for both network-wide configuration and single-site deployment.

Includes CSS controls to fit the captcha into the registration form without custom coding, plus a set of action hooks and variables for developers who need to extend the behavior.

**Requires** the WPMU Dev Groups [Membership Plugin](https://premium.wpmudev.org/project/membership/).

## Installation

1. Add the zip to your plugin uploader, or extract to your plugins folder and upload
2. Activate the plugin
3. Configure your reCaptcha API keys at **Settings > Membership Captcha** in the WordPress dashboard

## Changelog

**1.7** - Current release

**1.6** - Added legacy support for older versions of Membership (thanks Indrek)

**1.5** - Multi-site fixes

**1.4** - Added network-wide override settings for network admins to set API keys and configuration across the entire network. Added action hooks.

**1.3** - Settings for controlling whether the plugin adds its default CSS

**1.2** - Minor fixes

**1.1** - Language filter support

**1.0** - Launch

## Source

[github.com/eraq/wordpress-recaptcha-wpmu-groups](https://github.com/eraq/wordpress-recaptcha-wpmu-groups)
