---
date: 2014-02-22 01:42:00+00:00
layout: post
title: 学而时习之，不亦乐乎
categories: BLOG
tags:  BLOG
---

## 学而时习之，不亦乐乎

开始用 Markdown 写东西。不再纠结于 Office 软件的排版。专心用文字记录下数学学习中的点点滴滴。

本博客运行于 [Jekyll](http://jekyllrb.com) @ [GitHub](http://github.com/ccpaging)，博客模板修改自：

[Yonsm.NET](http://www.yonsm.net) 以及 [WebFrog](http://webfrogs.me/)

## 折腾了一下

* Add 百度统计
* Set cnzz 统计
* Set 多说留言
* Add MathJAX 数学公式

----

## 测试数学公式

行内公式：$y=x^2+2\times x+1$

单独公式：

$$y=x^2+2\times x+1$$

## 测试语法高亮

使用 [Pygments](http://pygments.org/) ，[使用介绍在此](https://github.com/mojombo/jekyll/wiki/Liquid-Extensions)。

{% highlight c linenos %}

#include <stdio.h>
#include <iostream>

int main()
{
    printf("Hello world!");

    return 0;
}

{% endhighlight %}
