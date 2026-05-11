---
title: "*FIX* Iframes In Chrome And Safari Ignore Scrolling=no / Scrolling:no;"
date: 2010-08-31
draft: false
---

*Originally published on erikshosting.com. Archived here.*

---

### So I noticed that when embedding an Iframe, Google Chrome (and Safari) failed to respond to scrolling=no.

I went to look and see if this syntax was deprecated, but its not.

Basically webkit (safari and chrome are based on them) values css styles on the html, body, and others, higher than the actual iframe style itself.

what that means is that if their is an ‘overflow’ attribute as anything other than ‘hidden’ in your applicable css, and you place scrolling=no onto an iframe style or place it in the html itself, chrome and safari will show scroll bars. firefox and IE will not. WTF?

### What can you do..

Well you can place the iframe inside a div, call larger than width and heights to eleminate the ‘auto’ scroll bars in chrome and safari, then use a div outside of it with a set height and width as well as overflow=hidden to trim the iframe.

### The Cause…

There is an attribute inside your css that calls overflow: scroll, or overflow: auto, or overflow-x: scroll, or overflow-y: scroll, or auto or whatever… If you are lucky enough to be able to pull this css style attribute out, it will fix your problem…
