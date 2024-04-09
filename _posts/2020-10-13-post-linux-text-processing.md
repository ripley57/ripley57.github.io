---
layout: post
title: Linux Text Processing
categories:
  - Linux
---
* **awk**:
  * Remove some columns: `awk '{$6=$8=""; print $0}' file`  
* **cut**:  
  * Display first x characters: `cut -c 1-35 <file>`
  * Cut the first x characters: `cut -c 1-35 --completement <file>`
* **grep**:  
  * Treat binary file as text file: `grep -a data fsstatus.log`
* **sed**:  
  * sed on a string (not a file) using a here string: `sed "s/,/','/g" <<< "A,B,C"`
* **sort**
  * Sort numeric column 3 in CSV file: `sort -t ',' -n -k 3,3 data.csv`  
