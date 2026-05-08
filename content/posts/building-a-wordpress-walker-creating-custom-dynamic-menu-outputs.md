---
title: "Building a WordPress Walker – Creating Custom Dynamic Menu Outputs"
date: 2010-08-24
draft: false
---

*Code snippet for custom walker near bottom. Narrative near top*

I was recently working on a clients project where I needed to draw the primary nav of site#1 onto site #2-5, while retaining its ability to be edited via site#1's wp menu editor panel.

So what I did was put a php include onto each site that called a seperate php file that had my iframe code in it. This Iframe framed the primary nav menu of the first site, while the 2nd site called the frame file as an include, and the menu was available to the 2nd site as well…

Now for the next problem, the links on the menu were set with the 'target' attribute of '_self', meaning that when clicked, they took us to the link in the iframe and not in the full browser window showing the 2nd site. So the obvious solution would be to change the target attribute to '_top'.

Turns out that the wordpress Menus Control Panel, has an advanced screen option of 'link target' this allows you the options of 'current window' or 'new window', meaning '_self' and '_blank', respectively. The fact that '_parent' wasn't included as an option blew me away. So i added a ticket to the wordpress trac and slept on it.

Next day I see in the trac ticket, the begining of an argument about how frames are "too 1995″ and if the _parent or _top option was necessary for casual users…..

I'm not going to get into how much of an excuse this is for not fixing a glaring omission, but I'm also not going to wait around to see if i can finish my project.

### So, I modified the primary menus walker to output slightly different html.

I did this by defining a custom walker in my themes functions.php file, and then calling it as an $arg in my themes header.php where it called the wp_nav_menu function..

So to begin i grabbed wordpress's default walker code from line #67-92 of /wp-includes/nav-menu-template.php. Then I copied this into my themes functions.php file. I then surrounded this block of code in a class function and remembered to place the } after the block. You can see the default wordpress walker (with the target="_top" attribute added) and my custom function name surrounding it below. So drop the following code into your themes functions.php file

```php
class erockscustom_walker extends Walker_Nav_Menu
{
function start_el(&$output, $item, $depth, $args) {
global $wp_query;
$indent = ( $depth ) ? str_repeat( "\t", $depth ) : '';

$class_names = $value = '';

$classes = empty( $item->classes ) ? array() : (array) $item->classes;

$class_names = join( ' ', apply_filters( 'nav_menu_css_class', array_filter( $classes ), $item ) );
$class_names = '';

$output .= $indent . '<li id="menu-item-'. $item->ID . '"' . $value . $class_names .'>';

$attributes  = ! empty( $item->attr_title ) ? ' title="'  . esc_attr( $item->attr_title ) .'"' : '';
$attributes .= ! empty( $item->target )     ? ' target="' . esc_attr( $item->target     ) .'"' : '';
$attributes .= ! empty( $item->xfn )        ? ' rel="'    . esc_attr( $item->xfn        ) .'"' : '';
$attributes .= ! empty( $item->url )        ? ' href="'   . esc_attr( $item->url        ) .'"' : '';

$item_output = $args->before;
$item_output .= '<a target="_top"'. $attributes .'>';
$item_output .= $args->link_before . apply_filters( 'the_title', $item->title, $item->ID ) . $args->link_after;
$item_output .= '</a>';
$item_output .= $args->after;

$output .= apply_filters( 'walker_nav_menu_start_el', $item_output, $item, $depth, $args );
}
}
```

Then I dropped the argument into wp_nav_menu (where the wp3 custom menu is called in your themes header.php), like so:

```php
<?php $args=array('walker' => new erockscustom_walker()); wp_nav_menu($args); ?>
```

AND BAM! links open in the top window, and everything works as it should!
