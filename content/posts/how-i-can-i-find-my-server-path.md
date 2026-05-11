---
title: "How I Can I find My Server Path?"
date: 2010-08-23
draft: false
---

*Originally published on erikshosting.com. Archived here.*

---

### Sometimes it is difficult to locate your server path.

Drop this string into a .php file called ‘locate-path’ or something, and then navigate to it in a browser to see your full server path!

```php
<p><?php echo $_SERVER['PATH_TRANSLATED'];?></p>
```
