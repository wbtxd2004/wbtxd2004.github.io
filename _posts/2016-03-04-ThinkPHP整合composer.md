---
layout: post
category: 记录
title:  ThinkPHP3.2.3使用composer
date:   2016-03-04 11:37:05
tagline: by WuBin 武斌
tags: [ThinkPHP,Elasticsearch,Composer]
published: true
author: wubin

---

开发过程遇到需要使用composer安装的php插件，所以在这里记录一下修改和使用方法。

<!--more-->

# 修改composer.json

将需要使用的插件添加到项目根目录的composer.json插件中，我需要使用elasticsearch。

	{
	    "name": "topthink/thinkphp",
	    "description": "the ThinkPHP Framework",
	    "type": "framework",
	    "keywords": ["framework","thinkphp","ORM"],
	    "homepage": "http://thinkphp.cn/",
	    "license": "Apache2",
	    "authors": [
	        {
	            "name": "liu21st",
	            "email": "liu21st@gmail.com"
	        }
	    ],
	    "require": {
	        "php": ">=5.3.0",
	         "elasticsearch/elasticsearch": "~2.0"
	    },
	    "minimum-stability": "dev",
	    "repositories": [
	        {"type": "composer", "url": "http://packagist.phpcomposer.com"},
	        {"packagist": false}
	    ]
	}

## 这里记录一下波浪号运算符

~ 最好用例子来解释： ~1.2 相当于 >=1.2,<2.0，而 ~1.2.3 相当于 >=1.2.3,<1.3。正如你所看到的这对于遵循 语义化版本号 的项目最有用。一个常见的用法是标记你所依赖的最低版本，像 ~1.2 （允许1.2以上的任何版本，但不包括2.0）。由于理论上直到2.0应该都没有向后兼容性问题，所以效果很好。你还会看到它的另一种用法，使用 ~ 指定最低版本，但允许版本号的最后一位数字上升。

# 安装插件

在项目根目录通过终端执行：

	composer install
	
至于怎么使用和安装composer这里就不描述了，有问题的可以参考[Composer中文网](http://www.phpcomposer.com/)

# ThinkPHP 配置

在入口文件（通常是index.php）中增加一句

	include 'vendor/autoload.php';
	
*注意要先引入composer再引入ThinkPHP*

# 使用Elasticsearch

在需要使用elasticsearch的控制器中实例化就可以了：

	$params['hosts'] = array(
        '127.0.0.1:9200'
    );
    $el = new \Elasticsearch\Client($params);
    
 *至于怎么使用elasticsearch就请参考官方文档吧*