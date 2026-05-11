---
title: "Facebook Connect Login With Ajax WordPress Widget"
date: 2010-08-12
draft: false
tags: ["wordpress", "wpmu", "facebook", "ajax", "widget"]
description: "A merged widget combining Login With Ajax and Simple Facebook Connect, adding on-page error reporting and a Facebook login button without a page reload."
---

![Login With Ajax and Facebook Connect widget](/images/open-source/login-with-ajax-facebook-connect.jpg)

The Simple Facebook Connect plugin has a login widget, but it is limited. It lacks on-page error reporting, lost password functionality, and redirects users to `login.php` on failed attempts. In a multi-site environment, that redirect dumps users on the top-level blog login page, which completely breaks the feel of a sub-blog.

Login With Ajax handles those cases well: error messages appear inline, lost password is available without leaving the page, and there is no full reload on login. But it does not include the Facebook Connect button.

I edited the Login With Ajax plugin to also include the Simple Facebook Connect "connect with Facebook" button. The result combines the Ajax error handling and UX of Login With Ajax with the Facebook authentication of SFC.

## Requirements

Simple Facebook Connect for WordPress must be installed and configured before activating this plugin.

## Installation

1. Install and configure the Simple Facebook Connect WordPress plugin
2. Install the Login With Ajax and SFC plugin
3. Add the widget via the Widgets page, a shortcode in a page or post, or use the shortcode directly in a template file

## Source

[github.com/eraq/wordpress-facebook-connect-ajax-login](https://github.com/eraq/wordpress-facebook-connect-ajax-login)
