监听硬件的`back`键操作，并且如果没有任何监听器返回true，则可以利用程序调用默认的back键功能来退出应用

例子：

```javascript
BackAndroid.addEventListener('hardwareBackPress', function() {
     if (!this.onMainScreen()) {
       this.goBack();
       return true;
     }
     return false;
});
```

### 方法

<div class="props">
	<div class="prop"><h4 class="propTitle"><a class="anchor" name="exitapp"></a><span class="propType">static </span>exitApp<span class="propType">()</span> <a class="hash-link" href="#exitapp">#</a></h4></div>
	<div class="prop"><h4 class="propTitle"><a class="anchor" name="addeventlistener"></a><span class="propType">static </span>addEventListener<span class="propType">(eventName: BackPressEventName, handler: Function)</span> <a class="hash-link" href="#addeventlistener">#</a></h4></div>
	<div class="prop"><h4 class="propTitle"><a class="anchor" name="removeeventlistener"></a><span class="propType">static </span>removeEventListener<span class="propType">(eventName: BackPressEventName, handler: Function)</span> <a class="hash-link" href="#removeeventlistener">#</a></h4></div>
</div>