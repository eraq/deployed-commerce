---
title: "Image Widget Alignment Fix"
date: 2011-10-03
draft: false
---

*Originally published on erikshosting.com. Archived here.*

---

So, I found that my wordpress Image Widget plugin by Shane and Peter inc, was having an issue aligning in my sidebar. I noticed that when I added multiple instances of the widget, they wouldn’t line up vertically. this naturally bugged the shit out of me, so I took a look at what was going on. Turns out the widget was actually closing a div that it hadn’t opened. Basically this update (3.2.8) is creating validation errors and prematuraly closing my themes sidebar div. So, I opened up the plugin files and took a look. I started with the /views/widget.php file that the readme mentions as being the output for the frontend widget display. Looking in the file I couldn’t see where the close div tag was. it looks like it is part of the $after_widget string thats generated elsewhere in the code. so rather than spend forever looking for it. I decided to simple OPEN a new div, right in front of the call to the string. That way, I could open the div and the string would close it. Check the frontend. VERTICAL ALIGNMENT ACHIEVED! check validation, NO ERRORS! wicked….. Here is my code for the /views/widget.php file..

Note the

```php
echo "<div>";
```

3rd to last line is what i added. You’ll see its right above the echo to the $after_widget string..

```php
<?php
echo $before_widget;
if ( !empty( $title ) ) { echo $before_title . $title . $after_title; }
if ( !empty( $image ) ) {
	if ( $link ) {
		echo '<a class="'.$this->widget_options['classname'].'-image-link" href="'.$link.'" target="'.$linktarget.'">';
	}
	if ( $imageurl ) {
		echo "<img src=\"{$imageurl}\" style=\"";
		if ( !empty( $width ) && is_numeric( $width ) ) {
			echo "max-width: {$width}px;";
		}
		if ( !empty( $height ) && is_numeric( $height ) ) {
			echo "max-height: {$height}px;";
		}
		echo "\"";
		if ( !empty( $align ) && $align != 'none' ) {
			echo " class=\"align{$align}\"";
		}
		if ( !empty( $alt ) ) {
			echo " alt=\"{$alt}\"";
		} else {
			echo " alt=\"{$title}\"";
		}
		echo " />";
	}

	if ( $link ) { echo '</a>'; }
}
if ( !empty( $description ) ) {
	$text = apply_filters( 'widget_text', $description );
	echo '<div class="'.$this->widget_options['classname'].'-description" >';
	echo wpautop( $text );
	echo "</div>";
}
echo "<div>";
echo $after_widget;
?>
```
