Ember.js的安装与使用
-----------------------

使用ember-cli作为开发命令行工具，让ember.js具备rails似的强大工具


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
