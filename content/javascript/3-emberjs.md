Ember.js的安装与使用
-----------------------

使用ember-cli作为开发命令行工具，让ember.js具备rails似的强大工具

## 8. 格式化数据

从客户端请求或提交的数据，有时候需要格式化，具体由RESTSerializer负责

参考：

* 官方文档，非常详细了 http://emberjs.com/api/data/classes/DS.ActiveModelSerializer.html#method_serializeBelongsTo
* http://stackoverflow.com/questions/21634433/formatting-json-using-the-restserializer-in-the-latest-ember-data-version
* http://stackoverflow.com/questions/20410016/transform-json-to-an-appropriate-format-for-restadapter-emberjs

## 7. 设置一个全局变量，比如currentUser

* 不建议这么做。

参考：http://stackoverflow.com/questions/16878473/access-a-global-variable-from-any-app-controller

* 简单的做法，要用initializer，很多插件就是这么做的，特别是ember-simple-auth

参考：http://stackoverflow.com/questions/23718384/where-do-you-place-a-simple-variable-in-the-ember-app-kit-file-structure-so-it-c
     
http://www.samselikoff.com/blog/injecting-a-global-variable-into-your-ember-classes/
     
## 6. ember-data 

参考：https://github.com/emberjs/data/blob/master/TRANSITION.md

http://www.toptal.com/emberjs/a-thorough-guide-to-ember-data

http://www.57kan.com/show/index/id/36812 分析很深入

## 5. nest 嵌套资源等

参考：http://stackoverflow.com/questions/24097522/nested-resources-in-ember-js-adding-comments-to-a-post-with-fixture-data

## 4. router.js需要注意的小细节

*  `this.resource('tools');` 与 `this.resource('tools', function() {});` 的区别，下面的文章印证了这个区别

链接：http://ugisozols.com/blog/2013/11/05/understanding-nesting-in-emberjs/

## 3. link-to的2个必须注意的小细节

* 当你点击链接，没有达到你的预期效果的时候，需要考虑下面的情况

`{{link-to 'blogs.show', post}}`需要`post`对象数据已经加载， `{{link-to 'blogs.show', post.id}}`则会重新调用model钩子方法加载数据。

参考: http://guides.emberjs.com/v1.11.0/templates/links/

* 当你需要优化url，实现更加人性花的地址显示的时候，要使用下面的方法

对于动态参数不是`id`的情况，需要重写`serialize`钩子方法

参考: http://guides.emberjs.com/v1.11.0/routing/defining-your-routes/#toc_dynamic-segments

```
//app/routes/post.js

export default Ember.Route.extend({
  model: function(params) {
    // the server returns `{ slug: 'foo-post' }`
    return Ember.$.getJSON('/posts/' + params.post_slug);
  },

  serialize: function(model) {
    // this will make the URL `/posts/foo-post`
    return { post_slug: model.get('slug') };
  }
});
```
## 2. Watchman安装
说明: 不安装，会出现错误 you have a different program called watchman, falling back to NodeWatcher.
安装

参考：https://facebook.github.io/watchman/docs/install.html

```
$ git clone https://github.com/facebook/watchman.git
$ cd watchman
$ ./autogen.sh
$ ./configure
$ make
$ sudo make install
```

## 1. 安装

```
npm install -g ember-cli
```
