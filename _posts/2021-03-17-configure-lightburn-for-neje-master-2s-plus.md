---
id: 3753
title: 'Configure Lightburn for Neje Master 2S Plus'
date: '2021-03-17T14:33:00+00:00'
author: Andy
layout: post
guid: 'http://new.andydixon.com/?p=3753'
permalink: /configure-lightburn-for-neje-master-2s-plus/
trx_addons_post_views_count:
    - '0'
trx_addons_post_likes_count:
    - '0'
trx_addons_options:
    - 'a:1:{s:4:"icon";s:0:"";}'
gutentype_options:
    - 'a:0:{}'
categories:
    - Tech
---

I have a Neje Master 2S Plus laser engraver, and I use Linux, so I have got myself a license of Lightburn, and proceeded to set the device up. Note: The majority of the instructions also work for Windows too. As for a Mac? I really don’t care.

First important thing is to install the GRBL firmware on the device – for this download and follow the instructions [here](https://wiki.nejetool.com/doku.php?id=nejelaser_master_2_plus) (Neje Wiki)

Next, download the following two files:

- [Neje Master 2S Plus Device Settings.lbset](<https://www.andydixon.com/assets/Neje Master 2S Plus Device Settings.lbset>)
- [Neje Master 2S Plus.lbdev](<https://www.andydixon.com/assets/Neje Master 2S Plus.lbdev>)

When starting Lightburn, if you get the Devices box popup, click *Import* and import the *Neje Master 2S Plus.lbdev* file. If you don’t, click the *Devices* button near the bottom right of Lightburn and click *Import*

Once this is done, to improve performance, Select the *Edit* menu, and select *Machine Settings*. On the new window, click *Load* and select the *Neje Master 2S Plus Device Settings.lbset* and then click *Write*.

This will configure the Neje Master 2S Plus for use with Lightburn!

If using Linux, then make sure the user is allowed to use serial – depending on the distro, you will need to make your user a member of either *dialout* or *uucp* – you can do this simply enough with the following command: **sudo usermod -a -G \[groupname\] \[username\]**