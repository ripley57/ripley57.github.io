---
layout: post
title: Linux Screen
categories:
  - Linux
---
* Basic usage example:  
```
screen -S my-session bash
ctrl+a d
screen -ls
screen -r my-session
```
* [How to use Linux Screen](https://linuxize.com/post/how-to-use-linux-screen/)
* [Manual (gnu.org)](https://www.gnu.org/software/screen/manual/html_node/index.html#SEC_Contents)
* Name session: `screen -S session_name`
* Name session using a screenfile: `screen -S sentinel-demo -c ~/scripts/screenfile-sentinel-demo`
* Rename the screen session (the name listed by "screen -ls"): `Ctrl+a then type :sessionname MyNewSessionName`  
* Re-name a screen window's title: Hit Enter to open that window, and then `ctl+a + shift+a`  
* Detach: `Ctrl+a` then `d`
* List sessions: `screen -ls`
* Re-attach to session: `screen -r <name> or <pid>`



