---
layout: post
title: Bash
categories:
  - Linux
---
* Extract "hel" character range from variable:  
`s1="hello world"`  
`echo ${s1:0:3}`  
* [Built-in variables (including the current function name)](http://tldp.org/LDP/abs/html/internalvariables.html)
* [Sort an array in bash](https://stackoverflow.com/questions/7442417/how-to-sort-an-array-in-bash)
* [Use process redirection (to log output to multiple places)](https://www.linuxjournal.com/content/shell-process-redirection):  
`# Process substitution is not a POSIX compliant feature and so it may have to be enabled`  
`# See https://www.linuxjournal.com/content/shell-process-redirection`  
`set +o posix`   
`exec > >(tee /tmp/test.log | logger -t user-data -s) 2>&1`  
`echo "Send to stderr. This will be logged to a file, syslog, and the screen $(date)" >&2`  
`echo "Send to stdout. This will be logged to a file, syslog, and the screen $(date)"`  
