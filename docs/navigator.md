使用导航器可以让你在应用中的不同场景进行切换。导航器通过路由对象来分辨不同的场景，同时利用`renderScene`方法，导航栏可以渲染指定路由的场景。

想要改变场景的动画或者手势，可以通过`configureScene`属性获取指定路由对象的配置信息。查看`Navigator.SceneConfigs`来获取默认的动画和更多的场景配置选项

### 基本用法
```javascript
<Navigator
    initialRoute={{name: 'My First Scene', index: 0}}
    renderScene={(route, navigator) =>
      <MySceneComponent
        name={route.name}
        onForward={() => {
          var nextIndex = route.index + 1;
          navigator.push({
            name: 'Scene ' + nextIndex,
            index: nextIndex,
          });
        }}
        onBack={() => {
          if (route.index > 0) {
            navigator.pop();
          }
        }}
      />
    }
  />
```
  
### 导航方法
如果你有一个导航对象的引用，你可以调用许多方法来进行导航

* getCurrentRoutes() - 获取当前栈里的路由，也就是push进来，没有pop掉的那些
* jumpBack() - 跳回之前的路由，当然前提是保留现在的，还可以再跳回来，会给你保留原样。
* jumpForward() - 上一个方法不是调到之前的路由了么，用这个跳回来就好了
* jumpTo(route) - 跳转到已有的场景并且不卸载
* push(route) - 跳转到新的场景，并且将场景入栈，你可以稍后跳转过去
* pop() - 跳转回去并且卸载掉当前场景
* replace(route) - 用一个新的路由替换掉当前场景
* replaceAtIndex(route, index) - 替换掉指定序列的路由场景
* replacePrevious(route) - 替换掉之前的场景
* immediatelyResetRouteStack(routeStack) - 用新的路由数组来重置路由栈
* popToRoute(route) - 跳转到路由指定的场景，其他的场景将会卸载。
* popToTop() - 跳转到栈中的第一个场景，卸载掉所有的其他场景。

### 属性

<div class="props">
  <div class="prop">
    <h4 class="propTitle"><a class="anchor" name="configurescene"></a>configureScene <span class="propType">function</span> <a class="hash-link" href="#configurescene">#</a></h4>
    <div>
      <p>可选的函数，用来配置场景动画和手势。会带有一个路由参数调用，然后它应当返回一个场景配置对象</p>
      <pre class="markdown-highlight"><code class="language-javascript hljs">(route) =&gt; Navigator.SceneConfigs.FloatFromRight</code></pre>
    </div>
  </div>
  <div class="prop">
    <h4 class="propTitle"><a class="anchor" name="initialroute"></a>initialRoute <span class="propType">object</span> <a class="hash-link" href="#initialroute">#</a></h4>
    <div>
      <p>定义启动时加载路由。路由是导航栏用来识别渲染场景的一个对象。<code>initialRoute</code>必须是<code>initialRouteStack</code>中的一个路由。<code>initialRoute</code>默认为<code>initialRouteStack</code>中最后一项。</p>
    </div>
  </div>
  <div class="prop">
    <h4 class="propTitle"><a class="anchor" name="initialroutestack"></a>initialRouteStack <span class="propType">[object]</span> <a class="hash-link" href="#initialroutestack">#</a></h4>
    <div>
      <p>提供一个路由集合用来初始化。如果没有设置初始路由的话则必须设置该属性。如果没有提供该属性，它将被默认设置成一个只含有<code>initialRoute</code>的数组。</p>
    </div>
  </div>
  <div class="prop">
    <h4 class="propTitle"><a class="anchor" name="navigationbar"></a>navigationBar <span class="propType">node</span> <a class="hash-link" href="#navigationbar">#</a></h4>
    <div>
      <p>可选参数，提供一个在场景切换的时候保持的导航栏。</p>
    </div>
  </div>
  <div class="prop">
    <h4 class="propTitle"><a class="anchor" name="navigator"></a>navigator <span class="propType">object</span> <a class="hash-link" href="#navigator">#</a></h4>
    <div>
      <p>可选参数，提供从父导航器获得的导航器对象。</p>
    </div>
  </div>
  <div class="prop">
    <h4 class="propTitle"><a class="anchor" name="ondidfocus"></a>onDidFocus <span class="propType">function</span> <a class="hash-link" href="#ondidfocus">#</a></h4>
    <div>
      <p>@已废弃。使用<code>navigationContext.addListener('didfocus', callback)</code>来替代。</p>
      <p>每当导航切换完成或初始化之后，调用此回调，参数为新场景的路由。</p>
    </div>
  </div>
  <div class="prop">
    <h4 class="propTitle"><a class="anchor" name="onwillfocus"></a>onWillFocus <span class="propType">function</span> <a class="hash-link" href="#onwillfocus">#</a></h4>
    <div>
      <p>@已废弃。使用<code>navigationContext.addListener('willfocus', callback)</code>来替代。</p>
      <p>会在导航切换之前调用，参数为目标路由。</p>
    </div>
  </div>
  <div class="prop">
    <h4 class="propTitle"><a class="anchor" name="renderscene"></a>renderScene <span class="propType">function</span> <a class="hash-link" href="#renderscene">#</a></h4>
    <div>
      <p>必要参数。用来渲染指定路由的场景。调用的参数是路由和导航器。</p>
      <pre class="markdown-highlight"><code class="language-javascript hljs">(route, navigator) =&gt;
  <span class="xml"><span class="hljs-tag">&lt;<span class="hljs-title">MySceneComponent</span> <span class="hljs-attribute">title</span>=<span class="hljs-value">{route.title}</span> /&gt;</span>
</span></code></pre>
    </div>
  </div>
  <div class="prop">
    <h4 class="propTitle"><a class="anchor" name="scenestyle"></a>sceneStyle <span class="propType"><a href="view.html#style">View#style</a></span> <a class="hash-link" href="#scenestyle">#</a></h4>
    <div>
      <p>将会应用在每个场景的容器上的样式。</p>
    </div>
  </div>
</div>