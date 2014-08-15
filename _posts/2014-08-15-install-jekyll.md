---
layout: post
title: "install jekyll"
description: ""
category: 技术分享
tags: [install jekyll]
---
{% include JB/setup %}
# install jekyll
---


* 安装ruby，windows下安装[rubyinstaller](http://rubyinstaller.org/downloads/)
* 安装[DevKit](http://rubyinstaller.org/downloads/) ，注意：两者版本一定要匹配。解压到任意目录，cd进入
<!--break-->

```
 ruby dk.rb init
 ruby dk.rb review 
 ruby dk.rb install
```
* 安装完DevKit后，即可安装jekyll：`gem install jekyll`。
  由于GFW的原因，中国多数地区是无法正常安装的，这时就需要手动下载[gems](http://rubygems.org/pages/download) 。
  解压到任意目录，cd进入
<!--break-->

```
 ruby setup.rb
 gem install rubygems-update
```
   这之后再运行
<!--break-->
```
 gem install jekyll
```

* jekyll安装完后，可以测试
<!--break-->
```
  jekyll new xxxx
  jekyll server
```
   在本地登陆：[http://localhost:4000](http://localhost:4000) 即可看到jekyll生成的页面

* Enjoy

 


