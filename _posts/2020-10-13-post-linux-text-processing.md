---
layout: post
title: Linux Text Processing
categories:
  - Linux
---
* **cut**:  
  * Display first x characters: `cut -c 1-35 <file>`
  * Cut the first x characters: `cut -c 1-35 --completement <file>`
* **grep**:  
  * Treat binary file as text file: `grep -a data fsstatus.log`
* **sed**:  
  * sed on a string (not a file) using a here string: `sed "s/,/','/g" <<< "A,B,C"`
