---
title: "Magento 2 Photo Wall"
date: 2023-02-23
draft: false
tags: ["magento2", "adobe-commerce", "php"]
description: "A Magento 2 module for managing and displaying a photo wall on your storefront. Upload photos through the admin, set sort order, and publish them in a responsive grid at /photo-wall."
---

A Magento 2 module that gives you a clean admin interface to manage a collection of photos and display them in a responsive grid at `/photo-wall` on your storefront.

The module started as a personal need: a way to publish a wall of travel photos inside a Magento store without pulling in a third-party gallery service or embedding an iframe. Something that lives entirely in the platform, uses standard media storage, and lets you manage photos the same way you manage any other admin entity.

Each photo has a title, description, sort order, and an active toggle. The admin side is a standard Magento 2 UI component grid and form. Photos are stored in `pub/media/eraq/photowall/` and the upload field uses the native fileUploader component. The frontend outputs a CSS grid, two columns on mobile up to four on desktop.

Compatible with Magento 2.4.5 through 2.4.7 and PHP 8.1+.

## Source

[github.com/eraq/magento2-photo-wall](https://github.com/eraq/magento2-photo-wall)
