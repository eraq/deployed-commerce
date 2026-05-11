---
title: "Adding Custom Menus, Links, Drop Downs,  & Flyouts To The Buddypress Bar"
date: 2012-03-19
draft: false
---

*Originally published on erikshosting.com. Archived here.*

---

It is entirely possible to add your own links to the buddypress bar without modifying core files. It is also possible to add your own drop down menus complete with flyout menus. Let me show you how..

### First, lets tackle adding a simple link to the buddypress admin bar.

What I'm going to do is tap into the buddypress admin bar and add a link using a php file placed in the '/wp-content/plugins/' folder and activated via the plugins menu. Create a file in your /plugins/ dir and name it erocks-admin-bar-mods.php then drop the following code into it. After this, go to your plugins page, and activate the BP Nav Bar Mods Plugin.

Lets create that simple link!

```php
<?php
/*
Plugin Name: BP Nav Bar Mods - Add Link
Plugin URI: http://erikshosting.com
Description: Add A Simple Link To The Buddypress Admin Bar
Author: Erock
Version: 1.0
Author URI: http://erikshosting.com
*/

//Links and Menus Added To The Following Function Are Always Visible On The BP Bar
function bp_adminbar_currentsite_menu() {
	global $bp;
	?>

	<li>
		<!-- Insert your link url or relative url, and your link text below -->
		<a href="http://EXAMPLE.COM">EXAMPLE LINK TEXT</a>
	</li>

<?php
}

// Call The Function Above
add_action('bp_adminbar_menus', 'bp_adminbar_currentsite_menu', 999);

?>
```

### Now Lets Add Multiple Links To The Buddypress Bar..

Pay Special Attention to Enclosing The Href In &lt;li&gt; Tags Each Time.

```php
<?php
/*
Plugin Name: BP Nav Bar Mods - Add Multiple Links
Plugin URI: http://erikshosting.com
Description: Add Multiple Links To The Buddypress Admin Bar
Author: Erock
Version: 1.0
Author URI: http://erikshosting.com
*/

//Links and Menus Added To The Following Function Are Always Visible On The BP Bar
function bp_adminbar_currentsite_menu() {
	global $bp;
	?>

	<li>
		<!-- Insert your 1st link url or relative url, and your link text below -->
		<a href="http://EXAMPLE1.COM">EXAMPLE LINK TEXT1</a>
	</li>
	<li>
		<!-- Insert your 2nd link url or relative url, and your link text below -->
		<a href="http://EXAMPLE2.COM">EXAMPLE LINK TEXT2</a>
	</li>
	<li>
		<!-- Insert your 3rd link url or relative url, and your link text below -->
		<a href="http://EXAMPLE3.COM">EXAMPLE LINK TEXT3</a>
	</li>

<?php
}

//Call The Function Above
add_action('bp_adminbar_menus', 'bp_adminbar_currentsite_menu', 999);

?>
```

So you see its easy to add multiple links, you just have to repeat the format..

### Next Lets Add A Drop Down Menu To The Buddypress Bar

All we gotta do is make use of a &lt;ul&gt; tag inside of your parent items &lt;li&gt; tag. Just like this..

```php
<?php
/*
Plugin Name: BP Nav Bar Mods - Add Drop Down Menu
Plugin URI: http://erikshosting.com
Description: Add A Drop Down Menu To The Buddypress Admin Bar
Author: Erock
Version: 1.0
Author URI: http://erikshosting.com
*/

//Links and Menus Added To The Following Function Are Always Visible On The BP Bar
function bp_adminbar_currentsite_menu() {
	global $bp;
	?>

	<li>
		<!-- Insert your parent link url or relative url, and your link text below -->
		<a href="http://EXAMPLE1.COM">TOP PARENT MENU LINK TEXT</a>

		<!-- Start The Drop Down Menu By Not Closing The LI Tag From The Item Above, & By Starting A UL Tag Below -->
		<ul>
			<li>
				<!-- Insert your 1st dropdown menu sub item link url or relative url, and your link text below -->
				<a href="http://EXAMPLE2.COM">EXAMPLE LINK TEXT2</a>
			</li>
			<li>
				<!-- Insert your 2nd dropdown menu sub item link url or relative url, and your link text below -->
				<a href="http://EXAMPLE3.COM">EXAMPLE LINK TEXT3</a>
			</li>
			<!-- Below Ends The Drop Down Menu By Closing The UL and LI Tags -->
		</ul>
	</li>

<?php
}

//Call The Function Above
add_action('bp_adminbar_menus', 'bp_adminbar_currentsite_menu', 999);

?>
```

Pretty Easy.

### What About Flyout Menus? You Know, Sub-Sub-Menus?

No Problem, thats just more easy work with the &lt;li&gt; and &lt;ul&gt; tags.. We just repeat what we did above, but go another level with the &lt;ul&gt; and &lt;li&gt; tags. Watch..

```php
<?php
/*
Plugin Name: BP Nav Bar Mods - Add Drop Down With Flyout
Plugin URI: http://erikshosting.com
Description: Add Drop Down With Flyout Menu To The Buddypress Admin Bar
Author: Erock
Version: 1.0
Author URI: http://erikshosting.com
*/

//Links and Menus Added To The Following Function Are Always Visible On The BP Bar
function bp_adminbar_currentsite_menu() {
	global $bp;
	?>

	<li>
		<!-- Insert your parent link url or relative url, and your link text below -->
		<a href="http://EXAMPLE.COM">TOP PARENT MENU LINK TEXT</a>

		<!-- Start The Drop Down Menu By Not Closing The LI Tag From The Item Above, & By Starting A UL Tag Below -->
		<ul>
			<li>
				<!-- Insert your 1st dropdown menu sub item link url or relative url, and your link text below -->
				<a href="http://EXAMPLE.COM">EXAMPLE LINK TEXT</a>
			</li>
			<li>
				<!-- Start The Flyout Menu Off The Item Below -->
				<a href="http://EXAMPLE.COM">EXAMPLE LINK TEXT</a>

				<!-- Instead of Closing the LI tag, Start a UL tag To Create The Flyout Menu -->
				<ul>
					<li>
						<!-- Insert your 1st flyout menu sub-sub item link url or relative url, and your link text below -->
						<a href="http://EXAMPLE.COM">EXAMPLE LINK TEXT</a>
					</li>
					<li>
						<!-- Insert your 2nd flyout menu sub-sub item link url or relative url, and your link text below -->
						<a href="http://EXAMPLE.COM">EXAMPLE LINK TEXT</a>
					</li>
					<!-- Below Ends The Flyout Menu By Closing The UL And LI Tags -->
				</ul>
			</li>
			<!-- Go Back To The Drop Down Menu And Add Another Item -->
			<li>
				<a href="http://EXAMPLE4.COM">EXAMPLE LINK TEXT4</a>
			</li>
			<!-- Below Ends The Drop Down Menu By Closing The UL and LI Tags -->
		</ul>
	</li>

<?php
}

//Call The Function Above
add_action('bp_adminbar_menus', 'bp_adminbar_currentsite_menu', 999);

?>
```

Real easy. You can add multiple flyout menus, just continue repeat the format.
