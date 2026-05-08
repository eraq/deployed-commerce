---
title: "Blogs & Members Directory, Strange Nav Spacing FIX"
date: 2010-09-06
draft: false
---

So I installed the wpmu dev teams blogs directory and their members directory plugins on the wpmu triden theme. I noticed that when I clicked on the link and went to one of the directory pages, the page spacing in the navbar got way big. I figured their was some spacing issue coming from the plugin, but it turns out its a little different than that. Looks like the ‘current_page_item’ was generating an empty href link before the actual link. So their were two links per <li> tag for the members directory page nav link when on that page. same with the blogs directory. Also, when you remove this filter, you stop the plugin from renaming the page, so you can edit the title of the page in the wp editor, and have the on page title actually reflect that, rather than letting the plugin rename the page ‘blogs’ or ‘members’.

### So how do you fix it?

Open up the blogs directory plugins php file, and find and remove the following line:

```php
add_filter(‘the_title’, ‘blogs_directory_title_output’, 99, 2);
```

Now in the Members Directory, Find and remove this line:

```php
add_filter(‘the_title’, ‘members_directory_title_output’, 99, 2);
```
