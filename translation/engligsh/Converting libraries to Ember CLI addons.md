# Converting libraries to Ember CLI addons

In this guide we will cover two main cases:

- Ember specific library
- vendor library

### Ember library

The Ember library will assume that Ember has already ben loaded (higher in the loading order) and thus will assume it has access to the Ember API.

Let's assume we have a library which creates a new Ember namespace called `Ember.Validators` and the full distributed library is available at: `dist/ember-validators.js`.

```javascript
// dist/ember-validators.js
Ember.Validators = Ember.Namespace.create({
  // ...
});

Ember.Validators.presence = function (args) {
  // ...
}
```

Then we should expose the library via [bower](http://bower.io/docs/creating-packages/) by configuring a `bower.json` file. We should use the `"main"` property to indicate the main files of the distribution and use `"ignore"` to specify which folders/files not to take part in the package when it is installed.

```javascript
//bower.json
{
  "name": "my-project",
  "version": "1.0.0",
  "main": [
    "dist/es6/ember-validator.js",
    "dist/ember-validator.js",
    ],
  "ignore": [
    ".jshintrc",
    "lib"
    // ...
  ],
  "dependencies": {
    // ...
  },
  "devDependencies": {
    // ...
  }
}
```


In a "normal" Ember app, you would simply reference this library by script like this:

```html
<script src="bower_components/ember/dist/stable/ember.js"/>
<script src="bower_components/ember-validations/dist/ember-validators.js"/>
````

For an Ember CLI app, we should instead import such files via *Broccoli* using `app.import` statements:

```javascript
// Broccoli.js
app.import(app.bowerDirectory + '/ember-validations/ember-validators.js')
```

For an Ember CLI addon, we can avoid having to *pollute* our main `Brocfile` with all these import statements by instead having the addon import them on the app using the `"included"` hook.

```javascript
// index.js (of the addon)
module.exports = {
  name: 'ember-cli-validators',
 
  included: function(app) {
    this._super.included(app);

    app.import(app.bowerDirectory + '/ember-validatiors/ember-validators.js');
  }
}
````

In the hosting app, we then have to first install it as a bower component via `bower install` and then as an ember-cli addon (npm package) via `npm install`.

This should have the exact same effect as the simple `<script src="">` example above and it should add Ember namespace.

As we can see, this is not really optimal, as it leads to duplication, ie. the package being installed twice by two different package managers. Instead it is recommended to package the library first as a normal bower package and then create a new `ember-cli-*` package that is a thin "bower wrapper", which assumes the bower package has already been installed. The addon should then simply reference the bower component and install the app tree and blueprints particular to the addon.

This is the way most of the ember-cli addons that come with ember-cli are packaged (f.ex see *ember-qunit* in your bower components folder, then *ember-cli-qunit* in your node_modules

Here is one such example:

```javascript
app.import('bower_components/ember-cli-shims/test-shims.js', {
  type: 'test',
  exports: {
    'qunit': ['default']
  }
});
```

For our example it could be something like:

```javascript
this.app.import(
  app.bowerDirectory + '/ember-easyform-cli/distributions/es6/ember-easyform-cli.js',
    {exports: {'ember-easyform': 'default'}}
);
```

Or more simply just:

```javascript
  this.app.import(
    app.bowerDirectory + '/ember-easyform-cli/distributions/ember-easyform-cli.js'
  );
  // lets see that we got it!
  console.log('app, app.legacyFilesToAppend);
```

And then import it in our app like this:

```bash
$ ember serve
version: 0.0.46
loaded ember-easyform-cli
including ember-easyform-cli into app
app [ 'bower_components/loader/loader.js',
  'bower_components/jquery/dist/jquery.js',
  'bower_components/handlebars/handlebars.js',
  'bower_components/ember/ember.js',
  'bower_components/ember-cli-shims/app-shims.js',
  'bower_components/ember-resolver/dist/modules/ember-resolver.js',
  'bower_components/ember-load-initializers/ember-load-initializers.js',
  'vendor/ember-data/ember-data.js',
  'vendor/ic-ajax/dist/named-amd/main.js',
  'bower_components/ember-easyform-cli/distributions/ember-easyform-cli.js' ]
```

So as we can see, it should be available as a legacy file in this fashion.

### Ember objects

If our addon doesn't add to the namespace, but instead exposes one or more Ember objects to be included in parts of the app, we need a different strategy.

Lets imagine we have a libray which defines a few globals like this (not exactly recommended):

```javascript
// dist/my-ember-mixins.js
var AuthorizerMixin = Ember.Mixin.create({
  // ...
});

var TimerMixin = Ember.Mixin.create({
  // ...
});
```

We could use the same approach as for the `Ember.Namespace` example, but then we would still pollute the global namespace of the app. How can we wrap this in a way that we have more fine grained control?

We could create another file which wraps it as follows, using ES6 modules. We will put this ES6 wrapper in `dist/es6/my-ember-mixins.js`

```javascript
// dist/es6/my-ember-mixins.js

require('../my-ember-mixins.js');

export var Authorizer = AuthorizerMixin;
export var TimerMixin = TimerMixin;
```

If we only want (or need) to export a single variable we can use `export default`

```
var mixins = {
  authorizer: AuthorizerMixin,
  timer: TimerMixin
}

export default mixins;
```

We could then import the wrapper file instead for Ember CLI apps using it as an addon.

```javascript
module.exports = {
  name: 'ember-cli-validators',
 
  included: function(app) {
    this._super.included(app);

    app.import('dist/es6/ember-validators.js')  
  }
}
````

This would let us import just the variables we want, where we want. Here we demonstrate use of the (optional) alias feature by using `as`.

```javascript
// app/mixins/authorization.js

import {Authorizer as authorize} from "ember-cli-validators";

console.log('Authorizer', authorize);
```


### Vendor library

For a vendor library, you can use he same approach as described for Ember objects.