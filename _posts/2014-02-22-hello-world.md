---
date: 2014-02-22 01:42:00 +0800
layout: post
title: 学而时习之，不亦乐乎
categories: Edu
tags: 普及教育
mathjax: true
---

用 Markdown 写博客。不再纠结于软件、排版技术。专心用文字记录下数学学习中的点点滴滴。

本博客运行于 [Jekyll](http://jekyllrb.com) @ [GitHub](http://github.com/ccpaging)，
博客模板修改自：[Yonsm.NET](http://www.yonsm.net) 以及 [WebFrog](http://webfrogs.me/)

## 折腾了一下

* Add 百度统计
* Set cnzz 统计
* Set 多说留言
* Set Kramdown，[编辑参考](http://sourceforge.net/p/karma/wiki/markdown_syntax/)，[设计参考](http://kramdown.gettalong.org/quickref.html)
* Add MathJAX 数学公式。

----

## 测试数学公式

行内公式：$y=x^2+2x+1$

单独公式：

$$\lim_{馅 \rightarrow 0} 包子=馒头 $$

## 测试语法高亮

使用 [Pygments](http://pygments.org/) ，[常用语法](http://pygments.org/docs/lexers/)。

{% highlight c linenos %}

#include <stdio.h>
#include <iostream>

int main()
{
    printf("Hello world!");

    return 0;
}

{% endhighlight %}
