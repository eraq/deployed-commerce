---
title: "Add All Pages To Buddypress Admin Bar Dynamically"
date: 2010-09-06
draft: false
---

### Want to add all your pages into your buddypress admin bar automatically?

It’s easy as pie! Just add wp_list_pages to your buddypress bar with the following code!

Create a file called erocks-admin-bar-mod.php in your /plugins/ dir, put in the following code, then activate the BP Nav Bar Mods Plugin on the plugin control panel

```php
<?php
/*
Plugin Name: BP Nav Bar Mods - Add All Pages
Plugin URI: http://erikshosting.com
Description: Add All Your Pages To The Buddypress Admin Bar Automatically!
Author: Erock
Version: 1.0
Author URI: http://erikshosting.com
*/

//Links and Menus Added To The Following Function Are Always Visible On The BP Bar
function bp_adminbar_currentsite_menu() {
	global $bp;
	?>

<!-- Call All Pages Via A WordPress Shortcode! -->
<?php wp_list_pages('title_li='); ?>

<?php
}

// Call The Function Above
add_action('bp_adminbar_menus', 'bp_adminbar_currentsite_menu', 999);

?>
```

### Or How About As A Drop Down Menu?

```php
<?php
/*
Plugin Name: BP Nav Bar Mods - Add All Pages
Plugin URI: http://erikshosting.com
Description: Add All Your Pages To The Buddypress Admin Bar Automatically!
Author: Erock
Version: 1.0
Author URI: http://erikshosting.com
*/

//Links and Menus Added To The Following Function Are Always Visible On The BP Bar
function bp_adminbar_currentsite_menu() {
	global $bp;
	?>

<!-- Call All Pages Via A WordPress Shortcode As A Drop Down! -->
<li><a href="#">Pages</a>
<ul>
<?php wp_list_pages('title_li='); ?>
</ul>
</li>

<?php
}

// Call The Function Above
add_action('bp_adminbar_menus', 'bp_adminbar_currentsite_menu', 999);

?>
```
