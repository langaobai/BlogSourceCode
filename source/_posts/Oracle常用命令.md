title: Oracle常用命令
author: LanGaoBai
author_id: defaultAuthorId
language: zh-CN
tags:
  - Oracle
  - note
categories:
  - Oracle
date: 2018-03-09 16:02:00
---
### Oracle表空间创建

1. 创建临时表空间
```sql
create temporary tablespace YNMZCK_TEMP  
tempfile 'D:\Install_file\app\Administrator\oradata\orcl\YNMZCK_TEMP.dbf' 
size 50m  
autoextend on  
next 50m maxsize 20480m  
extent management local;
```
2. 创建数据表空间
```sql
create tablespace YNMZCK  
logging  
datafile 'D:\Install_file\app\Administrator\oradata\orcl\YNMZCK.dbf' 
size 50m  
autoextend on  
next 50m maxsize 20480m  
extent management local;
```
3. 创建用户并指定表空间
```sql
create user YNMZCK identified by YNMZCK
default tablespace YNMZCK  
temporary tablespace YNMZCK_TEMP;
```

4. 给用户授予权限
```sql
grant connect,resource,dba to YNMZCK;
```

### Oracle导入/导出dmp

1. 导出命令
```bash
exp YNMZCC/YNMZCC@orcl  file=d:\ynmzcc.dmp owner = YNMZCC
```

2. 导入命令
```bash
imp username/password@SID file=XXX.dmp fromuser=XXX touser=XXX tables=(XXX,XXX)
```

### Oracle清空或者删除当前用户下所有的表

1. 使用客户端

```bash
使用pl/sql客户端，使用该用户登录，选中所有表 右键drop即可
```

2. 动态生成删除命令（**要求用户有相应权限**）

```sql
select 'drop table '||table_name||';' from user_tables;  
```

3. 使用存储过程删除该用户下所有表

```sql
set ECHO ON  
set define off       
SPOOL logs/create_procedure.log  
  
--删除所有表的存储过程;    
create or replace procedure P_DROP_ALL_TABLE  
as   
  --引用user_tables表中的tableName的类型;  
  tableName user_tables.table_name%type;    
  type ty is record(table_name varchar2(30));  
  --定义ref类型游标;-强类型  
  type ref_type is ref cursor return ty;  
  ref_t ref_type;  
  --定义变量存储数量;  
  mycount number(10);  
  begin  
    --打开游标;  
    open ref_t for select table_name from user_tables;  
         loop  
             --从游标中获取一条记录,放入变量中;  
             fetch ref_t into tableName;  
                    SELECT COUNT(*) INTO mycount FROM user_tables WHERE TABLE_NAME = tableName;  
                    if mycount>0 then  
                       execute immediate 'DROP TABLE '||tableName || ' CASCADE CONSTRAINT ';  
                    end if;  
             exit when ref_t%notfound;  --退出;  
         end loop;  
     close ref_t;      
  end;  
/  
```

清除的话，将 **drop** 替换为 **truncate** 或者 **delete** ,过程 同上

### 如何使用sql语句操作表中的字段

1. 新增字段

```sql
ALTER TABLE 表名 ADD 时间字段 DATE DEFAULT SYSDATE;-- 新增
COMMENT ON COLUMN 表名.时间字段 IS '系统时间'; -- 注释
```

2. 修改字段


```sql
ALTER TABLE 表名 MODIFY 要修改的字段 VARCHAR2（12）;-- 修改
COMMENT ON COLUMN 表名.要修改的字段 IS '系统时间'; -- 注释
```

###    删除表空间

#### 删除用户

```sql
drop user 用户名称 cascade;
```

#### 删除表空间

```sql
drop tablespace 表空间名称 including contents and datafiles cascade constraint;
```

### 根据表相关信息进行查询

#### 根据表信息查询表

```sql
-- UTC可接字段
-- TABLE_NAME 表名
-- TABLE_TYPE 表类型
-- COMMENTS 注释
SELECT * FROM USER_TAB_COMMENTS UTC WHERE UTC.COMMENTS LIKE '%comment%'
```

#### 根据表字段查询

```sql
-- TABLE_NAME 表名
-- COLUMN_NAME 字段名称
-- COMMENTS 字段注释
SELECT * FROM USER_COL_COMMENTS WHERE TABLE_NAME = 'TABLE_NAME'
```

