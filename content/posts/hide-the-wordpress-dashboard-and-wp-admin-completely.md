---
title: "Hide The WordPress Dashboard and wp-admin COMPLETELY!"
date: 2010-09-09
draft: false
---

*Originally published on erikshosting.com. Archived here.*

---

### WordPress 3 Compatible

I have seen several plugins that "hide" the dashboard from subscribers, but none that functions as I want.

I don't want it to allow only the tools, and profile page. I want it to straight kick the user out of the dashboard!

So, I wrote my own plugin that does that. If anyone that is not an admin (cannot activate plugins) attempts to access the dashboard via url or link, they are redirected to the front of the site. sorry, access denied..

Here is my code. Just drop this in your themes functions.php file and edit the url of the redirect to whatever you want.

```php
//hook onto dashboard and redirect all non admin to front site
add_action("admin_init","redirect_nonadmin_fromdash");

function redirect_nonadmin_fromdash(){
	if (!current_user_can('activate_plugins')) {
		// Edit Line Below For Your Own Redirect
		header( 'Location: http://www.erikshosting.com' ) ;
	}
}
```
