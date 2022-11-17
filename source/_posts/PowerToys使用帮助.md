---
title: PowerToys使用帮助
date: 2022-11-17 12:30:00
updated: 2022-11-17 12:30:00
tag: 
    -   tools
    -   help
---
{% note warning flat %}文章仅作为本人使用时帮助{% endnote %}
[Windows PowerToys](https://learn.microsoft.com/en-us/windows/powertoys/): 
 {% ghcard microsoft/PowerToys, theme=algolia %}
 ## 0. 安装
 下载相关地址: https://learn.microsoft.com/en-us/windows/powertoys/install
 {% note info flat %}无需下载，直接执行下面步骤即可{% endnote %}

 使用{% span red, Windows PowerShell %}执行:

 ```POWERSHELL
 winget install Microsoft.PowerToys --source winget
 ```

 ## 1. 常规

备份目录：<font color=#49b1f5>**D:\PowerToys**</font>
设置 **开机启动**和**管理员运行**

## 2. 始终置顶

"始终置顶" 是一种可将窗囗固定在顶部的快捷方法 。

1. {% span red ,激活快捷键 %}: {% kbd windows %} + {% kbd Ctrl %} + {% kbd T %}
2. {% span red ,边框设置 %}: 粗细 3px
3. {% span red ,声音设置 %}: 关闭**固定窗口时播放声音**

## 3. 唤醒
* {% span green h3 ,关闭功能 %}

## 4. 颜色选择器
快速、筒单的系统范围颜色选择器。

1. {% span red ,激活快捷键 %}: {% kbd windows %} + {% kbd Shift %} + {% kbd C %}
2. {% span red ,默认格式 %}: HEX - ffaa00
3. {% span red ,颜色各式 %}: HEX RGB HSL