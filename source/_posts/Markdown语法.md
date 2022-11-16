---
title: Markdown语法
date: 2022-11-15 20:00:00
updated: 2022-11-15 20:00:00
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
|theme | 查阅:Available Themes | 主题 |
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

<!-- endtab -->
{% endtabs %}
