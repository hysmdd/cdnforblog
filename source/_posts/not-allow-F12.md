---
title: 网页禁止审查元素和F12
author:
	name: 覃浩
	avatar: https://cdn.jsdelivr.net/gh/queen999/ImageHosting//imagesavatar.jpg
	url: https://www.zhengyuanyuan520.com
categories: 小技巧
date: 2020-05-19 22:25:11
comments: true
---



很多时候我们不想要自己的博客被其他人审查元素，防止其他人扒下自己的网页，获取网站内资源的真实链接，都会选择使用禁止浏览器右键查看元素或F12审查元素。

<!-- more -->

```js
<script>
document.onkeydown = function(){

if(window.event && window.event.keyCode == 123) {
    alert("F12被禁用");
    event.keyCode=0;
    event.returnValue=false;
}
if(window.event && window.event.keyCode == 13) {
    window.event.keyCode = 505;
}
if(window.event && window.event.keyCode == 8) {
    alert(str+"\n请使用Del键进行字符的删除操作！");
    window.event.returnValue=false;
}

}
</script>

<script type="text/javascript">
  document.onkeydown = function(){
   
      if(window.event && window.event.keyCode == 123) {
          window.location="about:blank"; //将当前窗口跳转置空白页
          event.keyCode=0;
          event.returnValue=false;
      }
      if(window.event && window.event.keyCode == 13) {
          window.event.keyCode = 505;
      }
      if(window.event && window.event.keyCode == 8) {
          alert(str+"\n请使用Del键进行字符的删除操作！");
          window.event.returnValue=false;
      }
   
  }
  </script>
```

