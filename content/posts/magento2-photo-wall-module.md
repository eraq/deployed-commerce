---
title: "Magento 2 Photo Wall Module"
date: 2023-02-23
draft: false
---

I shipped a small Magento 2 module this week that I've been meaning to build for a while. It's called Photo Wall, and it does exactly what it sounds like: gives you a clean admin interface to manage a collection of photos, then displays them in a responsive grid at `/photo-wall` on your storefront.

The module is available at [github.com/eraq/magento2-photo-wall](https://github.com/eraq/magento2-photo-wall).

### Why

The personal motivation was straightforward. I wanted a low-friction way to publish a wall of travel photos inside a Magento store without pulling in a third-party gallery service or embedding an iframe. Something that lives entirely in the platform, uses the standard media storage, and lets me manage photos the same way I manage any other admin entity -- grid, edit form, upload, sort order.

The result is simple on purpose. Each photo has a title, a description, a sort order, and an active toggle. That's it. No albums, no tags, no lightbox JavaScript. Just photos in a grid.

### What it does

The admin side is a standard Magento 2 UI component grid and form. Photos live in their own database table (`eraq_photowall_photo`) and are stored in `pub/media/eraq/photowall/`. The upload field uses the native Magento fileUploader component, so it behaves consistently with product image uploads.

On the frontend, a controller at `photo-wall/index/index` renders a block that pulls all active photos ordered by sort order. The template outputs a CSS grid -- two columns on mobile, three on tablets, four on larger screens.

### Installation

```bash
composer require eraq/module-photo-wall
bin/magento module:enable Eraq_PhotoWall
bin/magento setup:upgrade
bin/magento setup:di:compile
bin/magento cache:flush
```

After that, **Content > Photo Wall > Manage Photos** is available in the admin. The frontend page appears at `/photo-wall`.

### A note on the use case

This module started as a travel photo wall, but it works just as well for anything you'd put on a physical corkboard -- team photos, product shots from events, seasonal imagery, a behind-the-scenes collage. The sort order field is there to give you control over the arrangement without needing to re-upload anything.

Compatible with Magento 2.4.5 and PHP 8.1.
