---
title: "Pro -Sites Shortcodes, Functions, And Level Checks"
date: 2012-03-22
draft: false
---

*Originally published on erikshosting.com. Archived here.*

---

Okay, we all remember is_supporter, but things aren’t that easy with pro -sites anymore… I have been reading all over the web people trying to get info on these. They want to do things like wrap a admin menu in a check so that if there not a premium user, the menu isnt shown. They want to display a custom nag to non-paid up users.. So after alot of googling and a jackpot in the code, Here are the functions and parameters. THanks to well documented code..

 

/**

* Check if a given site is Pro or at a given Pro level

*

* @since 3.0

*

* @param int $blog_id optional – The ID of the site to check. Defaults to current blog.

* @param int $level optional – Check if site is at this level or below. If ommited checks if at any level.

* @return bool

*/

function is_pro_site($blog_id = false, $level = false) {

global $psts;

return $psts->is_pro_site($blog_id, $level);

}

/**

* Check if a given user is a member of a Pro site (at any level)

*

* @since 3.0

*

* @param int $user_id optional – The ID of the user to check. Defaults to current user.

* @return bool

*/

function is_pro_user($user_id = false) {

global $psts;

return $psts->is_pro_user($user_id);

}

/**

* Check if a given site is in an active trial

*

* @since 3.0

*

* @param int $blog_id required – The ID of the site to check.

* @return bool

*/

function is_pro_trial($blog_id) {

global $psts;

return $psts->is_trial( $blog_id );

}

/*

* function psts_levels_select

* Print an html select field to choose level for an external plugin

*

* @param string $name Name of the form field

* @param int $selected the level number to select by default

*

* @return echo html select

*/

function psts_levels_select($name, $selected) {

global $psts;

$psts->levels_select($name, $selected);

}

//depreciated!

function is_supporter($blog_id = false) {

return is_pro_site( $blog_id, apply_filters( ‘psts_supporter_level’, false ) );

}

//depreciated!

function is_supporter_user($user_id = ”) {

return is_pro_user( $user_id );

}

//depreciated!

function supporter_feature_notice() {

global $psts;

$psts->feature_notice();

}

//depreciated!

function supporter_get_expire($blog_id = false) {

global $psts;

return $psts->get_expire($blog_id);

}
