---
deleted: true
tags: [MySQL]
title: Untitled (4)
created: '2020-01-13T06:27:24.852Z'
modified: '2020-02-05T10:21:56.504Z'
---

# Untitled (4)


## Global And Session Updates

```sql

select @@session.SQL_SAFE_UPDATES

```

## Safe Update

* `UPDATE` and `DELETE` statements that do not use a key in the `WHERE` clause or a `LIMIT` clause produce an error
* restrictions are placed on `SELECT` statements that produce (or are estimated to produce) very large result sets

```sql

set sql_safe_updates = 0; # ignore safe update
set sql_safe_updates = 1; # safe update

```


## Primary Key

Uniquely identify each row;
Every table should have primary key Integer key preferred
not null and unique
