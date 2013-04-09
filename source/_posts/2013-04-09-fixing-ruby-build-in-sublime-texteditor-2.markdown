---
layout: post
title: "Fixing Ruby build in Sublime Text 2"
date: 2013-04-09 14:35
comments: true
categories:
  - ruby
  - sublime
---

If youre getting this error while trying to run ruby script, just replace the loop in *Packages/Default/exec.py* on line 44 with the snippet below:

<pre>UnicodeDecodeError: 'ascii' codec can't decode byte 0xe2 in position 60 ...</pre>


``` python Packages/Default/exec.py:44
for k, v in proc_env.iteritems():
  path_vars = os.path.expandvars(v)
  if isinstance(path_vars, unicode):
      path_vars = path_vars.encode(sys.getfilesystemencoding())
  proc_env[k] = path_vars
```
