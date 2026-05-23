---
title: "Adobe Commerce Zero Downtime Deployments. The Good, The Bad, and The Data Patch"
date: 2026-05-02
draft: false
tags: ["adobe-commerce", "magento2", "devops", "deployment"]
image: zero-downtime-banner.webp
description: "Zero downtime deployments in Adobe Commerce are a genuine overhead when you're shipping features with data patches, but for day-to-day frontend work they're nearly invisible and really good."
---

<figure>
  <img src="yabadee-yabadoo.webp" alt="Blue Man Group">
  <figcaption><s>blue green</s> zero downtime deployments</figcaption>
</figure>

So if you're on Adobe Commerce Cloud, you have zero downtime deployments available to you, but there's a right way to set them up.

The way it works is you move static content generation into the build phase rather than the deploy phase. That's the key. When SCD runs during build, the deploy phase becomes short enough that Adobe can hold active connections in a queue, up to five minutes, and release them when the deployment completes. Sessions stay intact, carts don't drop, and the store never goes dark. No maintenance window, no putting the site offline and hoping nobody notices.

For the projects where everything is built to handle this that's great, but in reality it's going to be a PIA.

### The problem

Here's the deal with data patches.

Your deploy hooks run in order, build, then deploy (setup:upgrade, data patches, the whole thing), then post-deploy. So there's a gap where your new code is live but your database is still sitting at the old schema. If you wrote a feature that reads a new column and you didn't write a fallback for the state before the patch runs, you're going to get errors. Possibly in production.

So you end up writing code that checks whether a column or table exists before it queries it. Making sure your data patches are idempotent. Testing what happens when the patch hasn't run yet, not just when it has. And if the patch itself throws an exception halfway through, setup:upgrade bails and you're in rollback territory.

It's extra work on every feature ticket that touches the database. And it's not just your code, every third party module on the project has to handle this too, and so does that legacy spaghetti codebase you've just been handed and asked to maintain. It's going to bite you.

### Where it actually earns its keep

Frontend deploys. That's where zero downtime is genuinely great.

CSS changes, LESS updates, template work, layout adjustments, responsive fixes, pixel-pushing from designer mockups, none of that touches the database. Build it, deploy it, connections queue and release, done. No maintenance mode, no customers hitting a broken page mid-deploy.

Most of the week-to-week deploy volume on a mature commerce site is this stuff anyway. The client wants the hero image taller. The designer sent new mockups. The PDP layout needs a second look on mobile. All of that goes through cleanly and you don't have to think about it.

You can ship a CSS fix in the afternoon, look at it on the live site, and push a follow-up before end of day. That cadence is actually useful when you're working directly off design reviews.

### So

Not going to pretend zero downtime deployments have no overhead, they do, and if you're shipping database-touching features every sprint you're going to feel it. Go in knowing that defensive code around your schema changes is part of the deal, and make sure your patches are bulletproof before they go anywhere near production.

For frontend work though, it's a significant upgrade over the old approach. Ships clean, stays up, nobody panics. Maybe they'll even let me run deployments during business hours now?
