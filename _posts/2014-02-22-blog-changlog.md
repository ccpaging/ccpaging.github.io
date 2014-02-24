---
date: 2014-02-24 16:10:00+00:00
layout: post
title: 修复 MathJAX 显示 BUG
categories: BLOG
tags:  BLOG
---

## 修复 CSS 与 MathJax 的冲突

文件： style.css

网页字体相关。导致数学公式显示过小。

> .import url(http://fonts.googleapis.com/css?family=Cuprum);

图片相关，设置了边框和阴影。

> .content img{max-width:640px;display:block;margin:4px auto;-webkit-box-shadow:#999 1px 1px 4px;-moz-box-shadow:#999 1px 1px 4px;box-shadow:#999 1px 1px 4px;}
