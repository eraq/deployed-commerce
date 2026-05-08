---
title: "Add GD Star Rating next to Post Title"
date: 2011-09-25
draft: false
---

So here is the steps I used to call the GD star rating for a post and display it where I wanted. In my case it was in the LI tags of a list of all posts in a category.

  You could use this to post the rating right up next to your post title with a little modification to your template.

So, What I did was I called a new wp_query and sorted it based upon the gd star rating. Then while inside the loop I used wp_gdsr_render_article where I wanted the rating to display.

  Next, I went and created a custom template for the GD article rating, and I removed all the tags and header information till I was just left with the %RATING% . Next I went back to my call to wp_gdsr_render_article, and I specified my custom template ID (in my case 46) number using the argument.

My code looked like this: wp_gdsr_render_article($template_id = 46, $read_only = false, $stars_set = “”, $stars_size = 0, $stars_set_ie6 = “”, $echo = true

hopes this helps!
