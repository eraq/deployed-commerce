---
title: "Analytics 360 For Editors"
date: 2011-10-21
draft: false
---

*Originally published on erikshosting.com. Archived here.*

---

I wanted Analytics360 to be visible to the editors of a particular website. I found the appropriate threat on the net that explained it, and set about doing it. But then I noticed that the code had changed a bit since the last post, thusly making the workaround display the api settings page to editors (no good!).  So, what I did, was change all instances of ‘manage_options’ to ‘moderate_comments’, inside analytics360.php but then I duplicated the function that created the menu, and put it and the original behind an IF/ELSE statement and removed the creation of the settings page in the appropriate place, and voila. settings page for admin, analytics page for admin and editors!..

The code to replace is the a360_admin_menu function in analytics360.php starting at line #635.. Replace that function with this modified function

```php
function a360_admin_menu() {
	if (current_user_can('manage_options')) {
		add_options_page(
			__('Settings', 'analytics360'),
			__('Analytics360°', 'analytics360'),
			'manage_options',
			basename(__FILE__),
			'a360_settings_form'
		);
		add_dashboard_page(
			__('Dashboard', 'analytics360'),
			__('Analytics360°', 'analytics360'),
			'manage_options',
			basename(__FILE__),
			'a360_dashboard'
		);
	} else {
	if (current_user_can('publish_posts')) {
		add_options_page(
			__('Analytics360°', 'analytics360'),
			'publish_posts',
			basename(__FILE__),
			'a360_settings_form'
		);
		add_dashboard_page(
			__('Dashboard', 'analytics360'),
			__('Analytics360°', 'analytics360'),
			'publish_posts',
			basename(__FILE__),
			'a360_dashboard'
		);
	}
	}
}
```
