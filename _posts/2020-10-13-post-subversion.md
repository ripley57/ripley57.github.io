---
layout: post
title: Subversion
categories:
  - Tools
---
* [Transition to SSL](http://devwiki/wiki/Subversion_Secure_protocol)
* [List inherited svn properties (and their value)](http://svnbook.red-bean.com/en/1.8/svn.ref.svn.c.proplist.html):  
`svn proplist --show-inherited-props -v .`  
* [svn unencrypted password caching on Linux](http://help.collab.net/index.jsp?topic=/faq/cachepassword.html):  
Example file: `/home/hub/.subversion/auth/svn.simple/65b1be3cfa4a989d76fe9c3b14b925b2`  
* [Checkout a specific version of file (using Tortoise)](https://stackoverflow.com/questions/2812901/reverting-single-file-in-svn-to-a-particular-revision):  
1. Right click on your source file, and select "TortoiseSVN" -> "Show log".  
2. Right click on a revision in the log, and select "Save revision to...".  
3. Let the old revision overwrite your current file.  
4. Commit the overwritten source file.  
* checkout:  
`svn co http://nwb-svn/... --username=jc`  
`svn --non-interactive --trust-server-cert --no-auth-cache --username fred --password bert co ...`  
* commit: `svn commit --username jc -m"My change" scripts/compcob`  
Note: We don't seem to be using `svn propset svn:executable ON compcob`, which means executable permission is not preserved. See [here](https://stackoverflow.com/questions/5757293/proper-way-to-add-svnexecutable/5757365)  
* [Resolving conflicts](https://tortoisesvn.net/docs/release/TortoiseSVN_en/tsvn-dug-conflicts.html)  
**Note:** Using Tortoise "Resolve" does not commit anything. It should be enough to remove the "conflict" icon in Windows. 
