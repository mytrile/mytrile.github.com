---
layout: post
title: "Get HOME directory"
date: 2013-04-13 11:45
comments: true
categories:
  - ruby
---

``` ruby
require 'etc'

login = Etc.getlogin

config_file = File.join(Dir.home(user), ".zshrc")
```
