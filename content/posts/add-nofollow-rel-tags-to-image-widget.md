---
title: "Add nofollow rel tags to image widget"
date: 2011-10-03
draft: false
---

*Originally published on erikshosting.com. Archived here.*

---

So, to modify the href tag for the image widget plugin output. just open up /views/widget.php and add rel=”nofollow” inside the echo string on the 6th line. Here is a copy of my code

```php
<?php
echo $before_widget;
if ( !empty( $title ) ) { echo $before_title . $title . $after_title; }
if ( !empty( $image ) ) {
	if ( $link ) {
		echo '<a rel="nofollow" class="'.$this->widget_options['classname'].'-image-link" href="'.$link.'" target="'.$linktarget.'">';
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
