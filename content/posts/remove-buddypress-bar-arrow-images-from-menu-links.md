---
title: "Remove Buddypress Bar Arrow Images From Menu Links"
date: 2010-09-05
draft: false
---

### Now, How About We Remove The Arrow Images From Our Non- Drop Down Menu Items

All you have to do is override the <li> tags background css attribute. It’s easy, watch..

```html
<li style=”background:none;”>
	<!-- Insert your link url or relative url, and your link text below -->
	<a href=”http://EXAMPLE.COM”>EXAMPLE LINK TEXT</a>
</li>
```

& Bam, those drop down arrows are gone from the link.
