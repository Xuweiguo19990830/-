## <font color="red">Oracle常用SQL语句</font>

<h3>查看锁表进程SQL语句1</h3>

****

```sql
select sess.sid,
	   sess.serial#,
	   lo.oracle_username,
	   lo.os_user_name,ao.object_name,      
	   lo.locked_mode      
	   		from v$locked_object lo,dba_objects ao,v$session sess  
	   			where ao.object_id = lo.object_id and lo.session_id = sess.sid;
```

<h3>查看锁表进程SQL语句2</h3>

****

```sql
select * from v$session t1, v$locked_object t2 
	where t1.sid = t2.SESSION_ID;
```

### 根据sid查看导致锁表的SQL语句

-- --

```sql
select sql_text
  from v$sqltext a
 where (a.HASH_VALUE, a.ADDRESS) in
       (select decode(sql_hash_value, 0, prev_hash_value, sql_hash_value),
               decode(sql_hash_value, 0, prev_sql_addr, sql_address)
          from v$session b
         where b.SID = 1568)	-- 锁表进程sid
 order by piece asc;
```

<h3>杀掉锁表进程</h3>

****

```sql
如有記錄則表示有lock，記錄下SID和serial# ，將記錄的ID替換下面的738,1429，即可解除LOCK  
alter system kill session 'SID,serial#';  
```

<h3>查看用户锁</h3>

****

```sql
select username,lock_date from dba_users where username='oracle用户名';
```

<h3>解用户锁</h3>

****

```sql
ALTER USER 'oracle用户名' ACCOUNT UNLOCK;
```

<h3>取消用户口令限制</h3>

****

```sql
SELECT username,PROFILE FROM dba_users;

select * from dba_profiles s where s.profile='DEFAULT' and resource_name='PASSWORD_LIFE_TIME';

alter profile default limit PASSWORD_LIFE_TIME UNLIMITED;
```

<h3>创建DBLINK</h3>

****

```sql
create public database link DDZXDB connect to CDTSCHEDULE
identified by cdtschedule
using 'DDZXDB';

create database link CDTDB connect to CDT
identified by dhcc123
using 'CDTDB';
```

<h3>temp表空间查看</h3>

****

```sql
SELECT TU.TABLESPACE_NAME                                    AS "TABLESPACE_NAME",
       TT.TOTAL - TU.USED                                    AS "FREE(G)",
       TT.TOTAL                                              AS "TOTAL(G)",
       ROUND(NVL(TU.USED, 0) / TT.TOTAL * 100, 3)            AS "USED(%)",
       ROUND(NVL(TT.TOTAL - TU.USED, 0) * 100 / TT.TOTAL, 3) AS "FREE(%)"
FROM (SELECT TABLESPACE_NAME, 
              SUM(BYTES_USED) / 1024 / 1024 / 1024 USED
       FROM GV_$TEMP_SPACE_HEADER
       GROUP BY TABLESPACE_NAME) TU ,
     (SELECT TABLESPACE_NAME,
              SUM(BYTES) / 1024 / 1024 / 1024 AS TOTAL
       FROM DBA_TEMP_FILES
       GROUP BY TABLESPACE_NAME) TT
WHERE TU.TABLESPACE_NAME = TT.TABLESPACE_NAME;
```

<h3>删除已连接用户 查看用户的连接状况</h3>

****

```sql
select username,sid,serial# from v$session 
                          sid
alter system kill session'517,1957' 
drop user nc2008 cascade；

SELECT t.tablespace_name, round(SUM(bytes / (1024 * 1024)), 0) ts_size 
FROM dba_tablespaces t, dba_data_files d 
WHERE t.tablespace_name = d.tablespace_name 
GROUP BY t.tablespace_name;

select total.tablespace_name,

　　round(total.MB, 2) as Total_MB,

　　round(total.MB - free.MB, 2) as Used_MB,

　　round((1 - free.MB / total.MB) * 100, 2) || '%' as Used_Pct

　　from (select tablespace_name, sum(bytes) / 1024 / 1024 as MB

　　from dba_free_space

　　group by tablespace_name) free,

　　(select tablespace_name, sum(bytes) / 1024 / 1024 as MB

　　from dba_data_files

　　group by tablespace_name) total

　　where free.tablespace_name = total.tablespace_name;
```

<h3>UNDO表空间超过了90%，是哪些会话的事务占用了这些空间</h3>

****

```sql
select s.sid,s.serial#,s.sql_id,v.usn,segment_name,r.status, v.rssize/1024/1024 mb
  2    From dba_rollback_segs r, v$rollstat v,v$transaction t,v$session s
  3    Where r.segment_id = v.usn and v.usn=t.xidusn and t.addr=s.taddr
  4    order by segment_name ;
```

<h3>expdp</h3>

****

```sql
1、创建DIRECTORY
create directory dir_ccre as '/home/dmpfile'; 
grant read,write on directory dir_ccre to public;

2、授权
Grant read,write on directory dir_dp to cdt160315;
select * from dba_directories;
expdp ccre1/ccre1 schemas=ccre1 dumpfile=ccre120181214.dmp parallel=4 DIRECTORY=dir_ccre logfile=ccre20181214160315.log
impdp pjcdt/dhcc123 DIRECTORY=dir_pj dumpfile=scf_dev03_20180327.dmp parallel=4  SCHEMAS=pjdev logfile=pjdev.log
impdp cdt170512/cdt170512 DIRECTORY=dir_dp dumpfile=cdt170512_%u.dmp parallel=4  REMAP_SCHEMA=cdt:cdt170512 logfile=cdt170512.log
```

<h3>数据泵导出多个dmp文件,导出整个数据库</h3>

****

```sql
expdp oracle用户名/oracle用户名密码  directory=导出目录  dumpfile=dmp文件名称  logfile=db1-190831.log  full=y
```

<h3>创建永久表空间</h3>

****

```sql
create bigfile tablespace ITREASURY 
logging 
datafile '/u01/app/oradata/orcl/itreasury2.dbf' 
size 1024m 
autoextend on 
next 100m maxsize 20480M 
extent management local autoallocate;
```

<h3>创建临时表空间</h3>

****

```sql
create temporary tablespace TEMP1 
tempfile '/u01/app/oradata/orcl/temp1.dbf' size 100M
autoextend on next 100M maxsize unlimited extent management local;

alter tablespace ITREASURY add datafile '/u01/app/oradata/orcl/itreasury3.dbf' size 20480M reuse;
	   
ALTER DATABASE DATAFILE '/app/oracle/oradata/orcl/cdtfc01.dbf' RESIZE 10240M;

DROP TABLESPACE TEMP INCLUDING CONTENTS AND DATAFILES;
```

<h3>指定某一个Oracle用户导入dmp文件</h3>

****

```sql
impdp oracle用户名/oracle用户名密码  directory=dmp文件目录 dumpfile=dmp文件名称 parallel=4 logfile=import.log remap_schema=cnmef:cnmef0814 schemas=oracle用户名;
```

### 指定某一个表空间导入dmp文件

---

```sql
impdp oracle用户名/oracle用户名密码  directory=dmp文件目录 dumpfile=dmp文件名称 parallel=4 logfile=import.log remap_schema=cnmef:cnmef0814  remap_tablespace=ITREASURY:CDTFC  schemas=oracle用户名;
```

<h3>增加数据文件命令</h3>

****

```sql
alter tablespace CDTFC add datafile '/u01/oradata/orcl/CDTFC06.dbf' size 2048m reuse;

alter tablespace “你的表空间” add datafile '文件路径' size 50M reuse;
```

<h3>查询当前数据库中所有数据文件是否为自动扩展</h3>

****

```sql
select tablespace_name,file_name,autoextensible from dba_data_files where tablespace_name = 'TEMP';
```

<h3>通过修改CDTFC的数据文件为自动扩展达到表空间CDTFC为自动扩展的目的</h3>

****

```sql
alter database datafile '/oracle/oradata/orcl/CDTFC.dbf' autoextend on;
```

<h3>确认是否已经修改成功</h3>

****

```sql
select tablespace_name,file_name,autoextensible from dba_data_files where tablespace_name = 'temp';
```

<h3>表空间可以自动扩展，每次增容尺寸为50M，最大扩到1G</h3>

****

```sql
ALTER DATABASE DATAFILE 'D:\oracle\product\10.2.0\db_1\oradata\orcl\CDTFC.dbf' AUTOEXTEND ON NEXT 50M MAXSIZE 1G;
```

<h3>Oracle解锁用户步骤</h3>

```sql
1.sqlplus / as sysdba						--登录数据库管理员用户

2.alter user 用户名 account unlock;		  --解锁用户
```

<h3>Oracle修改默认表空间</h3>

```sql
1.sqlplus cdt/dhcc123          								--登录需要修改的用户名/密码

2.alter user '需要修改的用户名' default tablespace '表空间名称';

3.select default_tablespace from user_users; 				--查看修改后的表空间名称
```

<h2>Oracle跨库复制表结构和表数据</h2>

```sql
create table 新表名 as select  * from 数据库用户名.旧表名;

create table sett_Foreigntradingdetail as select * from cnmef1121.sett_Foreigntradingdetail;
```

<h3>注意</h3>

	1.只会复制表数据和表结构，不会有任何约束。
	2.当 where 条件不成立时，只复制表结构，没有任务数据。

<h3>相关链接</h3>

<a href="<https://www.cnblogs.com/grimm/p/5984672.html>"><https://www.cnblogs.com/grimm/p/5984672.html></a>

<a href="https://blog.csdn.net/haiross/article/details/17002119">https://blog.csdn.net/haiross/article/details/17002119</a>



## <font color="red">Oracle函数</font>

### nal()函数



### nvl()函数



### concat()函数

​	将两个不同的字符串连接在一起。请注意，Oracle的CONCAT()只允许两个参数；换言之，一次只能将两个字符串串连起来。不过，在Oracle中，我们可以用'||'来一次串连多个字符串，例如'a'||'b'||'c'。

### decode()函数



### sysdate()函数



### lpad()函数

-- --

```
 lpad函数从左边对字符串使用指定的字符进行填充。从其字面意思也可以理解，l是left的简写，pad是填充的意思，所以lpad就是从左边填充的意思。

编辑本段语法
　　语法格式如下：

　　lpad( string, padded_length, [ pad_string ] )
	参数:
　　    1.string:
　　    	准备被填充的字符串；
　　    
　      2.padded_length:
　      	填充之后的字符串长度，也就是该函数返回的字符串长度，如果这个数量比原字符串的长度要短，lpad函数将会把字符串截取成从左到右的n个字符;
　      	 3.　pad_string:
    填充字符串，是个可选参数，这个字符串是要粘贴到string的左边，如果这个参数未写，lpad函数将会在string的左边粘贴空格。
```

### last_day()函数

​	LAST_DAY函数返回指定日期对应月份的最后一天。

### over()函数

​	

### binand()函数

​	