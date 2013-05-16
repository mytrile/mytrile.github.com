---
layout: post
title: "Integer types in Rails"
date: 2013-05-16 10:41
comments: true
categories:
  - rails
  - db
---

By default Rails will create INT(11) for integer type without limit. If you want to use different integer type like BIGINT you should use :limit.

```
+------------------------------------------------------------+
| :limit | Numeric Type  | Column Size |      Max Value      |
|--------+---------------+-------------+---------------------|
|    1   |    TINYINT    |   1 byte    | 127                 |
|    2   |    SMALLINT   |   2 bytes   | 32767               |
|    3   |    MEDIUMINT  |   3 bytes   | 8388607             |
|    4   |     INT(11)   |   4 bytes   | 2147483647          |
|    8   |     BIGINT    |   8 bytes   | 9223372036854775807 |
+------------------------------------------------------------+
```

Example in a migration file:

``` ruby
add_column :users, :amount, :integer, limit: 8 # BIGINT
```

<blockquote>Notice: If you don't supply limit it defaults to 4 => INT(11). If your limit is 5..8 it will be BIGINT<blockquote>
