---
title: "Remove White Box On Frame Loading"
date: 2010-08-24
draft: false
---

*Originally published on erikshosting.com. Archived here.*

---

I know that if any of you have used iframes you’ll have noticed the white box that floats there so in-your-face, just taunting you with its uglyness as the rest of the page loads.

Why not take a screenshot of the page when it has fully loaded, crop the img down to just the contents of the fully loaded frame, and then use it as the background for a div container around the frame. an example would be:

```html
<div style="background: url('http://erikshosting.com/childframe/pre-load-screenshot.png');">
<iframe src="http://erikshosting.com/childframe/frame1.php" width="100%" height="211" frameborder="0" scrolling="no" overflow="hidden" name="erocks-global-nav-embed">
You Must Use A Browser Built This Century To See This Frame</iframe></div>
```
