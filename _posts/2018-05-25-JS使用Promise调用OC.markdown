---
layout:     post
title:      "JS通过Promise调用OC方法"
subtitle:   "使用wkWebView"
date:       2018-05-25
author:     "Hong"
header-img: "img/home-bg.jpg"
tags:
    - OC
---

###Javascript调用OC使用Promise

JavaScript代码

```
!function(w){
	class i_handler {
		constructor (s,f) {
			this.success = s
			this.fail = f
		}
	}
    class iOS {
        constructor () {
            this.calls = new Map();
        }
        native (val) {
        	if (typeof val !== 'object') {
        		return
        	}
        	let key = val.identifier; 
        	if (typeof key === 'string' && this.calls.has(key)) {
        		let c = this.calls.get(key);
        		let successfull = val.successfull;
        		if (successfull) {
        			c.success(val.data);
        		} else {
        			c.fail(val.data); 
        		}
        		this.calls.delete(key);
        	}
        }
        emmit (method,paramater) {
            return new Promise(function(resoleve,reject) {
            	if (typeof method !== 'string' || method.length === 0) {
            		reject('方法名不能为空')
            		return;
            	}
            	let date = new Date();
            	let identifier = method + date.toDateString()
            	let msg = {
            		handler:method,
            		parameter:paramater,
            		identifier:identifier,
            	}
            	let c = new i_handler(resoleve,reject);
            	ios.calls.set(identifier,c)
            	window.webkit.messageHandlers.iOS.postMessage(msg);
            })
        }
    }
    if (!Reflect.has(w,'ios')) {
    	w.ios = new iOS();
    }
}(window)


```
使用

```
ios.emmit('method',{}).then(function(val) {

}).catch(functhon(error) {

})
```

水平有限，请指教

