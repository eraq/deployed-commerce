---
title: "Buddypress Avatar Upload Failed – FIX"
date: 2010-09-11
draft: false
---

So I found an error on a clients server. They were getting the “Upload Failed! Cannot Create Folder” “Is Parent Directory Writeable”.

And yes the folder was writeable. It was the /blogs.dir/1/files folder. of course I checked it and saw it had the appropriate 775 permissions. So I searched the forums and then contacted their servers customer support.

Turns out the folder AND ALL SUBFOLDERS RECURSIVELY were not ‘owned’ by anyone. (WTF?) This ment that even though 775 permission allowed the owner to write, the server was not the owner…..

What needed to happen was the blogs.dir/ dir and all its subfolders had to be modded by customer support at the hosting company to be owned by ‘apache’. Now that the server was the owner, the server could write to the files.

*Note on non-apache machines, the owner should the name of the main ftp user

Sometimes I wonder why people pick the Hosts that they do. I geuss it comes down to money… My advice, buck up and spend a few dollars on a good server.
