# grunt-tmpl-compile v0.2.4

> Concat and pre-compile your underscore and lodash template files.

## Getting Started
This plugin requires Grunt `~0.4.1`

If you haven't used [Grunt](http://gruntjs.com/) before, be sure to check out the [Getting Started](http://gruntjs.com/getting-started) guide, as it explains how to create a [Gruntfile](http://gruntjs.com/sample-gruntfile) as well as install and use Grunt plugins. Once you're familiar with that process, you may install this plugin with this command:

```shell
npm install grunt-tmpl-compile --save-dev
```

Once the plugin has been installed, it may be enabled inside your Gruntfile with this line of JavaScript:

```js
grunt.loadNpmTasks('grunt-tmpl-compile');
```

## The "tmpl_compile" task

### Overview
In your project's Gruntfile, add a section named `tmpl_compile` to the data object passed into `grunt.initConfig()`.

```js
grunt.initConfig({
  tmpl_compile: {
    options: {
      namespace: 'Templates',
      preCompile: true,
      library: 'lodash'
    },
    files: {
      // Target-specific file lists and/or options go here.
    }
  }
})
```

### Options

#### options.namespace
Type: `String`
Default value: `Templates`

Global namespace variable to store the templates in.

#### options.preCompile
Type: `Boolean`
Default value: `true`

Wether to precompile the templates, or create a function that will compile it on the first function call.

### Usage Examples

#### Default Options
In this example, the templates template_1 and template_2 will be concatenated to the file pre_compiled.js and added to the global namespace Templates. By default the lodash library will be used.`

```js
grunt.initConfig({
  tmpl_compile: {
    options: {},
    files: [{
      src: ['test/fixtures/template_1.tmpl.html', 'test/fixtures/template_2.tmpl.html'],
      dest: 'tmp/pre_compiled.js'
    }]
  }
})
```

#### Custom Options
In this example the templates template_1 and template_2 will be concatenated. Each template will get a function on the namespace CustomNamespace. The template will be compiled on the first run and cached for later use.`

```js
grunt.initConfig({
  tmpl_compile: {
    options: {
      namespace: 'CustomNamespace',
      preCompile: false,
      library: 'underscore'
    },
    files: [{
      src: ['test/fixtures'],
      dest: 'tmp/pre_compiled.js'
    }]
  }
})
```

## Contributing
In lieu of a formal styleguide, take care to maintain the existing coding style. Add unit tests for any new or changed functionality. Lint and test your code using [Grunt](http://gruntjs.com/).

## Release History
* 2013-24-12   v0.2.4   Quickfix: ignore .DS_Store files.
* 2013-11-12   v0.2.3   Bugfix; remove trailing comma.
* 2013-10-22   v0.2.2   Fix in paths. Update 'files'-option to be more in line with guidelines.
* 2013-10-22   v0.2.1   Small update in paths.
* 2013-10-08   v0.2.0   Rework the generated files. Library of choise optional. Option to include full dirs with sub directories.
* 2013-10-06   v0.1.1   Remove grunt-lib-contrib. Place template files in external file.
