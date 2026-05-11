---
title: "Snippet to Run ShortTags in Template"
date: 2010-08-15
draft: false
---

*Originally published on erikshosting.com. Archived here.*

---

## Want to use a WordPress plugins shorttag inside your template files?

### Use this nifty php snippet to call the shorttag properly!

So, I know that many of you use shorttags for plugins, simply drop the short-tag onto a post or page and voila! the plugin function is included.

Some times you just want to paste a plugins short-tag directly into your wordpress template files.. If you have tried this before you’ll notice that it simply outputs the shorttag, and nothing is included..

IF however, you want that plugin function to be called somewhere else, like in your template files themselves, then you must use a php snippet to call the shorttag.

So, Use this code to call short tags/ short codes in your themes template files:

```php
<?php echo do_shortcode("[your-shorttag]"); ?>
```

This will simply run the plugins shortag in your template files as if it was a real wordpress engine short code
