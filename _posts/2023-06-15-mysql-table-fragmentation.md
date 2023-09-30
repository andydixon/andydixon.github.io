---
id: 4014
title: 'MySQL Table Fragmentation'
date: '2023-06-15T09:59:49+01:00'
author: Andy
layout: post
guid: 'https://www.andydixon.com/?p=4014'
permalink: /mysql-table-fragmentation/
categories:
    - Tech
---

The following SQL will give you an understanding on how fragmented tables are on a MySQL server

```
<pre class="wp-block-code">```
SELECT CONCAT(TABLE_SCHEMA,'.',TABLE_NAME) AS tableName,Round( DATA_LENGTH/1024/1024) + round(INDEX_LENGTH/1024/1024) as dataSize, round(DATA_FREE/ 1024/1024) as wastedSpace,round(DATA_FREE/ 1024/1024)/(Round( DATA_LENGTH/1024/1024) + round(INDEX_LENGTH/1024/1024)) AS fragmentationRatio from information_schema.tables  where  DATA_FREE > 0 HAVING fragmentationRatio >0.01 OR fragmentationRatio IS NULL;
```
```