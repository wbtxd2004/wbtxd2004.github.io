---
layout: post
category: 记录
title:  php微信自定义菜单用json_encode不转义中文汉字的方法
date:   2015-12-01 15:52:05
tagline: by WuBin 武斌
tags: [ThinkPHP,PHP,微信,json_encode]
published: true
author: wubin

---

本篇文档是转自CSDN上ball球的博客[ 从微信自定义菜单说php json_encode不转义中文汉字的方法](http://blog.csdn.net/qmhball/article/details/45690017),我在使用ThinkPHP＋[wechat-php-sdk](https://github.com/gaoming13/wechat-php-sdk)开发微信时遇到了一样的错误，最终通过本方法解决。

<!--more-->


>本篇文档是转自CSDN上ball球的博客[ 从微信自定义菜单说php json_encode不转义中文汉字的方法](http://blog.csdn.net/qmhball/article/details/45690017),我在使用ThinkPHP＋[wechat-php-sdk](https://github.com/gaoming13/wechat-php-sdk)开发微信时遇到了一样的错误，最终通过本方法解决。

## 问题

最近在开发微信自定义菜单。
接口比较简单，就是按微信要求的格式post一段json数据过去就成。
但我的菜单中里有中文，json_encode后出现了类似"\u5c0f\u8c61" 的unicode字符。
请求发出后被微信接口告知：

	{"errcode":40033,"errmsg":"invalid charset. please check your request, if include \\uxxxx will create fail!"}

不支持unicode字符！
那么如何才能使json_encode不转义汉字呢？
## 方法1
如果你的php版本是5.4+， 那么恭喜你，一个参数JSON_UNESCAPED_UNICODE就能搞定。

	<?php                                                                                         
	$data = array(                                                                                
    "name"=>"羊羊羊",                                                                         
    "type"=>"view",                                                                           
    "url"=>"http://xuan9806.com/"                                                             
	);                                                                                            
                                                                                              
	echo json_encode($data, JSON_UNESCAPED_UNICODE), "\n";
	
得到结果：

	{"name":"羊羊羊","type":"view","url":"http:\/\/xuan9806.com\/"}
	
## 方法2(未测试)
如果不幸由于种种原因你的php无法升到高版本，那么可以这么做：
把字段中的中文urlencode， 在json_encode后将得到的字串整体urldecode即可

	<?php
	$data = array(
	    "name"=>urlencode("羊羊羊"),
	    "type"=>"view",
	    "url"=>"http://xuan9806.com/"
	);
	
	$result = json_encode($data, JSON_UNESCAPED_UNICODE);
	$result = urldecode($result);
	
	echo $result, "\n";
	
同样得到法1中的结果。

  