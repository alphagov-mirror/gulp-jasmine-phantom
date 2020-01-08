‼️‼️ DEPRECATED ‼️‼️
=============
PhantomJS is no longer being maintain. Instead of using this repository, switch
to another headless browser. When this project was archived the [Digital Marketplace team were the only team using it](https://github.com/search?q=alphagov%2Fgulp-jasmine-phantom%23node-10-fs-unlink&type=Code). The team migrated to Jest/JSDOM
in January 2020 and so no longer required it. The team could not see any other codebase on github using it so decided to archive it instead of deleting.

gulp-jasmine-phantom
=============

A gulp plugin that runs Jasmine tests with PhantomJS.

This fork is intended for use in environments where PhantomJS is present and the Node version is `0.10.x`*.

It removes the ability to use mininodejasmine2 due to its inclusion introducing the need for 
`execSync` which is not available when using a version of Node under `0.12.x`.
*The current need is for running JS unit tests on [Travis-CI](https://travis-ci.org/) where the primary language is not Node. In this situation Node is available but is (as of 08 Sept 2015) locked to `0.10.36`.

Dependencies
------------

Before you install `gulp-jasmine-phantom` please ensure that you have PhantomJS
installed on your machine. The plugin assumes that the `phantomjs` binary is
available in the PATH and executable from the command line.

If not, ensure you at least have `phantomjs` as an npm dependency. The module
checks in `./node_modules/phantomjs` for an executable if you do not have it
installed globally.

**If you do not have `phantomjs` installed please install following
[these directions.](http://phantomjs.org/download.html)

Install
-----

```
$ npm install --save-dev git://github.com/alphagov/gulp-jasmine-phantom.git#<latest commit SHA>
```

Usage
-----
Basic usage:

```javascript
var gulp = require('gulp');
var jasmine = require('gulp-jasmine-phantom');

gulp.task('default', function() {
  return gulp.src('spec/test.js')
          .pipe(jasmine());
});
```

Options
-------

#### jasmineVersion
Type: `string` <br />
Default: '2.0'

Specifies the version of Jasmine you want to run. Possible options are in the `vendor/` folder. Just specify what `2.x` minor release you want.

#### keepRunner
Type: `boolean | string` <br />
Default: false

Keep the `specRunner.html` file after build. If given a string, it will keep
the runner at the string path.

#### includeStackTrace
Type: `boolean` <br />
Default: false

Prints out a longer stack trace for errors.

#### abortOnFail
Type: `boolean` <br />
Default: false

**Currently built with integration mode only** <br />
Exits Gulp with an status of 1 that will halt any further Gulp tasks.

#### specHtml
Type: `string` <br />
Default: null

**Only use in combination with `integration: true`**

Allows you to specify the HTML runner that Jasmine uses **only** during
integration tests.

#### vendor
Type: `string | array` <br />
Default: null

**Only use in combination with `integration: true`**

A list of vendor scripts to import into the HTML runner, either as file
globs (e.g. `"**/*.js"`) or fully-qualified URLs (e.g.
`"http://my.cdn.com/jquery.js"`).

This option accepts either a single string or an array of strings (e.g.
`["test/*.js", "http://my.cdn.com/underscore.js"]`).

Technologies Used
-----------------

* Node
* Gulp
