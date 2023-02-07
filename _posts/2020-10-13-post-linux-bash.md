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
* Bash arrays:  
`#!/usr/bin/bash`  
`declare -a HOSTS_ARRAY=('nwb-tpccrh76es1' 'nwb-tpccrh76es2' 'nwb-tpccrh76es3' 'nwb-mlora1' 'nwb-mlora2' 'nwb-mlora3');`  
`declare -a FILES_ARRAY=('lib/mfescache.jar');`  
`function update_files()`  
`{`  
`        local _host _file`    
``  
`        for _host in "${HOSTS_ARRAY[@]}" ; do`  
`                for _file in "${FILES_ARRAY[@]}" ; do`  
`                  echo "scp -p $_file hub@${_host}:/home1/hub/pkg-es/$_file"`  
`                  scp -p $_file hub@${_host}:/home1/hub/pkg-es/$_file`  
`               done`  
`        done`  
`}`  
`update_files`  
