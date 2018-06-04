---
layout:      post
title:       "Fix Unrecognised Bluetooth Adapter on Lubuntu 18.04"
category:    Posix
tags:        [Ubuntu, Bluetooth, DBus]
image:
  thumbnail: /images/bt.png
---

This is a *note to self* since the fix is so bizarre and hard to track down. I recently broke bluetooth badly on my Mac Mini which is running Lubuntu 18.04, and took several hours to fix.

Whilst playing with various bluetooth tools I managed to break bluetooth such that nothing bluetooth related worked any more. After lots of reinstalls of software, reboots, and reading random internet web posts on the subject still I had no joy.

Essentially it came down to this - running the command `hciconfig dev` returned a bluetooth adapter with a corrupt BT address of `00:00:00:00:00:00`.

# The Fix

Finally, in desperation, I ran the the command `sudo service dbus stop` which instantly crashed my computer.

However, once I rebooted the computer the bluetooth adapter was recognised as having a valid address, and has worked perfectly ever since.

Don't you just love computers!
