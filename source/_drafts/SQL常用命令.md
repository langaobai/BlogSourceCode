title: SQL常用命令
author: LanGaoBai
author_id: defaultAuthorId
language: zh-CN
tags:
  - SQL
  - Common
categories:
  - SQL
date: 2018-03-12 13:57:00
---

#### 查询表相关

```sql
-- 根据表名称查询表
SELECT * FROM USER_TAB_COMMENTS WHERE TABLE_NAME LIKE '%TABLE_NAME%'

```
#### 查询字段相关

```sql
-- 根据表名称查询字段
SELECT * FROM USER_COL_COMMENTS WHERE TABLE_NAME = 'TABLE_NAME'
```

