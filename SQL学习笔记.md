# SQL  
**SQL是用于访问和处理数据库的标准计算机语言   
SQL即结构化查询语言，用于管理关系化数据管理系统   
包括了数据插入、查询、更新和删除，数据库模式的创建和修改，及数据访问控制**    
SQL的基本作用  
* SQL面向数据库执行查询    
* SQL 可从数据库取回数据  
* SQL 可在数据库中插入新的记录  
* SQL 可更新数据库中的数据  
* SQL 可从数据库删除记录  
* SQL 可创建新数据库  
* SQL 可在数据库中创建新表  
* SQL 可在数据库中创建存储过程  
* SQL 可在数据库中创建视图  
* SQL 可以设置表、存储过程和视图的权限  
## 语法
* SQL对大小写不敏感  
* 每条SQL语句的末端应使用分号  
* SQL通常使用单引号而非双引号包裹文本值字段，若值为数值字段，则不需要引号。文本字段可以是字符串，它对文本字段中的大小写敏感。    
## 基础语句
### select
用于从数据库中选取数据，结果会被存储在一个结果表中，称为结果集。  
### select distinct 
该语句参数大于等于一，返回指定列中唯一且不相同的值  
### where子句
提取满足条件的数据    
逻辑运算符的优先级：()>not>and>or   
特殊条件：  
1. 空值判断：is null  
2. 在什么什么之间的值：between and  
3. 是否存在的判断：in  
4. 模糊查询：like  
	* 如：like '%M'，%M为能配符，表示模糊查询以M开头的数据    
	* %表示多个子值，_(下划线)则表示一个字符  
	* %M%：表示查询包含M的数据  
	* %M_：查询M在倒数第二位的数据  
### order by 
对结果集进行按照一列或多列内容排序，默认按照升序排序，关键字desc指定降序排序，asc升序。  
多参数时，先按照第一条排，顺位排序。  
order by A，B 默认升序  
order by A DESC,B A降序，B升序  
order by A,B DESC B降序，A升序  
### insert into 
一：insert into table_name values (1,2,...);  
只需提供被插入的值即可  
二：指定列名及插入的值，一一对应。  
### update
更新表中已存在的记录  
基本格式：update table_name set 修改的数据 where condition；  
where子句很重要，可以通过增加set:sql_safe_updates=1;这一语句（安全模式开关状态）来提醒带where子句。  
### delete  
删除表中记录的行  
SQL中包含三个有关删除的语句：drop、truncate和delete  
通常来说删除强度依次降低。  
后两者在操作时不像前者一样删除内容的同时还删除了表的结构，而delete不同于truncate，在删除表的内容的同时，不仅保留表的结构，还保留表所占的内存空间。  
## 深入学习  
### select top|limit|rownum
用于规定要返回的记录的数目  
MySQL支持limit语句，Oracle则支持rownum选取  
变相返回后N行：select top 5 * from table_name order by id desc;  
### 通配符   
通配符与like关键字一起使用  
包括%、_、[charlist]和[^charlist]或[!charlist]  
后两者指代字符序列中的任意单一字符或否  
注意：mysql中使用如select * from table_name where column_name regexp '^[a-f]'  
具体根据数据库使用对应的通配符  
### not in与in  
相当于=和<>，但in后面可以接多个参数  
### between  
选取介于两个值之间的值，这个值可以是数值、文本或日期。  
不同的数据库对位于between区间的两个值的取法不相同。  
### 别名  
为表或列指定名称  
横向合并一个表中的多列，可以使用关键字concat，并且可以指定合并列的名称和值之间的分隔符。  
### join  
包含left join、right join、inner join、outer join、full join(mysql中不支持)  
使用on关键字匹配  
### union  
合并两个或多个有相同数量的列和相似数据结构的值的select语句，且每个select语句中列顺序相同。  
结果表中的列名总是等于union中第一个select语句中的列名。  