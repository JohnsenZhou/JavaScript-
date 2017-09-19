# XMLHttpRequest2

## 新属性 FormData

用法：

```
var data = new FormData();
// append()方法接受两个参数，以键值对方式表示
data.append('name', 'Johnsen');
data.append('age', 23);
data.append('phone', 15700000000);

var xhr = new XMLHttpRequest();
// 回调处理
xhr.onload = function() {
	if ( (xhr.status >= 200 && xhr.status < 300) || xhr.status === 304 ) {
		alert(xhr.responseText);
	} else {
		alert("Request was unsuccessful: " + xhr.status");
	}
};

xhr.open("post", "server url");
xhr.send(data);

// FormData中也可以直接传入表单元素
var formVal = document.getElementById("userInfo");
xhr.send(new FormData(formVal));
```

## 超时设定

`timeout` 属性： 请求在等待响应多少毫秒之后终止。

`ontimeout`属性：规定时间没接收到响应，触发`timeout`，接着调用`ontimeout`事件处理程序

```
xhr.open("post", "server url");
xhr.timeout = 1000;
xhr.ontimeout = function() {
	alert('time out')
};
xhr.send(data);
```

## progress 事件

```
// 上传
xhr.upload.onprogress = function(e) {
	if(e.lengthComputable) {
		var percent = e.loaded / e.total * 100;
	}
}
// 下载
xhr.onprogress = function(e) {
	if(e.lengthComputable) {
		var percent = e.loaded / e.total * 100;
	}
}
```

## 友情链接

[XMLHttpRequest详解](https://segmentfault.com/a/1190000004322487#articleHeader12)


