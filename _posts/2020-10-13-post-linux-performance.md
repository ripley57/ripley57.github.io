---
layout: post
title: Linux Performance
categories:
  - Linux
---
* **iftop**:
  Displays per-network-connection traffic every 2,10,40 seconds:  
  `iftop -n -N -P -i ens192 -f 'port 9223' -t -L 15`  
  (remove "-t" to see curses-style ui, "-L" is the number of results to display, "-P" is to show ports.)  
  Note: To see curses output property in putty, go to "Window > Translation" and tick "Enable VT100 line drawing even in UTF-8 mode".  
* [Load averages (e.g. top, uptime)](http://www.brendangregg.com/blog/2017-08-08/linux-load-averages.html)
* **pidstat**:
  * Installation: `yum install sysstat`
  * [thegeekstuff.com](https://www.thegeekstuff.com/2014/11/pidstat-examples/)
  * Example: 5 samples, one second between each, then give me an average:  
  `pidstat -C cassi -l 1 5`  
  `Average:      UID       PID    %usr %system  %guest   %wait    %CPU   CPU  Command`  
  `Average:     1001     27616    0.80    1.39    0.00    0.00    2.19     -  pidstat -C cassi -l 1 5`  
  `Average:     1001     31248    6.57    3.98    0.00    0.00   10.56     -  cassi32 /rTPCCDBFH -rTPCCDBFH`  
  `Average:     1001     31254    6.37    3.19    0.00    0.00    9.56     -  cassi32 /rTPCCDBFH -rTPCCDBFH`  
  `Average:     1001     31260    3.78    1.79    0.00    0.00    5.58     -  cassi32 /rTPCCDBFH -rTPCCDBFH`  
  `Average:     1001     31264    6.18    2.99    0.00    0.00    9.16     -  cassi32 /rTPCCDBFH -rTPCCDBFH`  
  `Average:     1001     31266   12.75    7.37    0.00    0.00   20.12     -  cassi32 /rTPCCDBFH -rTPCCDBFH`  
* **top:**
  * "top" in batch mode (i.e. can be redirected to a file) and include command-line args: `top -b -n 1 -c`
