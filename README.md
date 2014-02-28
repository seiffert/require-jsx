# require-jsx

A [RequireJS](http://requirejs.org) plugin for JavaScript files containing [JSX](http://facebook.github.io/react/docs/syntax.html).

It can be used to load JS source file that contain [JSX](http://facebook.github.io/react/docs/syntax.html) code.
This is helpful when using [React](http://facebook.github.io/react/index.html) with [RequireJS](http://requirejs.org).

## Install <a name="install"></a>

Download the plugin [here](https://github.com/seiffert/require-jsx/raw/master/jsx.js)

Place this in the directory that is your
[baseUrl](http://requirejs.org/docs/api.html#config-baseUrl) for your project,
or set up a [paths config](http://requirejs.org/docs/api.html#config-paths)
for it for the module ID `jsx`.

## Usage <a name="usage".</a>

First, you need to configure RequireJS to use Facebook's [JSXTransformer](http://fb.me/JSXTransformer-0.3.0.js) which also is 
in [React](http://facebook.github.io/react/index.html):

    require.config({
        deps: ["main"],
        
        paths: {
            jsx: "../lib/jsx",
            JSXTransformer: '../lib/JSXTransformer'
        },
        
        shim: {
            JSXTransformer: {
                exports: "JSXTransformer"
            }
        }
    });

Then, you can reference JSX files via the `jsx!` plugin syntax. For example, to load
the `router.js` file that is in your `app` directory:

    require(['jsx!app/router'], function (Router) {
        
    });

The Plugin is then going to load the JavaScript source file `app/router.js`, parse it with Facebook's JSXTransformer 
and execute the resulting JavaScript source.
