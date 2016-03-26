---
layout: post
category: WEB开发
title:  ThinkPHP＋AJAX＋JQuery实现了图片不刷新页面上传
date:   2015-11-15 19:52:05
tagline: by WuBin 武斌
tags: [ThinkPHP,JS,图片上传]
published: true
author: wubin

---

本篇文档是在前一篇文章“ThinkPHP图片裁剪上传插件”的完善，通过AJAX＋JQuery实现了不刷新页面上传

<!--more-->


>本文是在ThinkPHP3.2下进行测试实现的,使用ThinkPHP自带的图片上传裁剪库。其他环境没有测试。

## Html

	<div class="form-group">
      <label for="" class="col-sm-3 control-label">创意草图</label>
      <form id="upload_picture" name="upload_picture" enctype="multipart/form-data">
          <!-- hidden crop params -->
          <input type="hidden" id="x1" name="x1" autocomplete="off" />
          <input type="hidden" id="y1" name="y1" autocomplete="off"/>
          <input type="hidden" id="x2" name="x2" autocomplete="off" />
          <input type="hidden" id="y2" name="y2" autocomplete="off" />
          <input type="file" name="file" id="image_file" onchange="fileSelectHandler()" />
      </form>
      <div class="error">注意：上传前，先截图</div>
      <div class="step2">
          <span class="img-box"><img id="preview" /></span>
          <div class="info"><!--文件大小、类型、图像尺寸、宽度、高度-->
            <input type="hidden" id="filesize" name="filesize" />
            <input type="hidden" id="filetype" name="filetype" />
            <input type="hidden" id="filedim" name="filedim" />
            <input type="hidden" id="w" name="w" />
            <input type="hidden" id="h" name="h" />
          </div>
          <!-- <input value="上传" class="btn btn-pic" /> -->
          <!-- <input type="button" name="b1" value="submit" onclick="pictureup()"> -->
      </div>
      <a id="btnpicture" class="btn btn-info" onclick="pictureup()">上传</a>
    </div>
 
## AJAX

	<script>
    function pictureup(){
      checkForm();
      var data = new FormData();
      data.append('file',$('#image_file')[0].files[0]);
      var other_data = $('#upload_picture').serializeArray();
      $.each(other_data,function(key,input){
          data.append(input.name,input.value);
      });
      //console.log(data);
      $.ajax({
        url : "{:U('Home/PublicUpload/idea_picture_upload')}",
        type : 'POST',
        data : data,
        processData : false,
        contentType : false,
      }).done(function(result){
      		//这里根据返回json填写自己的信息
      });
    }
    </script>

参考网页：

1. [通过jQuery Ajax使用FormData对象上传文件](http://www.jianshu.com/p/46e6e03a0d53)
2. [Send FormData and String Data Together Through JQuery AJAX?](http://stackoverflow.com/questions/21060247/send-formdata-and-string-data-together-through-jquery-ajax)