在跨平台、浏览器、移动设备兼容的时候，要根据设备、浏览器做特定调整，所以我们经常会用到navigator.userAgent.toLowerCase()来进行判断。

先来解释一下意思，navigator是HTML中的内置对象，包含浏览器的信息；userAgent是navigator的属性方法，可以返回由客户机发送服务器的头部的值，作用其实就是就是返回当前用户所使用的是什么浏览器，toLowerCase(）是将转换为小写。

区分Android、iphone、ipad：

[javascript] view plain copy
var ua = navigator.userAgent.toLowerCase();  
if (/android|adr/gi.test(ua)) {  
    // 安卓  
       
}else if(/\(i[^;]+;( U;)? CPU.+Mac OS X/gi.test(ua)){  
    //苹果  
       
}else if(/iPad/gi.test(ua)){  
    //ipad  
  
}  
有些软件是内置的浏览器，比如新浪微博、腾讯QQ（非QQ浏览器）和微信

（微信在6.0.2版本的时候做了改动，微信的分享功能在新版本跟以前不一样了）为了兼容版本，要做以下操作：

注：新浪微博为1，QQ客户端为2，微信低于6.0.2版本为3，高于6.0.2版本为4，其他为0。

[javascript] view plain copy
var ua = navigator.userAgent.toLowerCase();    
if(ua.match(/weibo/i) == "weibo"){    
    console.log(1);  
}else if(ua.indexOf('qq/')!= -1){    
    console.log(2);  
}else if(ua.match(/MicroMessenger/i)=="micromessenger"){    
var v_weixin = ua.split('micromessenger')[1];    
    v_weixin = v_weixin.substring(1,6);    
    v_weixin = v_weixin.split(' ')[0];    
if(v_weixin.split('.').length == 2){    
    v_weixin = v_weixin + '.0';    
}    
if(v_weixin < '6.0.2'){    
    console.log(3);  
}else{    
    console.log(4);    
}    
}else{    
    console.log(0);   
}    
区分各个浏览器：

[javascript] view plain copy
var ua=navigator.userAgent.toLowerCase();    
if(/msie/i.test(ua) && !/opera/.test(ua)){    
    alert("IE");    
    return ;    
}else if(/firefox/i.test(ua)){    
    alert("Firefox");    
    return ;    
}else if(/chrome/i.test(ua) && /webkit/i.test(ua) && /mozilla/i.test(ua)){    
    alert("Chrome");    
    return ;    
}else if(/opera/i.test(ua)){    
    alert("Opera");    
    return ;    
}else if(/iPad/i){   
    alert("ipad");   
    return ;   
}  
 if(/webkit/i.test(ua) &&!(/chrome/i.test(ua) && /webkit/i.test(ua) && /mozilla/i.test(ua))){    
    alert("Safari");    
    return ;    
}else{    
    alert("unKnow");    
}    




*********************************补充分割线*************************************************

chrome中：navigator.userAgent的值：


其实navigator.userAgent 也有bug,

在IOS中，时间的显示格式一般是 '2016/11/11 11:11:11' ，所以对于安卓的'2016-11-11 11:11:11'，是不适用于IOS的。

因此，我们用下面的代码去判断安卓系统，

[javascript] view plain copy
<span style="font-size:18px;">var isAdr = new Date('2016-11-11 11:11:11').getTime() > 0;</span>  

!isAdr就是IOS~~~
