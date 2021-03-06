# gulp-lodash-autobuild

> Create a custom build for [Lodash](https://lodash.com/custom-builds) (>= v4.0)

## Install

```shell
$ npm install --save-dev gulp-lodash-autobuild
```

## Basic Usage

Something like this will compile your Sass files:

```javascript
'use strict';

const gulp = require('gulp');
const lodashAutobuild = require('gulp-lodash-autobuild');

const options = {
  target: '.tmp/lodash.custom.js',
  settings: {},
  include: ['_.chunk', '_.tap'] // Force include these functions
};

gulp.task('lodash:autobuild', () => {
  return gulp.src('./src/**/*.js', { buffer: false })
    .pipe(lodashAutobuild(options))
    .on('error', function(err) {
      console.log('err: ', err);
    });
});
```

## Note

Lodash chained functions are not properly detected, you may manually include them using `options.include`.
Eg: in `_.chain(obj).filter(...)`, `filter` won't be detected as a lodash function.

## Issues

Lightweight gulp wrapper for [lodash-cli](https://www.npmjs.com/package/lodash-cli), refer to this repo for main issues.
Feel free to report bugs or submit a PR.

## Test build

Not a proper unit test, but make sure the code work and the file is built.

```bash
gulp lodash:autobuild --gulpfile test/lodash-autobuild-test.js
```


> Original code from https://github.com/OneLittleRobot/gulp-lodash-autobuild

