---
title: "Chrome / Safari Specific Stylesheet CSS Hack and Classes"
date: 2010-08-20
draft: false
---

*Originally published on erikshosting.com. Archived here.*

---

So, I was working with the login-with-ajax wordpress plugin, When I noticed that it displays differently in chrome. I was blown away that firefox and internet explorer would both show the appropriate  css styling and that chrome should some entirely different placing of the div via css.

So what I needed was a way to have two different style classes for each browser set..

So I did some research and found that we can use the webkit difference of chrome and safari to firefox and IE. So, if you want a chrome/safari specific css style override just frame it in the below code, and drop it in below the old line# in your stylesheet.

```css
#div1 {old rules for:IE,Firefox;}

@media screen and (-webkit-min-device-pixel-ratio:0) {
	#div1 {new rules for:Chrome,Safari;}
}
```
