---
title: Markdown语法
date: 2022-11-15 20:00:00
updated: 2022-11-17 9:32:00
tag: 语法
---

{% tip info %}本文章借鉴于[Fomalhaut博客](https://www.fomal.cn/posts/2013454d.html){% endtip %}

## 1.Markdown 语法自带格式

### 1.1 代码块

{% tabs 代码块 %}
<!-- tab 示例代码  -->
```shell
\```shell
# VSCode终端
hexo clean; hexo s
hexo clean; hexo g; hexo d
git add .; git commit -m "npm publish"; npm version patch; 
git push

# Cmder终端
hexo clean && hexo s
hexo clean && hexo g && hexo d
git add . && git commit -m "npm publish" && npm version patch
git push
\```
```
<!-- endtab -->

<!-- tab 渲染演示 -->
```shell
# VSCode终端
hexo clean; hexo s
hexo clean; hexo g; hexo d
git add .; git commit -m "npm publish"; npm version patch; 
git push

# Cmder终端
hexo clean && hexo s
hexo clean && hexo g && hexo d
git add . && git commit -m "npm publish" && npm version patch
git push
```
<!-- endtab -->
{% endtabs %}

### 1.2 多级标题

{% tabs 多级标题 %}
<!-- tab 示例代码  -->
```MARKDOWN
# H1
## H2
### H3
#### H4
##### H5
###### H6
```
<!-- endtab -->

<!-- tab 渲染演示 -->
见本文章标题！
<!-- endtab -->
{% endtabs %}

### 1.3 文字样式

{% tabs 文字样式 %}
<!-- tab 示例代码  -->
```MARKDOWN
<u>下划线演示</u>

文字**加粗**演示

文字*斜体*演示

文本`高亮`演示

文本~~删除~~线演示

<font size = 5>5号字</font>
<font face="黑体">黑体</font>
<font color=blue>蓝色</font>

<table><tr><td bgcolor=BlueViolet >这里的背景色是：BlueViolet ，此处输入任意想输入的内容</td></tr></table>
```
<!-- endtab -->

<!-- tab 渲染演示 -->
<u>下划线演示</u>

文字**加粗**演示

文字*斜体*演示

文本`高亮`演示

文本~~删除~~线演示

<font size = 5>5号字</font>
<font face="黑体">黑体</font>
<font color=blue>蓝色</font>

<table><tr><td bgcolor=BlueViolet >这里的背景色是：BlueViolet ，此处输入任意想输入的内容</td></tr></table>
<!-- endtab -->
{% endtabs %}

### 1.4 引用

{% tabs 引用 %}
<!-- tab 示例代码  -->
```MARKDOWN
>  Java
> 二级引用演示
> MySQL
> >外键
> >
> >事务
> >
> >**行级锁**(引用内部一样可以用格式)
> 
> ....
```
<!-- endtab -->

<!-- tab 渲染演示 -->
> Java
> 二级引用演示
> MySQL
> >外键
> >
> >事务
> >
> >**行级锁**(引用内部一样可以用格式)
>
> ....
<!-- endtab -->
{% endtabs %}

### 1.5 分割线

{% tabs 分割线 %}
<!-- tab 示例代码  -->
```MARKDOWN
---
***
```
<!-- endtab -->

<!-- tab 渲染演示 -->
---
***
<!-- endtab -->
{% endtabs %}

### 1.6 列表 (*,+,- 跟空格都可以)

#### 1.6.1 无序列表

{% tabs 无序列表 %}
<!-- tab 示例代码  -->
```MARKDOWN
* Java
* Python
* ...

+ Java
+ Python
+ ...

- Java
- Python
- ...
```
<!-- endtab -->

<!-- tab 渲染演示 -->
* Java
* Python
* ...

+ Java
+ Python
+ ...

- Java
- Python
- ...
<!-- endtab -->
{% endtabs %}

#### 1.6.2 有序列表

{% tabs 有序列表 %}
<!-- tab 示例代码  -->
```MARKDOWN
# 注意后面有空格
1. 
2. 
3. 
4. 
```
<!-- endtab -->

<!-- tab 渲染演示 -->
1. 
2. 
3. 
4. 
<!-- endtab -->
{% endtabs %}

### 1.7 图片

{% tabs 图片 %}
<!-- tab 示例代码  -->
```MARKDOWN
# 本地图片

<img src="/pic/网站icon.jpg" alt="示例图片" style="zoom:50%;" />

# 在线图片
![](https://xxxiuron-picture.oss-cn-chengdu.aliyuncs.com/--background_cover.png)
```
<!-- endtab -->

<!-- tab 渲染演示 -->
 本地图片:
<img src="/pic/网站icon.jpg" alt="示例图片" style="zoom:50%;" />

在线图片:
![](https://xxxiuron-picture.oss-cn-chengdu.aliyuncs.com/--background_cover.png)
<!-- endtab -->
{% endtabs %}

### 1.8 表格

{% tabs 表格 %}
<!-- tab 示例代码  -->
```MARKDOWN
| 项目标号 | 资金     | 备注 |
| -------- | -------- | ---- |
| 1        | 100，000 | 无   |
| 2        | 200，000 | 无   |
| 3        | 300,600  | 重要 |
```
<!-- endtab -->

<!-- tab 渲染演示 -->
| 项目标号 | 资金     | 备注 |
| -------- | -------- | ---- |
| 1        | 100，000 | 无   |
| 2        | 200，000 | 无   |
| 3        | 300,600  | 重要 |
<!-- endtab -->
{% endtabs %}

### 1.9 公式

{% tabs 公式 %}
<!-- tab 示例代码  -->
```MARKDOWN
$$
\Gamma(z)=\int_0^\infty t^{z-1}e^{-t}dt.
$$
```
<!-- endtab -->

<!-- tab 渲染演示 -->
$$
\Gamma(z)=\int_0^\infty t^{z-1}e^{-t}dt.
$$
<!-- endtab -->
{% endtabs %}

## 2.Butterfly 外挂标签

### 2.1 行内文本样式 text

{% tabs 行内文本样式 text %}
<!-- tab 标签语法  -->
```MARKDOWN
{% u 文本内容 %}
{% emp 文本内容 %}
{% wavy 文本内容 %}
{% del 文本内容 %}
{% kbd 文本内容 %}
{% psw 文本内容 %}
```
<!-- endtab -->

<!-- tab 示例源码 -->
```MARKDOWN
1. 带 {% u 下划线 %} 的文本
2. 带 {% emp 着重号 %} 的文本
3. 带 {% wavy 波浪线 %} 的文本
4. 带 {% del 删除线 %} 的文本
5. 键盘样式的文本 {% kbd command %} + {% kbd D %}
6. 密码样式的文本：{% psw 这里没有验证码 %}
```
<!-- endtab -->

<!-- tab 渲染演示 -->
1. 带 {% u 下划线 %} 的文本
2. 带 {% emp 着重号 %} 的文本
3. 带 {% wavy 波浪线 %} 的文本
4. 带 {% del 删除线 %} 的文本
5. 键盘样式的文本 {% kbd command %} + {% kbd D %}
6. 密码样式的文本：{% psw 这里没有验证码 %}
<!-- endtab -->
{% endtabs %}

### 2.2  行内文本 span

{% tabs 行内文本 %}
<!-- tab 标签语法  -->
```MARKDOWN
{% span 样式参数(参数以空格划分), 文本内容 %}
```
<!-- endtab -->

<!-- tab 配置参数  -->
1. {% span red, 字体 %}: logo, code
2. {% span red, 颜色 %}: red,yellow,green,cyan,blue,gray
3. {% span red, 大小 %}: small, h4, h3, h2, h1, large, huge, ultra
4. {% span red, 对齐方向 %}: left, center, right
<!-- endtab -->

<!-- tab 示例源码 -->
```MARKDOWN
- 彩色文字
在一段话中方便插入各种颜色的标签，包括：{% span red, 红色 %}、{% span yellow, 黄色 %}、{% span green, 绿色 %}、{% span cyan, 青色 %}、{% span blue, 蓝色 %}、{% span gray, 灰色 %}。
- 超大号文字
文档「开始」页面中的标题部分就是超大号文字。
{% span center logo large, Volantis %}
{% span center small, A Wonderful Theme for Hexo %}
```
<!-- endtab -->

<!-- tab 渲染演示 -->
- 彩色文字
在一段话中方便插入各种颜色的标签，包括：{% span red, 红色 %}、{% span yellow, 黄色 %}、{% span green, 绿色 %}、{% span cyan, 青色 %}、{% span blue, 蓝色 %}、{% span gray, 灰色 %}。
- 超大号文字
文档「开始」页面中的标题部分就是超大号文字。
{% span center logo large, Volantis %}
{% span center small, A Wonderful Theme for Hexo %}
<!-- endtab -->
{% endtabs %}

### 2.3 段落文本 p

{% tabs 段落文本p %}
<!-- tab 标签语法  -->
```MARKDOWN
{% p 样式参数(参数以空格划分), 文本内容 %}
```
<!-- endtab -->

<!-- tab 配置参数 -->
1. {% span red, 字体 %}: logo, code
2. {% span red, 颜色 %}: red,yellow,green,cyan,blue,gray
3. {% span red, 大小 %}: small, h4, h3, h2, h1, large, huge, ultra
4. {% span red, 对齐方向 %}: left, center, right
<!-- endtab -->

<!-- tab 示例源码 -->
```MARKDOWN
- 彩色文字
在一段话中方便插入各种颜色的标签，包括：{% p red, 红色 %}、{% p yellow, 黄色 %}、{% p green, 绿色 %}、{% p cyan, 青色 %}、{% p blue, 蓝色 %}、{% p gray, 灰色 %}。
- 超大号文字
文档「开始」页面中的标题部分就是超大号文字。
{% p center logo large, Volantis %}
{% p center small, A Wonderful Theme for Hexo %}
```
<!-- endtab -->

<!-- tab 渲染演示 -->
- 彩色文字
在一段话中方便插入各种颜色的标签，包括：{% p red, 红色 %}、{% p yellow, 黄色 %}、{% p green, 绿色 %}、{% p cyan, 青色 %}、{% p blue, 蓝色 %}、{% p gray, 灰色 %}。
- 超大号文字
文档「开始」页面中的标题部分就是超大号文字。
{% p center logo large, Volantis %}
{% p center small, A Wonderful Theme for Hexo %}
<!-- endtab -->
{% endtabs %}

### 2.4 引用 note

{% tabs 引用 note %}
<!-- tab 通用配置  -->
```MARKDOWN
note:
  # Note tag style values:
  #  - simple    bs-callout old alert style. Default.
  #  - modern    bs-callout new (v2-v3) alert style.
  #  - flat      flat callout style with background, like on Mozilla or StackOverflow.
  #  - disabled  disable all CSS styles import of note tag.
  style: simple
  icons: false
  border_radius: 3
  # Offset lighter of background in % for modern and flat styles (modern: -12 | 12; flat: -18 | 6).
  # Offset also applied to label tag variables. This option can work with disabled note tag.
  light_bg_offset: 0
```
<!-- endtab -->

<!-- tab 标签语法  -->
```MARKDOWN
# 自带icon
{% note [class] [no-icon] [style] %}
Any content (support inline tags too.io).
{% endnote %}
# 外部icon
{% note [color] [icon] [style] %}
Any content (support inline tags too.io).
{% endnote %}
```
<!-- endtab -->

<!-- tab 配置参数 -->
1. 自带 icon

|参数 | 用法|
|-----|-----|
|class	|【可选】标识，不同的标识有不同的配色 （ default /primary/success/info/warning/danger ）|
|no-icon |【可选】不显示 icon|
|style	|【可选】可以覆盖配置中的 style （simple/modern/flat/disabled）|
2. 外部 icon

|参数 | 用法|
|-----|-----|
|class |【可选】标识，不同的标识有不同的配色 （ default /blue/pink/red/purple/orange/green ）|
|no-icon |【可选】可配置自定义 icon （只支持 fontawesome 图标，也可以配置 no-icon）|
|style	|【可选】可以覆盖配置中的 style （simple/modern/flat/disabled）|
<!-- endtab -->

<!-- tab 示例源码 -->
{% folding  1. 自带icon %}
1. {% span red, simple %} 样式
```MARKDOWN
{% note simple %}默认 提示块标签{% endnote %}

{% note default simple %}default 提示块标签{% endnote %}

{% note primary simple %}primary 提示块标签{% endnote %}

{% note success simple %}success 提示块标签{% endnote %}

{% note info simple %}info 提示块标签{% endnote %}

{% note warning simple %}warning 提示块标签{% endnote %}

{% note danger simple %}danger 提示块标签{% endnote %}
```
2. {% span red, modern %} 样式
```MARKDOWN
{% note modern %}默认 提示块标签{% endnote %}

{% note default modern %}default 提示块标签{% endnote %}

{% note primary modern %}primary 提示块标签{% endnote %}

{% note success modern %}success 提示块标签{% endnote %}

{% note info modern %}info 提示块标签{% endnote %}

{% note warning modern %}warning 提示块标签{% endnote %}

{% note danger modern %}danger 提示块标签{% endnote %}
```
3. {% span red, flat %} 样式
```MARKDOWN
{% note flat %}默认 提示块标签{% endnote %}

{% note default flat %}default 提示块标签{% endnote %}

{% note primary flat %}primary 提示块标签{% endnote %}

{% note success flat %}success 提示块标签{% endnote %}

{% note info flat %}info 提示块标签{% endnote %}

{% note warning flat %}warning 提示块标签{% endnote %}

{% note danger flat %}danger 提示块标签{% endnote %}
```
4. {% span red, disabled %} 样式
```MARKDOWN
{% note disabled %}默认 提示块标签{% endnote %}

{% note default disabled %}default 提示块标签{% endnote %}

{% note primary disabled %}primary 提示块标签{% endnote %}

{% note success disabled %}success 提示块标签{% endnote %}

{% note info disabled %}info 提示块标签{% endnote %}

{% note warning disabled %}warning 提示块标签{% endnote %}

{% note danger disabled %}danger 提示块标签{% endnote %}
```
5. {% span red, no-icon %} 样式
```MARKDOWN
{% note no-icon %}默认 提示块标签{% endnote %}

{% note default no-icon %}default 提示块标签{% endnote %}

{% note primary no-icon %}primary 提示块标签{% endnote %}

{% note success no-icon %}success 提示块标签{% endnote %}

{% note info no-icon %}info 提示块标签{% endnote %}

{% note warning no-icon %}warning 提示块标签{% endnote %}

{% note danger no-icon %}danger 提示块标签{% endnote %}
```
{% endfolding %}

{% folding  2. 外部icon %}
1. {% span red, simple %} 样式
```MARKDOWN
{% note 'fab fa-cc-visa' simple %}你是刷 Visa 还是 UnionPay{% endnote %}

{% note blue 'fas fa-bullhorn' simple %}2021年快到了....{% endnote %}

{% note pink 'fas fa-car-crash' simple %}小心开车 安全至上{% endnote %}

{% note red 'fas fa-fan' simple%}这是三片呢？还是四片？{% endnote %}

{% note orange 'fas fa-battery-half' simple %}你是刷 Visa 还是 UnionPay{% endnote %}

{% note purple 'far fa-hand-scissors' simple %}剪刀石头布{% endnote %}

{% note green 'fab fa-internet-explorer' simple %}前端最讨厌的浏览器{% endnote %}
```
2. {% span red, modern %} 样式
```MARKDOWN
{% note 'fab fa-cc-visa' modern %}你是刷 Visa 还是 UnionPay{% endnote %}

{% note blue 'fas fa-bullhorn' modern %}2021年快到了....{% endnote %}

{% note pink 'fas fa-car-crash' modern %}小心开车 安全至上{% endnote %}

{% note red 'fas fa-fan' modern%}这是三片呢？还是四片？{% endnote %}

{% note orange 'fas fa-battery-half' modern %}你是刷 Visa 还是 UnionPay{% endnote %}

{% note purple 'far fa-hand-scissors' modern %}剪刀石头布{% endnote %}

{% note green 'fab fa-internet-explorer' modern %}前端最讨厌的浏览器{% endnote %}
```
3. {% span red, flat %} 样式
```MARKDOWN
{% note 'fab fa-cc-visa' flat %}你是刷 Visa 还是 UnionPay{% endnote %}

{% note blue 'fas fa-bullhorn' flat %}2021年快到了....{% endnote %}

{% note pink 'fas fa-car-crash' flat %}小心开车 安全至上{% endnote %}

{% note red 'fas fa-fan' flat%}这是三片呢？还是四片？{% endnote %}

{% note orange 'fas fa-battery-half' flat %}你是刷 Visa 还是 UnionPay{% endnote %}

{% note purple 'far fa-hand-scissors' flat %}剪刀石头布{% endnote %}

{% note green 'fab fa-internet-explorer' flat %}前端最讨厌的浏览器{% endnote %}
```
4. {% span red, disabled %} 样式
```MARKDOWN
{% note 'fab fa-cc-visa' disabled %}你是刷 Visa 还是 UnionPay{% endnote %}

{% note blue 'fas fa-bullhorn' disabled %}2021年快到了....{% endnote %}

{% note pink 'fas fa-car-crash' disabled %}小心开车 安全至上{% endnote %}

{% note red 'fas fa-fan' disabled %}这是三片呢？还是四片？{% endnote %}

{% note orange 'fas fa-battery-half' disabled %}你是刷 Visa 还是 UnionPay{% endnote %}

{% note purple 'far fa-hand-scissors' disabled %}剪刀石头布{% endnote %}

{% note green 'fab fa-internet-explorer' disabled %}前端最讨厌的浏览器{% endnote %}
```
5. {% span red, no-icon %} 样式
```MARKDOWN
{% note no-icon %}你是刷 Visa 还是 UnionPay{% endnote %}

{% note blue no-icon %}2021年快到了....{% endnote %}

{% note pink no-icon %}小心开车 安全至上{% endnote %}

{% note red no-icon %}这是三片呢？还是四片？{% endnote %}

{% note orange no-icon %}你是刷 Visa 还是 UnionPay{% endnote %}

{% note purple no-icon %}剪刀石头布{% endnote %}

{% note green no-icon %}前端最讨厌的浏览器{% endnote %}
```
{% endfolding %}
<!-- endtab -->

<!-- tab 渲染演示 -->
{% folding  1. 自带icon %}
1. {% span red, simple %} 样式

{% note simple %}默认 提示块标签{% endnote %}

{% note default simple %}default 提示块标签{% endnote %}

{% note primary simple %}primary 提示块标签{% endnote %}

{% note success simple %}success 提示块标签{% endnote %}

{% note info simple %}info 提示块标签{% endnote %}

{% note warning simple %}warning 提示块标签{% endnote %}

{% note danger simple %}danger 提示块标签{% endnote %}

2. {% span red, modern %} 样式

{% note modern %}默认 提示块标签{% endnote %}

{% note default modern %}default 提示块标签{% endnote %}

{% note primary modern %}primary 提示块标签{% endnote %}

{% note success modern %}success 提示块标签{% endnote %}

{% note info modern %}info 提示块标签{% endnote %}

{% note warning modern %}warning 提示块标签{% endnote %}

{% note danger modern %}danger 提示块标签{% endnote %}

3. {% span red, flat %} 样式

{% note flat %}默认 提示块标签{% endnote %}

{% note default flat %}default 提示块标签{% endnote %}

{% note primary flat %}primary 提示块标签{% endnote %}

{% note success flat %}success 提示块标签{% endnote %}

{% note info flat %}info 提示块标签{% endnote %}

{% note warning flat %}warning 提示块标签{% endnote %}

{% note danger flat %}danger 提示块标签{% endnote %}

4. {% span red, disabled %} 样式

{% note disabled %}默认 提示块标签{% endnote %}

{% note default disabled %}default 提示块标签{% endnote %}

{% note primary disabled %}primary 提示块标签{% endnote %}

{% note success disabled %}success 提示块标签{% endnote %}

{% note info disabled %}info 提示块标签{% endnote %}

{% note warning disabled %}warning 提示块标签{% endnote %}

{% note danger disabled %}danger 提示块标签{% endnote %}

5. {% span red, no-icon %} 样式

{% note no-icon %}默认 提示块标签{% endnote %}

{% note default no-icon %}default 提示块标签{% endnote %}

{% note primary no-icon %}primary 提示块标签{% endnote %}

{% note success no-icon %}success 提示块标签{% endnote %}

{% note info no-icon %}info 提示块标签{% endnote %}

{% note warning no-icon %}warning 提示块标签{% endnote %}

{% note danger no-icon %}danger 提示块标签{% endnote %}

{% endfolding %}

{% folding  2. 外部icon %}
1. {% span red, simple %} 样式

{% note 'fab fa-cc-visa' simple %}你是刷 Visa 还是 UnionPay{% endnote %}

{% note blue 'fas fa-bullhorn' simple %}2021年快到了....{% endnote %}

{% note pink 'fas fa-car-crash' simple %}小心开车 安全至上{% endnote %}

{% note red 'fas fa-fan' simple%}这是三片呢？还是四片？{% endnote %}

{% note orange 'fas fa-battery-half' simple %}你是刷 Visa 还是 UnionPay{% endnote %}

{% note purple 'far fa-hand-scissors' simple %}剪刀石头布{% endnote %}

{% note green 'fab fa-internet-explorer' simple %}前端最讨厌的浏览器{% endnote %}

2. {% span red, modern %} 样式

{% note 'fab fa-cc-visa' modern %}你是刷 Visa 还是 UnionPay{% endnote %}

{% note blue 'fas fa-bullhorn' modern %}2021年快到了....{% endnote %}

{% note pink 'fas fa-car-crash' modern %}小心开车 安全至上{% endnote %}

{% note red 'fas fa-fan' modern%}这是三片呢？还是四片？{% endnote %}

{% note orange 'fas fa-battery-half' modern %}你是刷 Visa 还是 UnionPay{% endnote %}

{% note purple 'far fa-hand-scissors' modern %}剪刀石头布{% endnote %}

{% note green 'fab fa-internet-explorer' modern %}前端最讨厌的浏览器{% endnote %}

3. {% span red, flat %} 样式

{% note 'fab fa-cc-visa' flat %}你是刷 Visa 还是 UnionPay{% endnote %}

{% note blue 'fas fa-bullhorn' flat %}2021年快到了....{% endnote %}

{% note pink 'fas fa-car-crash' flat %}小心开车 安全至上{% endnote %}

{% note red 'fas fa-fan' flat%}这是三片呢？还是四片？{% endnote %}

{% note orange 'fas fa-battery-half' flat %}你是刷 Visa 还是 UnionPay{% endnote %}

{% note purple 'far fa-hand-scissors' flat %}剪刀石头布{% endnote %}

{% note green 'fab fa-internet-explorer' flat %}前端最讨厌的浏览器{% endnote %}

4. {% span red, disabled %} 样式

{% note 'fab fa-cc-visa' disabled %}你是刷 Visa 还是 UnionPay{% endnote %}

{% note blue 'fas fa-bullhorn' disabled %}2021年快到了....{% endnote %}

{% note pink 'fas fa-car-crash' disabled %}小心开车 安全至上{% endnote %}

{% note red 'fas fa-fan' disabled %}这是三片呢？还是四片？{% endnote %}

{% note orange 'fas fa-battery-half' disabled %}你是刷 Visa 还是 UnionPay{% endnote %}

{% note purple 'far fa-hand-scissors' disabled %}剪刀石头布{% endnote %}

{% note green 'fab fa-internet-explorer' disabled %}前端最讨厌的浏览器{% endnote %}

5. {% span red, no-icon %} 样式

{% note no-icon %}你是刷 Visa 还是 UnionPay{% endnote %}

{% note blue no-icon %}2021年快到了....{% endnote %}

{% note pink no-icon %}小心开车 安全至上{% endnote %}

{% note red no-icon %}这是三片呢？还是四片？{% endnote %}

{% note orange no-icon %}你是刷 Visa 还是 UnionPay{% endnote %}

{% note purple no-icon %}剪刀石头布{% endnote %}

{% note green no-icon %}前端最讨厌的浏览器{% endnote %}

{% endfolding %}
<!-- endtab -->
{% endtabs %}

### 2.5 上标标签 tip
{% tabs 上标标签 tip %}
<!-- tab 标签语法  -->
```MARKDOWN
{% tip [参数，可选] %}文本内容{% endtip %}
```
<!-- endtab -->

<!-- tab 配置参数 -->
1. {% span red, 样式 %}: success,error,warning,bolt,ban,home,sync,cogs,key,bell
2. {% span red, 自定义图标 %}: 支持 fontawesome。
<!-- endtab -->

<!-- tab 示例源码 -->
```MARKDOWN
{% tip %}default{% endtip %}
{% tip info %}info{% endtip %}
{% tip success %}success{% endtip %}
{% tip error %}error{% endtip %}
{% tip warning %}warning{% endtip %}
{% tip bolt %}bolt{% endtip %}
{% tip ban %}ban{% endtip %}
{% tip home %}home{% endtip %}
{% tip sync %}sync{% endtip %}
{% tip cogs %}cogs{% endtip %}
{% tip key %}key{% endtip %}
{% tip bell %}bell{% endtip %}
{% tip fa-atom %}自定义font awesome图标{% endtip %}
```
<!-- endtab -->

<!-- tab 渲染演示 -->
{% tip %}default{% endtip %}
{% tip info %}info{% endtip %}
{% tip success %}success{% endtip %}
{% tip error %}error{% endtip %}
{% tip warning %}warning{% endtip %}
{% tip bolt %}bolt{% endtip %}
{% tip ban %}ban{% endtip %}
{% tip home %}home{% endtip %}
{% tip sync %}sync{% endtip %}
{% tip cogs %}cogs{% endtip %}
{% tip key %}key{% endtip %}
{% tip bell %}bell{% endtip %}
{% tip fa-atom %}自定义font awesome图标{% endtip %}
<!-- endtab -->
{% endtabs %}

### 2.6 动态标签 anima

{% tabs 动态标签anima %}
<!-- tab 标签语法  -->
```MARKDOWN
{% tip [参数，可选] %}文本内容{% endtip %}
```
<!-- endtab -->

<!-- tab 配置参数 -->
{% note info flat %}
1. 将所需的 CSS 类添加到图标（或 DOM 中的任何元素）。
2. 对于父级悬停样式，需要给目标元素添加指定 CSS 类，同时还要给目标元素的父级元素添加 CSS 类 faa-parent animated-hover。（详情见示例及示例源码）
You can regulate the speed of the animation by adding the CSS class or . faa-fastfaa-slow
3. 可以通过给目标元素添加 CSS 类 faa-fast 或 faa-slow 来控制动画快慢。
{% endnote %}
<!-- endtab -->

<!-- tab 示例源码 -->
1. On DOM load（当页面加载时显示动画）
```MARKDOWN
{% tip warning faa-horizontal animated %}warning{% endtip %}
{% tip ban faa-flash animated %}ban{% endtip %}
```
2. 调整动画速度
```MARKDOWN
{% tip warning faa-horizontal animated faa-fast %}warning{% endtip %}
{% tip ban faa-flash animated faa-slow %}ban{% endtip %}
```
3. On hover（当鼠标悬停时显示动画）
```MARKDOWN
{% tip warning faa-horizontal animated-hover %}warning{% endtip %}
{% tip ban faa-flash animated-hover %}ban{% endtip %}
```
4. On parent hover（当鼠标悬停在父级元素时显示动画）
```MARKDOWN
{% tip warning faa-parent animated-hover %}<p class="faa-horizontal">warning</p>{% endtip %}
{% tip ban faa-parent animated-hover %}<p class="faa-flash">ban</p>{% endtip %}
```
<!-- endtab -->

<!-- tab 渲染演示 -->
1.On DOM load（当页面加载时显示动画）

{% tip warning faa-horizontal animated %}warning{% endtip %}
{% tip ban faa-flash animated %}ban{% endtip %}

2.调整动画速度

{% tip warning faa-horizontal animated faa-fast %}warning{% endtip %}
{% tip ban faa-flash animated faa-slow %}ban{% endtip %}

3.On hover（当鼠标悬停时显示动画）

{% tip warning faa-horizontal animated-hover %}warning{% endtip %}
{% tip ban faa-flash animated-hover %}ban{% endtip %}

4.On parent hover（当鼠标悬停在父级元素时显示动画）

{% tip warning faa-parent animated-hover %}<p class="faa-horizontal">warning</p>{% endtip %}
{% tip ban faa-parent animated-hover %}<p class="faa-flash">ban</p>{% endtip %}

<!-- endtab -->
{% endtabs %}


### 2.7 复选列表 checkbox

{% tabs 复选列表checkbox %}
<!-- tab 标签语法  -->
```MARKDOWN
{% checkbox 样式参数（可选）, 文本（支持简单md） %}
```
<!-- endtab -->

<!-- tab 配置参数 -->
1. {% span red, 样式 %}: plus, minus, times
2. {% span red, 颜色 %}: red,yellow,green,cyan,blue,gray
3. {% span red, 选中状态 %}: checked
<!-- endtab -->

<!-- tab 示例源码 -->
```MARKDOWN
{% checkbox 纯文本测试 %}
{% checkbox checked, 支持简单的 [markdown](https://guides.github.com/features/mastering-markdown/) 语法 %}
{% checkbox red, 支持自定义颜色 %}
{% checkbox green checked, 绿色 + 默认选中 %}
{% checkbox yellow checked, 黄色 + 默认选中 %}
{% checkbox cyan checked, 青色 + 默认选中 %}
{% checkbox blue checked, 蓝色 + 默认选中 %}
{% checkbox plus green checked, 增加 %}
{% checkbox minus yellow checked, 减少 %}
{% checkbox times red checked, 叉 %}
```
<!-- endtab -->

<!-- tab 渲染演示 -->
{% checkbox 纯文本测试 %}
{% checkbox checked, 支持简单的 [markdown](https://guides.github.com/features/mastering-markdown/) 语法 %}
{% checkbox red, 支持自定义颜色 %}
{% checkbox green checked, 绿色 + 默认选中 %}
{% checkbox yellow checked, 黄色 + 默认选中 %}
{% checkbox cyan checked, 青色 + 默认选中 %}
{% checkbox blue checked, 蓝色 + 默认选中 %}
{% checkbox plus green checked, 增加 %}
{% checkbox minus yellow checked, 减少 %}
{% checkbox times red checked, 叉 %}
<!-- endtab -->
{% endtabs %}

### 2.8 单选列表 radio

{% tabs 单选列表radio %}
<!-- tab 标签语法  -->
```MARKDOWN
{% radio 样式参数（可选）, 文本（支持简单md） %}
```
<!-- endtab -->

<!-- tab 配置参数 -->
1. {% span red, 颜色 %}: red,yellow,green,cyan,blue,gray
2. {% span red, 选中状态 %}: checked
<!-- endtab -->

<!-- tab 示例源码 -->
```MARKDOWN

{% radio 纯文本测试 %}
{% radio checked, 支持简单的 [markdown](https://guides.github.com/features/mastering-markdown/) 语法 %}
{% radio red, 支持自定义颜色 %}
{% radio green, 绿色 %}
{% radio yellow, 黄色 %}
{% radio cyan, 青色 %}
{% radio blue, 蓝色 %}
```
<!-- endtab -->

<!-- tab 渲染演示 -->

{% radio 纯文本测试 %}
{% radio checked, 支持简单的 [markdown](https://guides.github.com/features/mastering-markdown/) 语法 %}
{% radio red, 支持自定义颜色 %}
{% radio green, 绿色 %}
{% radio yellow, 黄色 %}
{% radio cyan, 青色 %}
{% radio blue, 蓝色 %}
<!-- endtab -->
{% endtabs %}

### 2.9 时间轴 timeline

{% tabs 时间轴timeline %}
<!-- tab 标签语法  -->
```MARKDOWN
{% timeline 时间线标题（可选）[,color] %}
<!-- timeline 时间节点（标题） -->
正文内容
<!-- endtimeline -->
<!-- timeline 时间节点（标题） -->
正文内容
<!-- endtimeline -->
{% endtimeline %}
```
<!-- endtab -->

<!-- tab 配置参数 -->
1. {% span red, title %}: 标题 / 时间线
2. {% span red, color %}:timeline 颜色:default (留空) /blue/pink /red/purple /orange/green

<!-- endtab -->

<!-- tab 示例源码 -->
```MARKDOWN
{% timeline 时间轴样式,blue %}

<!-- timeline 2020-07-24 [2.6.6 -> 3.0](https://github.com/volantis-x/hexo-theme-volantis/releases) -->

1. 如果有 `hexo-lazyload-image` 插件，需要删除并重新安装最新版本，设置 `lazyload.isSPA: true`。
2. 2.x 版本的 css 和 js 不适用于 3.x 版本，如果使用了 `use_cdn: true` 则需要删除。
3. 2.x 版本的 fancybox 标签在 3.x 版本中被重命名为 gallery 。
4. 2.x 版本的置顶 `top: true` 改为了 `pin: true`，并且同样适用于 `layout: page` 的页面。
5. 如果使用了 `hexo-offline` 插件，建议卸载，3.0 版本默认开启了 pjax 服务。

<!-- endtimeline -->

<!-- timeline 2020-05-15 [2.6.3 -> 2.6.6](https://github.com/volantis-x/hexo-theme-volantis/releases/tag/2.6.6) -->

不需要额外处理。

<!-- endtimeline -->

<!-- timeline 2020-04-20 [2.6.2 -> 2.6.3](https://github.com/volantis-x/hexo-theme-volantis/releases/tag/2.6.3) -->

1. 全局搜索 `seotitle` 并替换为 `seo_title`。
2. group 组件的索引规则有变，使用 group 组件的文章内，`group: group_name` 对应的组件名必须是 `group_name`。
2. group 组件的列表名优先显示文章的 `short_title` 其次是 `title`。

<!-- endtimeline -->

{% endtimeline %}
```
<!-- endtab -->

<!-- tab 渲染演示 -->
{% timeline 时间轴样式,blue %}

<!-- timeline 2020-07-24 [2.6.6 -> 3.0](https://github.com/volantis-x/hexo-theme-volantis/releases) -->

1. 如果有 `hexo-lazyload-image` 插件，需要删除并重新安装最新版本，设置 `lazyload.isSPA: true`。
2. 2.x 版本的 css 和 js 不适用于 3.x 版本，如果使用了 `use_cdn: true` 则需要删除。
3. 2.x 版本的 fancybox 标签在 3.x 版本中被重命名为 gallery 。
4. 2.x 版本的置顶 `top: true` 改为了 `pin: true`，并且同样适用于 `layout: page` 的页面。
5. 如果使用了 `hexo-offline` 插件，建议卸载，3.0 版本默认开启了 pjax 服务。

<!-- endtimeline -->

<!-- timeline 2020-05-15 [2.6.3 -> 2.6.6](https://github.com/volantis-x/hexo-theme-volantis/releases/tag/2.6.6) -->

不需要额外处理。

<!-- endtimeline -->

<!-- timeline 2020-04-20 [2.6.2 -> 2.6.3](https://github.com/volantis-x/hexo-theme-volantis/releases/tag/2.6.3) -->

1. 全局搜索 `seotitle` 并替换为 `seo_title`。
2. group 组件的索引规则有变，使用 group 组件的文章内，`group: group_name` 对应的组件名必须是 `group_name`。
2. group 组件的列表名优先显示文章的 `short_title` 其次是 `title`。

<!-- endtimeline -->

{% endtimeline %}
<!-- endtab -->
{% endtabs %}

### 2.10 链接卡片 link

{% tabs 链接卡片link %}
<!-- tab 标签语法  -->
```MARKDOWN
{% link 标题, 链接, 图片链接（可选） %}
```
<!-- endtab -->

<!-- tab 示例源码 -->
```MARKDOWN
{% link 糖果屋教程贴, https://akilar.top/posts/615e2dec/, https://cdn.cbd.int/akilar-candyassets@1.0.36/image/siteicon/favicon.ico %}
```
<!-- endtab -->

<!-- tab 渲染演示 -->
{% link 糖果屋教程贴, https://akilar.top/posts/615e2dec/, https://cdn.cbd.int/akilar-candyassets@1.0.36/image/siteicon/favicon.ico %}
<!-- endtab -->
{% endtabs %}

### 2.11 按钮 btns

{% tabs 按钮btns %}
<!-- tab 标签语法  -->
```MARKDOWN
{% btns 样式参数 %}
{% cell 标题, 链接, 图片或者图标 %}
{% cell 标题, 链接, 图片或者图标 %}
{% endbtns %}
```
<!-- endtab -->

<!-- tab 配置参数 -->
1. {% span red, 圆角样式 %}：rounded, circle
2. {% span red, 增加文字样式 %}：可以在容器内增加 <b> 标题 </b> 和 <p> 描述文字 </p>
3. {% span red, 布局方式 %}：
默认为自动宽度，适合视野内只有一两个的情况。

|参数	| 含义|
|-----|-----|
|wide	|宽一点的按钮|
|fill	|填充布局，自动铺满至少一行，多了会换行|
|center	|居中，按钮之间是固定间距|
|around	|居中分散|
|grid2	|等宽最多 2 列，屏幕变窄会适当减少列数|
|grid3	|等宽最多 3 列，屏幕变窄会适当减少列数|
|grid4	|等宽最多 4 列，屏幕变窄会适当减少列数|
|grid5	|等宽最多 5 列，屏幕变窄会适当减少列数|

<!-- endtab -->

<!-- tab 示例源码 -->
1.如果需要显示类似「团队成员」之类的一组含有头像的链接
```MARKDOWN
{% btns circle grid5 %}
{% cell xxxiuron, https://x-xiuron.com, https://xxxiuron-picture.oss-cn-chengdu.aliyuncs.com/%E5%A4%B4%E5%83%8F1.jpg %}
{% cell xxxiuron, https://x-xiuron.com, https://xxxiuron-picture.oss-cn-chengdu.aliyuncs.com/%E5%A4%B4%E5%83%8F1.jpg %}
{% cell xxxiuron, https://x-xiuron.com, https://xxxiuron-picture.oss-cn-chengdu.aliyuncs.com/%E5%A4%B4%E5%83%8F1.jpg %}
{% cell xxxiuron, https://x-xiuron.com, https://xxxiuron-picture.oss-cn-chengdu.aliyuncs.com/%E5%A4%B4%E5%83%8F1.jpg %}
{% cell xxxiuron, https://x-xiuron.com, https://xxxiuron-picture.oss-cn-chengdu.aliyuncs.com/%E5%A4%B4%E5%83%8F1.jpg %}
{% endbtns %}
```
2.或者含有图标的按钮
```MARKDOWN
{% btns rounded grid5 %}
{% cell 下载源码, /, fas fa-download %}
{% cell 查看文档, /, fas fa-book-open %}
{% endbtns %}
```
3.圆形图标 + 标题 + 描述 + 图片 + 网格 5 列 + 居中
```MARKDOWN
{% btns circle center grid5 %}
<a href='https://apps.apple.com/cn/app/heart-mate-pro-hrm-utility/id1463348922?ls=1'>
  <i class='fab fa-apple'></i>
  <b>心率管家</b>
  {% p red, 专业版 %}
  <img src='https://cdn.jsdelivr.net/gh/fomalhaut1998/cdn-assets/qrcode/heartmate_pro.png'>
</a>
<a href='https://apps.apple.com/cn/app/heart-mate-lite-hrm-utility/id1475747930?ls=1'>
  <i class='fab fa-apple'></i>
  <b>心率管家</b>
  {% p green, 免费版 %}
  <img src='https://cdn.jsdelivr.net/gh/fomalhaut1998/cdn-assets/qrcode/heartmate_lite.png'>
</a>
{% endbtns %}
```
<!-- endtab -->

<!-- tab 渲染演示 -->
1.如果需要显示类似「团队成员」之类的一组含有头像的链接

{% btns circle grid5 %}
{% cell xxxiuron, https://x-xiuron.com, https://xxxiuron-picture.oss-cn-chengdu.aliyuncs.com/%E5%A4%B4%E5%83%8F1.jpg %}
{% cell xxxiuron, https://x-xiuron.com, https://xxxiuron-picture.oss-cn-chengdu.aliyuncs.com/%E5%A4%B4%E5%83%8F1.jpg %}
{% cell xxxiuron, https://x-xiuron.com, https://xxxiuron-picture.oss-cn-chengdu.aliyuncs.com/%E5%A4%B4%E5%83%8F1.jpg %}
{% cell xxxiuron, https://x-xiuron.com, https://xxxiuron-picture.oss-cn-chengdu.aliyuncs.com/%E5%A4%B4%E5%83%8F1.jpg %}
{% cell xxxiuron, https://x-xiuron.com, https://xxxiuron-picture.oss-cn-chengdu.aliyuncs.com/%E5%A4%B4%E5%83%8F1.jpg %}
{% endbtns %}

2.或者含有图标的按钮

{% btns rounded grid5 %}
{% cell 下载源码, /, fas fa-download %}
{% cell 查看文档, /, fas fa-book-open %}
{% endbtns %}

3.圆形图标 + 标题 + 描述 + 图片 + 网格 5 列 + 居中

{% btns circle center grid5 %}
<a href='https://apps.apple.com/cn/app/heart-mate-pro-hrm-utility/id1463348922?ls=1'>
  <i class='fab fa-apple'></i>
  <b>心率管家</b>
  {% p red, 专业版 %}
  <img src='https://cdn.jsdelivr.net/gh/fomalhaut1998/cdn-assets/qrcode/heartmate_pro.png'>
</a>
<a href='https://apps.apple.com/cn/app/heart-mate-lite-hrm-utility/id1475747930?ls=1'>
  <i class='fab fa-apple'></i>
  <b>心率管家</b>
  {% p green, 免费版 %}
  <img src='https://cdn.jsdelivr.net/gh/fomalhaut1998/cdn-assets/qrcode/heartmate_lite.png'>
</a>
{% endbtns %}

<!-- endtab -->
{% endtabs %}

### 2.12 github 卡片 ghcard

{% tabs github 卡片ghcard %}
<!-- tab 标签语法  -->
```MARKDOWN
{% ghcard 用户名, 其它参数（可选） %}
{% ghcard 用户名/仓库, 其它参数（可选） %}
```
<!-- endtab -->

<!-- tab 配置参数 -->
使用 , 分割各个参数。写法为：参数名=参数值
以下只写几个常用参数值。

| 参数名| 取值 | 释义 |
|---------|--------|--------|
|hide | stars,commits,prs,issues,contribs	| 隐藏指定统计 |
|count_private|	true	|将私人项目贡献添加到总提交计数中 |
|show_icons	| true | 显示图标 |
|theme | 查阅:[Available Themes](https://github.com/anuraghazra/github-readme-stats/blob/master/themes/README.md) | 主题 |
<!-- endtab -->

<!-- tab 示例源码 -->
1. 用户信息卡片
```MARKDOWN
| {% ghcard xxxiuron %} | {% ghcard xxxiuron, theme=vue %} |
| -- | -- |
| {% ghcard xxxiuron, theme=buefy %} | {% ghcard xxxiuron, theme=solarized-light %} |
| {% ghcard xxxiuron, theme=onedark %} | {% ghcard xxxiuron, theme=solarized-dark %} |
| {% ghcard xxxiuron, theme=algolia %} | {% ghcard xxxiuron, theme=calm %} |
```
2. 仓库信息卡片
```MARKDOWN
| {% ghcard volantis-x/hexo-theme-volantis %} | {% ghcard volantis-x/hexo-theme-volantis, theme=vue %} |
| -- | -- |
| {% ghcard volantis-x/hexo-theme-volantis, theme=buefy %} | {% ghcard volantis-x/hexo-theme-volantis, theme=solarized-light %} |
| {% ghcard volantis-x/hexo-theme-volantis, theme=onedark %} | {% ghcard volantis-x/hexo-theme-volantis, theme=solarized-dark %} |
| {% ghcard volantis-x/hexo-theme-volantis, theme=algolia %} | {% ghcard volantis-x/hexo-theme-volantis, theme=calm %} |
```
<!-- endtab -->

<!-- tab 渲染演示 -->

| {% ghcard xxxiuron %} | {% ghcard xxxiuron, theme=vue %} |
| -- | -- |
| {% ghcard xxxiuron, theme=buefy %} | {% ghcard xxxiuron, theme=solarized-light %} |
| {% ghcard xxxiuron, theme=onedark %} | {% ghcard xxxiuron, theme=solarized-dark %} |
| {% ghcard xxxiuron, theme=algolia %} | {% ghcard xxxiuron, theme=calm %} |

2. 仓库信息卡片

| {% ghcard volantis-x/hexo-theme-volantis %} | {% ghcard volantis-x/hexo-theme-volantis, theme=vue %} |
| -- | -- |
| {% ghcard volantis-x/hexo-theme-volantis, theme=buefy %} | {% ghcard volantis-x/hexo-theme-volantis, theme=solarized-light %} |
| {% ghcard volantis-x/hexo-theme-volantis, theme=onedark %} | {% ghcard volantis-x/hexo-theme-volantis, theme=solarized-dark %} |
| {% ghcard volantis-x/hexo-theme-volantis, theme=algolia %} | {% ghcard volantis-x/hexo-theme-volantis, theme=calm %} |

<!-- endtab -->
{% endtabs %}

### 2.13 github 徽标 ghbdage

{% tabs 徽标ghbdage %}
<!-- tab 标签语法  -->
```MARKDOWN
{% bdage [right],[left],[logo]||[color],[link],[title]||[option] %}
```
<!-- endtab -->

<!-- tab 配置参数 -->
1. {% span red, left %}：徽标左边的信息，必选参数。
2. {% span red, right %}： 徽标右边的信息，必选参数，
3. {% span red, logo %}：徽标图标，图标名称详见 simpleicons，可选参数。
4. {% span red, color %}：徽标右边的颜色，可选参数。
5. {% span red, link %}：指向的链接，可选参数。
6. {% span red, title %}：徽标的额外信息，可选参数。主要用于优化 SEO，但 object 标签不会像 a 标签一样在鼠标悬停显示 title 信息。
7. {% span red, option %}：自定义参数，支持 shields.io 的全部 API 参数支持，具体参数可以参看上文中的拓展写法示例。形式为 name1=value2&name2=value2。

<!-- endtab -->

<!-- tab 示例源码 -->
1.基本参数，定义徽标左右文字和图标
```MARKDOWN
{% bdage Theme,Butterfly %}
{% bdage Frame,Hexo,hexo %}
```
2.信息参数，定义徽标右侧内容背景色，指向链接
```MARKDOWN
{% bdage CDN,JsDelivr,jsDelivr||abcdef,https://metroui.org.ua/index.html,本站使用JsDelivr为静态资源提供CDN加速 %}
//如果是跨顺序省略可选参数，仍然需要写个逗号,用作分割
{% bdage Source,GitHub,GitHub||,https://github.com/ %}
```
3.拓展参数，支持 shields 的 API 的全部参数内容
```MARKDOWN
{% bdage Hosted,Vercel,Vercel||brightgreen,https://vercel.com/,本站采用双线部署，默认线路托管于Vercel||style=social&logoWidth=20 %}
//如果是跨顺序省略可选参数组，仍然需要写双竖线||用作分割
{% bdage Hosted,Vercel,Vercel||||style=social&logoWidth=20&logoColor=violet %}
```
<!-- endtab -->

<!-- tab 渲染演示 -->
1.基本参数，定义徽标左右文字和图标

{% bdage Theme,Butterfly %}
{% bdage Frame,Hexo,hexo %}

2.信息参数，定义徽标右侧内容背景色，指向链接

{% bdage CDN,JsDelivr,jsDelivr||abcdef,https://metroui.org.ua/index.html,本站使用JsDelivr为静态资源提供CDN加速 %}
//如果是跨顺序省略可选参数，仍然需要写个逗号,用作分割
{% bdage Source,GitHub,GitHub||,https://github.com/ %}

3.拓展参数，支持 shields 的 API 的全部参数内容

{% bdage Hosted,Vercel,Vercel||brightgreen,https://vercel.com/,本站采用双线部署，默认线路托管于Vercel||style=social&logoWidth=20 %}
//如果是跨顺序省略可选参数组，仍然需要写双竖线||用作分割
{% bdage Hosted,Vercel,Vercel||||style=social&logoWidth=20&logoColor=violet %}

<!-- endtab -->
{% endtabs %}

### 2.14 网站卡片 sites

{% tabs 网站卡片sites %}
<!-- tab 标签语法  -->
```MARKDOWN
{% sitegroup %}
{% site 标题, url=链接, screenshot=截图链接, avatar=头像链接（可选）, description=描述（可选） %}
{% site 标题, url=链接, screenshot=截图链接, avatar=头像链接（可选）, description=描述（可选） %}
{% endsitegroup %}
```
<!-- endtab -->

<!-- tab 示例源码 -->
```MARKDOWN
{% sitegroup %}
{% site xaoxuu, url=https://xaoxuu.com, screenshot=https://i.loli.net/2020/08/21/VuSwWZ1xAeUHEBC.jpg, avatar=https://cdn.jsdelivr.net/gh/fomalhaut1998/cdn-assets/avatar/avatar.png, description=简约风格 %}
{% site inkss, url=https://inkss.cn, screenshot=https://i.loli.net/2020/08/21/Vzbu3i8fXs6Nh5Y.jpg, avatar=https://cdn.jsdelivr.net/gh/inkss/common@master/static/web/avatar.jpg, description=这是一段关于这个网站的描述文字 %}
{% site MHuiG, url=https://blog.mhuig.top, screenshot=https://i.loli.net/2020/08/22/d24zpPlhLYWX6D1.png, avatar=https://cdn.jsdelivr.net/gh/MHuiG/imgbed@master/data/p.png, description=这是一段关于这个网站的描述文字 %}
{% site Colsrch, url=https://colsrch.top, screenshot=https://i.loli.net/2020/08/22/dFRWXm52OVu8qfK.png, avatar=https://cdn.jsdelivr.net/gh/Colsrch/images/Colsrch/avatar.jpg, description=这是一段关于这个网站的描述文字 %}
{% site Linhk1606, url=https://linhk1606.github.io, screenshot=https://i.loli.net/2020/08/21/3PmGLCKicnfow1x.png, avatar=https://i.loli.net/2020/02/09/PN7I5RJfFtA93r2.png, description=这是一段关于这个网站的描述文字 %}
{% endsitegroup %}
```
<!-- endtab -->

<!-- tab 渲染演示 -->
{% sitegroup %}
{% site xaoxuu, url=https://xaoxuu.com, screenshot=https://i.loli.net/2020/08/21/VuSwWZ1xAeUHEBC.jpg, avatar=https://cdn.jsdelivr.net/gh/fomalhaut1998/cdn-assets/avatar/avatar.png, description=简约风格 %}
{% site inkss, url=https://inkss.cn, screenshot=https://i.loli.net/2020/08/21/Vzbu3i8fXs6Nh5Y.jpg, avatar=https://cdn.jsdelivr.net/gh/inkss/common@master/static/web/avatar.jpg, description=这是一段关于这个网站的描述文字 %}
{% site MHuiG, url=https://blog.mhuig.top, screenshot=https://i.loli.net/2020/08/22/d24zpPlhLYWX6D1.png, avatar=https://cdn.jsdelivr.net/gh/MHuiG/imgbed@master/data/p.png, description=这是一段关于这个网站的描述文字 %}
{% site Colsrch, url=https://colsrch.top, screenshot=https://i.loli.net/2020/08/22/dFRWXm52OVu8qfK.png, avatar=https://cdn.jsdelivr.net/gh/Colsrch/images/Colsrch/avatar.jpg, description=这是一段关于这个网站的描述文字 %}
{% site Linhk1606, url=https://linhk1606.github.io, screenshot=https://i.loli.net/2020/08/21/3PmGLCKicnfow1x.png, avatar=https://i.loli.net/2020/02/09/PN7I5RJfFtA93r2.png, description=这是一段关于这个网站的描述文字 %}
{% endsitegroup %}
<!-- endtab -->
{% endtabs %}

### 2.15 行内图片 inlineimage

{% tabs 行内图片inlineimage %}
<!-- tab 标签语法  -->
```MARKDOWN
{% inlineimage 图片链接, height=高度（可选） %}
```
<!-- endtab -->

<!-- tab 配置参数 -->
1. {% span red, 高度 %}：height=20px
<!-- endtab -->

<!-- tab 示例源码 -->
```MARKDOWN
这是 {% inlineimage https://cdn.jsdelivr.net/gh/volantis-x/cdn-emoji/aru-l/0000.gif %} 一段话。

这又是 {% inlineimage https://cdn.jsdelivr.net/gh/volantis-x/cdn-emoji/aru-l/5150.gif, height=40px %} 一段话。
```
<!-- endtab -->

<!-- tab 渲染演示 -->
这是 {% inlineimage https://cdn.jsdelivr.net/gh/volantis-x/cdn-emoji/aru-l/0000.gif %} 一段话。

这又是 {% inlineimage https://cdn.jsdelivr.net/gh/volantis-x/cdn-emoji/aru-l/5150.gif, height=40px %} 一段话。
<!-- endtab -->
{% endtabs %}

### 2.16 单张图片 image

{% tabs 单张图片image %}
<!-- tab 标签语法  -->
```MARKDOWN
{% image 链接, width=宽度（可选）, height=高度（可选）, alt=描述（可选）, bg=占位颜色（可选） %}
```
<!-- endtab -->

<!-- tab 配置参数 -->
1. {% span red, 图片宽度高度 %}：width=300px, height=32px
2. {% span red, 图片描述 %}：alt = 图片描述（butterfly 需要在主题配置文件中开启图片描述）
3. {% span red, 占位背景色 %}：bg=#f2f2f2
<!-- endtab -->

<!-- tab 示例源码 -->
1.添加描述：
```MARKDOWN
{% image https://cdn.jsdelivr.net/gh/volantis-x/cdn-wallpaper-minimalist/2020/025.jpg, alt=每天下课回宿舍的路，没有什么故事。 %}
```
2.指定宽度
```MARKDOWN
{% image https://cdn.jsdelivr.net/gh/volantis-x/cdn-wallpaper-minimalist/2020/025.jpg, width=400px %}
```
3.指定宽度并添加描述：
```MARKDOWN
{% image https://cdn.jsdelivr.net/gh/volantis-x/cdn-wallpaper-minimalist/2020/025.jpg, width=400px, alt=每天下课回宿舍的路，没有什么故事。 %}
```
4.设置占位背景色：
```MARKDOWN
{% image https://cdn.jsdelivr.net/gh/volantis-x/cdn-wallpaper-minimalist/2020/025.jpg, width=400px, bg=#1D0C04, alt=优化不同宽度浏览的观感 %}
```
<!-- endtab -->

<!-- tab 渲染演示 -->
1.添加描述：

{% image https://cdn.jsdelivr.net/gh/volantis-x/cdn-wallpaper-minimalist/2020/025.jpg, alt=每天下课回宿舍的路，没有什么故事。 %}

2.指定宽度

{% image https://cdn.jsdelivr.net/gh/volantis-x/cdn-wallpaper-minimalist/2020/025.jpg, width=400px %}

3.指定宽度并添加描述：

{% image https://cdn.jsdelivr.net/gh/volantis-x/cdn-wallpaper-minimalist/2020/025.jpg, width=400px, alt=每天下课回宿舍的路，没有什么故事。 %}

4.设置占位背景色：

{% image https://cdn.jsdelivr.net/gh/volantis-x/cdn-wallpaper-minimalist/2020/025.jpg, width=400px, bg=#1D0C04, alt=优化不同宽度浏览的观感 %}

<!-- endtab -->
{% endtabs %}

### 2.17 音频 audio

{% tabs 音频audio %}
<!-- tab 标签语法  -->
```MARKDOWN
{% audio 音频链接 %}
```
<!-- endtab -->

<!-- tab 示例源码 -->
```MARKDOWN
{% audio https://xxxiuron-music.oss-cn-chengdu.aliyuncs.com/Charlie%20Puth%20-%20See%20You%20Again%20%28Piano%20Demo%20Version%29.mp3 %}
```
<!-- endtab -->

<!-- tab 渲染演示 -->
{% audio https://xxxiuron-music.oss-cn-chengdu.aliyuncs.com/Charlie%20Puth%20-%20See%20You%20Again%20%28Piano%20Demo%20Version%29.mp3 %}
<!-- endtab -->
{% endtabs %}

### 2.18 视频 video

{% tabs 视频video %}
<!-- tab 标签语法  -->
```MARKDOWN
{% video 视频链接 %}
```
<!-- endtab -->

<!-- tab 配置参数 -->
1. {% span red ,对齐方向 %}：left, center, right
2. {% span red, 列数 %}：逗号后面直接写列数，支持 1 ～ 4 列。
<!-- endtab -->

<!-- tab 示例源码 -->
1.100% 宽度
```MARKDOWN
{% video https://github.com/volantis-x/volantis-docs/releases/download/assets/IMG_0341.mov %}
```
2.50% 宽度
```MARKDOWN
{% video https://github.com/volantis-x/volantis-docs/releases/download/assets/IMG_0341.mov %}
```
3.25% 宽度
```MARKDOWN
{% videos, 4 %}
{% video https://github.com/volantis-x/volantis-docs/releases/download/assets/IMG_0341.mov %}
{% video https://github.com/volantis-x/volantis-docs/releases/download/assets/IMG_0341.mov %}
{% video https://github.com/volantis-x/volantis-docs/releases/download/assets/IMG_0341.mov %}
{% video https://github.com/volantis-x/volantis-docs/releases/download/assets/IMG_0341.mov %}
{% video https://github.com/volantis-x/volantis-docs/releases/download/assets/IMG_0341.mov %}
{% video https://github.com/volantis-x/volantis-docs/releases/download/assets/IMG_0341.mov %}
{% video https://github.com/volantis-x/volantis-docs/releases/download/assets/IMG_0341.mov %}
{% video https://github.com/volantis-x/volantis-docs/releases/download/assets/IMG_0341.mov %}
{% endvideos %}
```
<!-- endtab -->

<!-- tab 渲染演示 -->
1.100% 宽度

{% video https://github.com/volantis-x/volantis-docs/releases/download/assets/IMG_0341.mov %}

2.50% 宽度

{% video https://github.com/volantis-x/volantis-docs/releases/download/assets/IMG_0341.mov %}

3.25% 宽度

{% videos, 4 %}
{% video https://github.com/volantis-x/volantis-docs/releases/download/assets/IMG_0341.mov %}
{% video https://github.com/volantis-x/volantis-docs/releases/download/assets/IMG_0341.mov %}
{% video https://github.com/volantis-x/volantis-docs/releases/download/assets/IMG_0341.mov %}
{% video https://github.com/volantis-x/volantis-docs/releases/download/assets/IMG_0341.mov %}
{% video https://github.com/volantis-x/volantis-docs/releases/download/assets/IMG_0341.mov %}
{% video https://github.com/volantis-x/volantis-docs/releases/download/assets/IMG_0341.mov %}
{% video https://github.com/volantis-x/volantis-docs/releases/download/assets/IMG_0341.mov %}
{% video https://github.com/volantis-x/volantis-docs/releases/download/assets/IMG_0341.mov %}
{% endvideos %}

<!-- endtab -->
{% endtabs %}

### 2.19 相册 gallery

{% tabs 相册gallery %}
<!-- tab 标签语法  -->
1.gallerygroup 相册图库
```MARKDOWN
<div class="gallery-group-main">
{% galleryGroup name description link img-url %}
{% galleryGroup name description link img-url %}
{% galleryGroup name description link img-url %}
</div>
```
2.gallery 相册
```MARKDOWN
{% gallery %}
markdown 圖片格式
{% endgallery %}
```

<!-- endtab -->

<!-- tab 配置参数 -->
* gallerygroup 相册图库

|参数名|	释义|
|---|---|
|name	|图库名字|
|description	|图库描述|
|link	|链接到对应相册的地址|
|img-url	|图库封面|

* gallery 相册

区别于旧版的 Gallery 相册，新的 Gallery 相册会自动根据图片长度进行排版，书写也更加方便，与 markdown 格式一样。可根据需要插入到相应的 md。无需再自己配置长宽。建议在粘贴时故意使用长短、大小、横竖不一的图片，会有更好的效果。（尺寸完全相同的图片只会平铺输出，效果很糟糕）
<!-- endtab -->

<!-- tab 示例源码 -->
1.gallerygroup 相册图库
```MARKDOWN
<div class="gallery-group-main">
{% galleryGroup MC 在Rikkaの六花服务器里留下的足迹 '/gallery/MC/' https://cdn.cbd.int/akilar-candyassets@1.0.36/image/1.jpg %}
{% galleryGroup Gundam 哦咧哇gundam哒！ '/gallery/Gundam/' https://cdn.cbd.int/akilar-candyassets@1.0.36/image/20200907110508327.png %}
{% galleryGroup I-am-Akilar 某种意义上也算自拍吧 '/gallery/I-am-Akilar/' https://cdn.cbd.int/akilar-candyassets@1.0.36/image/20200907113116651.png %}
</div>
```
2.gallery 相册
```MARKDOWN
{% gallery %}
![](https://i.loli.net/2019/12/25/Fze9jchtnyJXMHN.jpg)
![](https://i.loli.net/2019/12/25/ryLVePaqkYm4TEK.jpg)
{% endgallery %}
```
<!-- endtab -->

<!-- tab 渲染演示 -->
1.gallerygroup 相册图库

<div class="gallery-group-main">
{% galleryGroup MC 在Rikkaの六花服务器里留下的足迹 '/gallery/MC/' https://cdn.cbd.int/akilar-candyassets@1.0.36/image/1.jpg %}
{% galleryGroup Gundam 哦咧哇gundam哒！ '/gallery/Gundam/' https://cdn.cbd.int/akilar-candyassets@1.0.36/image/20200907110508327.png %}
{% galleryGroup I-am-Akilar 某种意义上也算自拍吧 '/gallery/I-am-Akilar/' https://cdn.cbd.int/akilar-candyassets@1.0.36/image/20200907113116651.png %}
</div>

2.gallery 相册

{% gallery %}
![](https://i.loli.net/2019/12/25/Fze9jchtnyJXMHN.jpg)
![](https://i.loli.net/2019/12/25/ryLVePaqkYm4TEK.jpg)
{% endgallery %}

<!-- endtab -->
{% endtabs %}

### 2.20 折叠框 folding

{% tabs 折叠框folding %}
<!-- tab 标签语法  -->
```MARKDOWN
{% folding 参数（可选）, 标题 %}
```
<!-- endtab -->

<!-- tab 配置参数 -->
1. {% span red, 颜色 %}：blue, cyan, green, yellow, red

2. {% span red, 状态 %}：状态填写 open 代表默认打开。
<!-- endtab -->

<!-- tab 示例源码 -->
```MARKDOWN
{% folding 查看图片测试 %}

![](https://cdn.jsdelivr.net/gh/volantis-x/cdn-wallpaper/abstract/41F215B9-261F-48B4-80B5-4E86E165259E.jpeg)

{% endfolding %}

{% folding cyan open, 查看默认打开的折叠框 %}

这是一个默认打开的折叠框。

{% endfolding %}

{% folding green, 查看代码测试 %}
假装这里有代码块（代码块没法嵌套代码块）
{% endfolding %}

{% folding yellow, 查看列表测试 %}

- haha
- hehe

{% endfolding %}

{% folding red, 查看嵌套测试 %}

{% folding blue, 查看嵌套测试2 %}

{% folding 查看嵌套测试3 %}

hahaha <span><img src='https://cdn.jsdelivr.net/gh/volantis-x/cdn-emoji/tieba/%E6%BB%91%E7%A8%BD.png' style='height:24px'></span>

{% endfolding %}

{% endfolding %}

{% endfolding %}
```
<!-- endtab -->

<!-- tab 渲染演示 -->
{% folding 查看图片测试 %}

![](https://cdn.jsdelivr.net/gh/volantis-x/cdn-wallpaper/abstract/41F215B9-261F-48B4-80B5-4E86E165259E.jpeg)

{% endfolding %}

{% folding cyan open, 查看默认打开的折叠框 %}

这是一个默认打开的折叠框。

{% endfolding %}

{% folding green, 查看代码测试 %}
假装这里有代码块（代码块没法嵌套代码块）
{% endfolding %}

{% folding yellow, 查看列表测试 %}

- haha
- hehe

{% endfolding %}

{% folding red, 查看嵌套测试 %}

{% folding blue, 查看嵌套测试2 %}

{% folding 查看嵌套测试3 %}

hahaha <span><img src='https://cdn.jsdelivr.net/gh/volantis-x/cdn-emoji/tieba/%E6%BB%91%E7%A8%BD.png' style='height:24px'></span>

{% endfolding %}

{% endfolding %}

{% endfolding %}
<!-- endtab -->
{% endtabs %}

### 2.21 分栏 tab

{% tabs 分栏tab %}
<!-- tab 标签语法  -->
```MARKDOWN
{% tabs Unique name, [index] %}
<!-- tab [Tab caption] [@icon] -->
Any content (support inline tags too).
<!-- endtab -->
{% endtabs %}
```
<!-- endtab -->

<!-- tab 配置参数 -->
1. Unique name :

* 选项卡块标签的唯一名称，不带逗号。

* 将在 #id 中用作每个标签及其索引号的前缀。

* 如果名称中包含空格，则对于生成 #id，所有空格将由破折号代替。

* 仅当前帖子 / 页面的 URL 必须是唯一的！

2. [index]:

* 活动选项卡的索引号。

* 如果未指定，将选择第一个标签（1）。

* 如果 index 为 - 1，则不会选择任何选项卡。

* 可选参数。

3. [Tab caption]:

* 当前选项卡的标题。

* 如果未指定标题，则带有制表符索引后缀的唯一名称将用作制表符的标题。

* 如果未指定标题，但指定了图标，则标题将为空。

* 可选参数。

4. [@icon]:

* FontAwesome 图标名称（全名，看起来像 “fas fa-font”）

* 可以指定带空格或不带空格；

* 例如’Tab caption @icon’ 和 ‘Tab caption@icon’.

* 可选参数。
<!-- endtab -->

<!-- tab 示例源码 -->
1.Demo 1 - 预设选择第一个【默认】
```MARKDOWN
{% tabs test1 %}
<!-- tab -->
**This is Tab 1.**
<!-- endtab -->

<!-- tab -->
**This is Tab 2.**
<!-- endtab -->

<!-- tab -->
**This is Tab 3.**
<!-- endtab -->
{% endtabs %}
```
2.Demo 2 - 预设选择 tabs
```MARKDOWN
{% tabs test2, 3 %}
<!-- tab -->
**This is Tab 1.**
<!-- endtab -->

<!-- tab -->
**This is Tab 2.**
<!-- endtab -->

<!-- tab -->
**This is Tab 3.**
<!-- endtab -->
{% endtabs %}
```
3.Demo 3 - 没有预设值
```MARKDOWN
{% tabs test3, -1 %}
<!-- tab -->
**This is Tab 1.**
<!-- endtab -->

<!-- tab -->
**This is Tab 2.**
<!-- endtab -->

<!-- tab -->
**This is Tab 3.**
<!-- endtab -->
{% endtabs %}
```
4.Demo 4 - 自定义 Tab 名 + 只有 icon + icon 和 Tab 名
```MARKDOWN
{% tabs test4 %}
<!-- tab 第一个Tab -->
**tab名字为第一个Tab**
<!-- endtab -->

<!-- tab @fab fa-apple-pay -->
**只有图标 没有Tab名字**
<!-- endtab -->

<!-- tab 炸弹@fas fa-bomb -->
**名字+icon**
<!-- endtab -->
{% endtabs %}
```
<!-- endtab -->

<!-- tab 渲染演示 -->
1.Demo 1 - 预设选择第一个【默认】

{% tabs test1 %}
<!-- tab -->
**This is Tab 1.**
<!-- endtab -->

<!-- tab -->
**This is Tab 2.**
<!-- endtab -->

<!-- tab -->
**This is Tab 3.**
<!-- endtab -->
{% endtabs %}

2.Demo 2 - 预设选择 tabs

{% tabs test2, 3 %}
<!-- tab -->
**This is Tab 1.**
<!-- endtab -->

<!-- tab -->
**This is Tab 2.**
<!-- endtab -->

<!-- tab -->
**This is Tab 3.**
<!-- endtab -->
{% endtabs %}

3.Demo 3 - 没有预设值

{% tabs test3, -1 %}
<!-- tab -->
**This is Tab 1.**
<!-- endtab -->

<!-- tab -->
**This is Tab 2.**
<!-- endtab -->

<!-- tab -->
**This is Tab 3.**
<!-- endtab -->
{% endtabs %}

4.Demo 4 - 自定义 Tab 名 + 只有 icon + icon 和 Tab 名

{% tabs test4 %}
<!-- tab 第一个Tab -->
**tab名字为第一个Tab**
<!-- endtab -->

<!-- tab @fab fa-apple-pay -->
**只有图标 没有Tab名字**
<!-- endtab -->

<!-- tab 炸弹@fas fa-bomb -->
**名字+icon**
<!-- endtab -->
{% endtabs %}

<!-- endtab -->
{% endtabs %}

### 2.22 诗词标签 poem

{% tabs 诗词标签poem %}

<!-- tab 配置参数 -->
1. {% span red, title %}：诗词标题
2. {% span red, author %}：作者，可以不写
<!-- endtab -->

<!-- tab 示例源码 -->
```MARKDOWN
{% poem 水调歌头,苏轼 %}
丙辰中秋，欢饮达旦，大醉，作此篇，兼怀子由。
明月几时有？把酒问青天。
不知天上宫阙，今夕是何年？
我欲乘风归去，又恐琼楼玉宇，高处不胜寒。
起舞弄清影，何似在人间？

转朱阁，低绮户，照无眠。
不应有恨，何事长向别时圆？
人有悲欢离合，月有阴晴圆缺，此事古难全。
但愿人长久，千里共婵娟。
{% endpoem %}
```
<!-- endtab -->

<!-- tab 渲染演示 -->
{% poem 水调歌头,苏轼 %}
丙辰中秋，欢饮达旦，大醉，作此篇，兼怀子由。
明月几时有？把酒问青天。
不知天上宫阙，今夕是何年？
我欲乘风归去，又恐琼楼玉宇，高处不胜寒。
起舞弄清影，何似在人间？

转朱阁，低绮户，照无眠。
不应有恨，何事长向别时圆？
人有悲欢离合，月有阴晴圆缺，此事古难全。
但愿人长久，千里共婵娟。
{% endpoem %}
<!-- endtab -->
{% endtabs %}

### 2.23 阿里图标 icon

{% tabs 阿里图标icon %}
<!-- tab 标签语法  -->
```MARKDOWN
{% icon [icon-xxxx],[font-size] %}
```
<!-- endtab -->

<!-- tab 配置参数 -->
1. {% span red, icon-xxxx %}：表示图标 font-class, 可以在自己的阿里矢量图标库项目的 font-class 引用方案内查询并复制。
2. {% span red, font-size %}：表示图标大小，直接填写数字即可，单位为 em。图标大小默认值为 1em。

<!-- endtab -->

<!-- tab 示例源码 -->
```MARKDOWN
{% icon icon-rat_zi %}{% icon icon-rat,2 %}

{% icon icon-ox_chou,3 %}{% icon icon-ox,4 %}

{% icon icon-tiger_yin,5 %}{% icon icon-tiger,6 %}

{% icon icon-rabbit_mao,1 %}{% icon icon-rabbit,2 %}

{% icon icon-dragon_chen,3 %}{% icon icon-dragon,4 %}

{% icon icon-snake_si,5 %}{% icon icon-snake,6 %}

{% icon icon-horse_wu %}{% icon icon-horse,2 %}

{% icon icon-goat_wei,3 %}{% icon icon-goat,4 %}

{% icon icon-monkey_shen,5 %}{% icon icon-monkey,6 %}

{% icon icon-rooster_you %}{% icon icon-rooster,2 %}

{% icon icon-dog_xu,3 %}{% icon icon-dog,4 %}

{% icon icon-boar_hai,5 %}{% icon icon-boar,6 %}
```
<!-- endtab -->

<!-- tab 渲染演示 -->
{% icon icon-rat_zi %}{% icon icon-rat,2 %}

{% icon icon-ox_chou,3 %}{% icon icon-ox,4 %}

{% icon icon-tiger_yin,5 %}{% icon icon-tiger,6 %}

{% icon icon-rabbit_mao,1 %}{% icon icon-rabbit,2 %}

{% icon icon-dragon_chen,3 %}{% icon icon-dragon,4 %}

{% icon icon-snake_si,5 %}{% icon icon-snake,6 %}

{% icon icon-horse_wu %}{% icon icon-horse,2 %}

{% icon icon-goat_wei,3 %}{% icon icon-goat,4 %}

{% icon icon-monkey_shen,5 %}{% icon icon-monkey,6 %}

{% icon icon-rooster_you %}{% icon icon-rooster,2 %}

{% icon icon-dog_xu,3 %}{% icon icon-dog,4 %}

{% icon icon-boar_hai,5 %}{% icon icon-boar,6 %}
<!-- endtab -->
{% endtabs %}

### 2.24 特效标签 wow

{% tabs 特效标签wow %}
<!-- tab 标签语法  -->
```MARKDOWN
{% wow [animete],[duration],[delay],[offset],[iteration] %}
内容
{% endwow %}
```
<!-- endtab -->

<!-- tab 配置参数 -->
1. {% span red, animate %}: 动画样式，效果详见 animate.css 参考文档
2. {% span red, duration %}: 选填项，动画持续时间，单位可以是 ms 也可以是 s。例如 3s，700ms。
3. {% span red, delay %}: 选填项，动画开始的延迟时间，单位可以是 ms 也可以是 s。例如 3s，700ms。
4. {% span red, offse %}t: 选填项，开始动画的距离（相对浏览器底部）
5. {% span red, iteration %}: 选填项，动画重复的次数
<!-- endtab -->

<!-- tab 示例源码 -->
1.flip 动画效果。
```MARKDOWN
{% wow animate__flip %}
{% note green 'fas fa-fan' modern%}
`flip`动画效果。
{% endnote %}
{% endwow %}
```
2.zoomIn 动画效果，持续 5s，延时 5s，离底部 100 距离时启动，重复 10 次
```MARKDOWN
{% wow animate__zoomIn,5s,5s,100,10 %}
{% note blue 'fas fa-bullhorn' modern%}
`zoomIn`动画效果，持续`5s`，延时`5s`，离底部`100`距离时启动，重复`10`次
{% endnote %}
{% endwow %}
```
3.slideInRight 动画效果，持续 5s，延时 5s
```MARKDOWN
{% wow animate__slideInRight,5s,5s %}
{% note orange 'fas fa-car' modern%}
`slideInRight`动画效果，持续`5s`，延时`5s`。
{% endnote %}
{% endwow %}
```
4.heartBeat 动画效果，延时 5s，重复 10 次。此处注意不用的参数位置要留空，用逗号间隔。
```MARKDOWN
{% wow animate__heartBeat,,5s,,10 %}
{% note red 'fas fa-battery-half' modern%}
`heartBeat`动画效果，延时`5s`，重复`10`次。
{% endnote %}
{% endwow %}
```
<!-- endtab -->

<!-- tab 渲染演示 -->
1.flip 动画效果。

{% wow animate__flip %}
{% note green 'fas fa-fan' modern%}
`flip`动画效果。
{% endnote %}
{% endwow %}

2.zoomIn 动画效果，持续 5s，延时 5s，离底部 100 距离时启动，重复 10 次

{% wow animate__zoomIn,5s,5s,100,10 %}
{% note blue 'fas fa-bullhorn' modern %}
`zoomIn`动画效果，持续`5s`，延时`5s`，离底部`100`距离时启动，重复`10`次
{% endnote %}
{% endwow %}

3.slideInRight 动画效果，持续 5s，延时 5s

{% wow animate__slideInRight,5s,5s %}
{% note orange 'fas fa-car' modern %}
`slideInRight`动画效果，持续`5s`，延时`5s`。
{% endnote %}
{% endwow %}

4.heartBeat 动画效果，延时 5s，重复 10 次。此处注意不用的参数位置要留空，用逗号间隔。

{% wow animate__heartBeat,,5s,,10 %}
{% note red 'fas fa-battery-half' modern %}
`heartBeat`动画效果，延时`5s`，重复`10`次。
{% endnote %}
{% endwow %}

<!-- endtab -->
{% endtabs %}

### 2.25 进度条 progress

{% tabs 进度条progress %}
<!-- tab 标签语法  -->
```MARKDOWN
{% progress [width] [color] [text] %}
```
<!-- endtab -->

<!-- tab 配置参数 -->
1. {% span red ,width %}: 0 到 100 的阿拉伯数字
2. {% span red ,color %}: 颜色，取值有 red,yellow,green,cyan,blue,gray
3. {% span red, text %}: 进度条上的文字内容
<!-- endtab -->

<!-- tab 示例源码 -->
```MARKDOWN
{% progress 10 red 进度条样式预览 %}
{% progress 30 yellow 进度条样式预览 %}
{% progress 50 green 进度条样式预览 %}
{% progress 70 cyan 进度条样式预览 %}
{% progress 90 blue 进度条样式预览 %}
{% progress 100 gray 进度条样式预览 %}
```
<!-- endtab -->

<!-- tab 渲染演示 -->
{% progress 10 red 进度条样式预览 %}
{% progress 30 yellow 进度条样式预览 %}
{% progress 50 green 进度条样式预览 %}
{% progress 70 cyan 进度条样式预览 %}
{% progress 90 blue 进度条样式预览 %}
{% progress 100 gray 进度条样式预览 %}
<!-- endtab -->
{% endtabs %}

### 2.26 注释 notation

{% tabs 注释notation %}
<!-- tab 标签语法  -->
```MARKDOWN
{% nota [label] , [text] %}
```
<!-- endtab -->

<!-- tab 配置参数 -->
1. {% span red, label %}: 注释词汇

2. {% span red, text %}: 悬停显示的注解内容
<!-- endtab -->

<!-- tab 示例源码 -->
```MARKDOWN
{% nota 把鼠标移动到我上面试试 ,可以看到注解内容出现在顶栏 %}
```
<!-- endtab -->

<!-- tab 渲染演示 -->
{% nota 把鼠标移动到我上面试试 ,可以看到注解内容出现在顶栏 %}
<!-- endtab -->
{% endtabs %}

### 2.27 气泡注释 bubble

{% tabs 气泡注释bubble %}
<!-- tab 标签语法  -->
```MARKDOWN
{% bubble [content] , [notation] ,[background-color] %}
```
<!-- endtab -->

<!-- tab 配置参数 -->
1. {% span red ,content %}: 注释词汇
2. {% span red ,notation %}: 悬停显示的注解内容
3. {% span red ,background-color %}: 可选，气泡背景色。默认为 “#71a4e3”
<!-- endtab -->

<!-- tab 示例源码 -->
```MARKDOWN
最近我学到了不少新玩意儿（虽然对很多大佬来说这些已经是旧技术了），比如CSS的{% bubble 兄弟相邻选择器,"例如 h1 + p {margin-top:50px;}" %}，{% bubble flex布局,"Flex 是 Flexible Box 的缩写，意为"弹性布局"，用来为盒状模型提供最大的灵活性","#ec5830" %}，{% bubble transform变换,"transform 属性向元素应用 2D 或 3D 转换。该属性允许我们对元素进行旋转、缩放、移动或倾斜。","#1db675" %}，animation的{% bubble 贝塞尔速度曲线,"贝塞尔曲线(Bézier curve)，又称贝兹曲线或贝济埃曲线，是应用于二维图形应用程序的数学曲线。一般的矢量图形软件通过它来精确画出曲线，贝兹曲线由线段与节点组成，节点是可拖动的支点，线段像可伸缩的皮筋","#de4489" %}写法，还有今天刚看到的{% bubble clip-path,"clip-path属性使用裁剪方式创建元素的可显示区域。区域内的部分显示，区域外的隐藏。","#868fd7" %}属性。这些对我来说很新颖的概念狠狠的冲击着我以前积累起来的设计思路。
```
<!-- endtab -->

<!-- tab 渲染演示 -->
最近我学到了不少新玩意儿（虽然对很多大佬来说这些已经是旧技术了），比如CSS的{% bubble 兄弟相邻选择器,"例如 h1 + p {margin-top:50px;}" %}，{% bubble flex布局,"Flex 是 Flexible Box 的缩写，意为"弹性布局"，用来为盒状模型提供最大的灵活性","#ec5830" %}，{% bubble transform变换,"transform 属性向元素应用 2D 或 3D 转换。该属性允许我们对元素进行旋转、缩放、移动或倾斜。","#1db675" %}，animation的{% bubble 贝塞尔速度曲线,"贝塞尔曲线(Bézier curve)，又称贝兹曲线或贝济埃曲线，是应用于二维图形应用程序的数学曲线。一般的矢量图形软件通过它来精确画出曲线，贝兹曲线由线段与节点组成，节点是可拖动的支点，线段像可伸缩的皮筋","#de4489" %}写法，还有今天刚看到的{% bubble clip-path,"clip-path属性使用裁剪方式创建元素的可显示区域。区域内的部分显示，区域外的隐藏。","#868fd7" %}属性。这些对我来说很新颖的概念狠狠的冲击着我以前积累起来的设计思路。
<!-- endtab -->
{% endtabs %}

### 2.28 引用文献 reference

{% tabs 引用文献reference %}
<!-- tab 标签语法  -->
```MARKDOWN
{% referto [id] , [literature] %}
{% referfrom [id] , [literature] , [url] %}
```
<!-- endtab -->

<!-- tab 配置参数 -->
1. referto 引用上标

* id: 上标序号内容，需与 referfrom 标签的 id 对应才能实现跳转

* literature: 引用的参考文献名称

2. referfrom 引用出处

* id: 序号内容，需与 referto 标签的 id 对应才能实现 跳转

* literature: 引用的参考文献名称

* url: 引用的参考文献链接，可省略


<!-- endtab -->

<!-- tab 示例源码 -->
```MARKDOWN
Akilarの糖果屋(akilar.top)是一个私人性质的博客{% referto '[1]','Akilarの糖果屋群聊简介' %}，从各类教程至生活点滴，无话不谈。建群的目的是提供一个闲聊的场所。博客采用Hexo框架{% referto '[2]','Hexo中文文档' %}，Butterfly主题{% referto '[3]','Butterfly 安装文档(一) 快速开始' %}

本项目参考了Volantis{% referto '[4]','hexo-theme-volantis 标签插件' %}的标签样式。引入`[tag].js`，并针对`butterfly`主题修改了相应的`[tag].styl`。在此鸣谢`Volantis`主题众开发者。
主要参考内容包括各个volantis的内置标签插件文档{% referto '[5]','Volantis文档:内置标签插件' %}
Butterfly主题的各个衍生魔改{% referto '[6]','Butterfly 安装文档:标签外挂（Tag Plugins' %}{% referto '[7]','小弋の生活馆全样式预览' %}{% referto '[8]','l-lin-font-awesome-animation' %}{% referto '[9]','小康的butterfly主题使用文档' %}

{% referfrom '[1]','Akilarの糖果屋群聊简介','https://jq.qq.com/?_wv=1027&k=pGLB2C0N' %}
{% referfrom '[2]','Hexo中文文档','https://hexo.io/zh-cn/docs/' %}
{% referfrom '[3]','Butterfly 安装文档(一) 快速开始','https://butterfly.js.org/posts/21cfbf15/' %}
{% referfrom '[4]','hexo-theme-volantis 标签插件','https://volantis.js.org/v5/tag-plugins/' %}
{% referfrom '[5]','Volantis文档:内置标签插件','https://volantis.js.org/tag-plugins/' %}
{% referfrom '[6]','Butterfly 安装文档:标签外挂（Tag Plugins','https://butterfly.js.org/posts/4aa8abbe/#%E6%A8%99%E7%B1%A4%E5%A4%96%E6%8E%9B%EF%BC%88Tag-Plugins%EF%BC%89' %}
{% referfrom '[7]','小弋の生活馆全样式预览','https://lovelijunyi.gitee.io/posts/c898.html' %}
{% referfrom '[8]','l-lin-font-awesome-animation','https://github.com/l-lin/font-awesome-animation' %}
{% referfrom '[9]','小康的butterfly主题使用文档','https://www.antmoe.com/posts/3b43914f/' %}
```
<!-- endtab -->

<!-- tab 渲染演示 -->
Akilarの糖果屋(akilar.top)是一个私人性质的博客{% referto '[1]','Akilarの糖果屋群聊简介' %}，从各类教程至生活点滴，无话不谈。建群的目的是提供一个闲聊的场所。博客采用Hexo框架{% referto '[2]','Hexo中文文档' %}，Butterfly主题{% referto '[3]','Butterfly 安装文档(一) 快速开始' %}

本项目参考了Volantis{% referto '[4]','hexo-theme-volantis 标签插件' %}的标签样式。引入`[tag].js`，并针对`butterfly`主题修改了相应的`[tag].styl`。在此鸣谢`Volantis`主题众开发者。
主要参考内容包括各个volantis的内置标签插件文档{% referto '[5]','Volantis文档:内置标签插件' %}
Butterfly主题的各个衍生魔改{% referto '[6]','Butterfly 安装文档:标签外挂（Tag Plugins' %}{% referto '[7]','小弋の生活馆全样式预览' %}{% referto '[8]','l-lin-font-awesome-animation' %}{% referto '[9]','小康的butterfly主题使用文档' %}

{% referfrom '[1]','Akilarの糖果屋群聊简介','https://jq.qq.com/?_wv=1027&k=pGLB2C0N' %}
{% referfrom '[2]','Hexo中文文档','https://hexo.io/zh-cn/docs/' %}
{% referfrom '[3]','Butterfly 安装文档(一) 快速开始','https://butterfly.js.org/posts/21cfbf15/' %}
{% referfrom '[4]','hexo-theme-volantis 标签插件','https://volantis.js.org/v5/tag-plugins/' %}
{% referfrom '[5]','Volantis文档:内置标签插件','https://volantis.js.org/tag-plugins/' %}
{% referfrom '[6]','Butterfly 安装文档:标签外挂（Tag Plugins','https://butterfly.js.org/posts/4aa8abbe/#%E6%A8%99%E7%B1%A4%E5%A4%96%E6%8E%9B%EF%BC%88Tag-Plugins%EF%BC%89' %}
{% referfrom '[7]','小弋の生活馆全样式预览','https://lovelijunyi.gitee.io/posts/c898.html' %}
{% referfrom '[8]','l-lin-font-awesome-animation','https://github.com/l-lin/font-awesome-animation' %}
{% referfrom '[9]','小康的butterfly主题使用文档','https://www.antmoe.com/posts/3b43914f/' %}
<!-- endtab -->
{% endtabs %}

###  2.29 PDF 展示

{% tabs PDF展示 %}
<!-- tab 标签语法  -->
```MARKDOWN
{% pdf 文件路径 %}
```
<!-- endtab -->

<!-- tab 配置参数 -->
1. {% span red ,文件路径 %}: 可以是相对路径或者是在线链接
<!-- endtab -->

<!-- tab 示例源码 -->
```MARKDOWN
# 1.本地文件:在md文件路径下创建一个同名文件夹，其内放pdf文件名为xxx.pdf的文件
{% pdf xxx.pdf %}
# 2.在线链接
{% pdf https://cdn.jsdelivr.net/gh/Justlovesmile/CDN/pdf/小作文讲义.pdf %}
```
<!-- endtab -->

<!-- tab 渲染演示 -->
2. 在线链接 (要放到最外层才能起作用)
{% pdf https://cdn.jsdelivr.net/gh/Justlovesmile/CDN/pdf/小作文讲义.pdf %}
<!-- endtab -->
{% endtabs %}

### 2.30 Hexo-tag-map 插件

{% tabs Hexo-tag-map %}
<!-- tab 标签语法  -->
```MARKDOWN
{% + 标签值 + 经度 + 纬度 + 文本 + 缩放等级 + 宽 + 高 + 默认图层 + %}
```
<!-- endtab -->

<!-- tab 配置参数 -->
|地图名	|标签值 <必填>	|宽 (默认 100%) / 高 (默认 360px)	|缩放等级 (默认 14)	|宽 (默认 100%) / 高 (默认 360px)	|默认图层 (默认 1)|
|---|---|---|---|---|---|
|混合地图|map	|百分数或具体值 (100% 或 360px)	|取值 3~18|	百分数或具体值 (100% 或 360px)	|取值 1~7|
|谷歌地图|googleMap	|百分数或具体值 (100% 或 360px)	|取值 1~20	|百分数或具体值 (100% 或 360px)	|取值 1~3|
|高德地图|gaodeMap	|百分数或具体值 (100% 或 360px)	|取值 3~18	|百分数或具体值 (100% 或 360px)	|取值 1~3|
|百度地图|baiduMap	|百分数或具体值 (100% 或 360px)	|取值 4~18	|百分数或具体值 (100% 或 360px)	|取值 1~2|
|Geoq 地图|geoqMap	|百分数或具体值 (100% 或 360px)	|取值 1~18|	百分数或具体值 (100% 或 360px)	|取值 1~5|
|openstreet 地图|openstreetMap	|百分数或具体值 (100% 或 360px)	|取值 1~18	|百分数或具体值 (100% 或 360px)	|不支持此参数|

1. 参数之间，用英文逗号相隔
2. 参数必须按上述事例顺序输入，不得为空
3. 同一个页面，同一组经纬度值，只能插入一个相同标签值的地图 (若有需要，可以将第二个地图上，经度或纬度末尾删除一两个数)
4. 参数取值必须在上述范围内
5. 默认图层：即地图叠加层的值，默认常规地图还是卫星地图，可按地图显示顺序取值
6. 缩放等级，数字越大，地图比例尺越小，显示的越精细
7. 除标签值外，其他参数选填，但 每个参数的左边的参数必填
8. 谷歌地图需要外网才能加载查看

坐标获取：[高德地图坐标拾取系统](https://lbs.amap.com/tools/picker) 、[百度地图坐标拾取系统](https://api.map.baidu.com/lbsapi/getpoint/index.html)
<!-- endtab -->

<!-- tab 示例源码 -->
```MARKDOWN
{% map 120.101101,30.239119 %}
{% googleMap 120.101101,30.239119, 这里是西湖灵隐寺，据说求姻缘很灵验哦！ %}
{% geoqMap 120.101101,30.239119, 这里是西湖灵隐寺，据说求姻缘很灵验哦！, 13, 90%, 320px, 3 %}
```
<!-- endtab -->

<!-- tab 渲染演示 -->
{% map 120.101101,30.239119 %}
{% googleMap 120.101101,30.239119, 这里是西湖灵隐寺，据说求姻缘很灵验哦！ %}
{% geoqMap 120.101101,30.239119, 这里是西湖灵隐寺，据说求姻缘很灵验哦！, 13, 90%, 320px, 3 %}
<!-- endtab -->
{% endtabs %}

### 2.31 隐藏块

{% tabs 隐藏块 %}
<!-- tab 标签语法  -->
```MARKDOWN
{% hideBlock display,bg,color %}
content
{% endhideBlock %}
```
<!-- endtab -->

<!-- tab 配置参数 -->
1. {% span red ,content %}：要隐藏的内容
2. {% span red ,display %}：展示前按钮显示的文字（可选）
3. {% span red ,bg %}：按钮的背景颜色（可选）
4. {% span red,color %}：按钮显示的文字的颜色（可选）
<!-- endtab -->

<!-- tab 示例源码 -->
```MARKDOWN
{% hideBlock 点我预览, blue %}
这里有张图片：
<img src="https://s1.vika.cn/space/2022/10/30/b35fce448bc9404a8d65c3ce1e6e46eb" alt="image (1)" style="zoom:67%;" />
{% endhideBlock %}
```
<!-- endtab -->

<!-- tab 渲染演示 -->
{% hideBlock 点我预览, blue %}
这里有张图片：
<img src="https://s1.vika.cn/space/2022/10/30/b35fce448bc9404a8d65c3ce1e6e46eb" alt="image (1)" style="zoom:67%;" />
{% endhideBlock %}
<!-- endtab -->
{% endtabs %}