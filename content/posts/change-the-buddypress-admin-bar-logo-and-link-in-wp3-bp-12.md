---
title: "Change The Buddypress Admin Bar Logo And Link In WP3 & BP 1.2+!"
date: 2010-09-12
draft: false
---

*Originally published on erikshosting.com. Archived here.*

---

### Wanna change the buddypress logo/text in the top left corner?

### Wanna change the link of the logo/text of the Buddypress admin bar?

I’ve seen a few tutorials on how to do this, but they are all outdated with the old version of buddypress. Some changes in the latest release, necessitate a new solution.. Here it is!

Create a php file inside /mu-plugins/ named ‘erocks-buddypress-logo-mod.php’. Drop in the code below, don’t forget to edit in your variables!

```php
// CHANGE BP ADMIN BAR LOGO
function erocks_bp_adminbar_logo() {
	global $bp;
	echo ‘<a href=”’ . $bp->root_domain . ‘”><img id=”admin-bar-logo” src=”http://EXAMPLE.LOGO.URL.PNG” alt=”Eriks Hosting | Solutions For An Online World” /></a>’;
}
remove_action( ‘bp_adminbar_logo’, ‘bp_adminbar_logo’ );
add_action( ‘bp_adminbar_logo’, ‘erocks_bp_adminbar_logo’ );
```

Just drop in your img src, your alt tag. remember to keep your img the same size as the original, or you will have to hardcode the new img sizes in the admin header file.

If you want to change the link the logo takes you to onclick, edit the <a href=”‘ .$bp->root_domain . ‘”> to whatever you want..
