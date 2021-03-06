
<p align="center">
  <img src="https://github.com/guuibayer/gride/blob/gh-pages/src/img/logo.png">
</p>

<p align="center">
  <a href="https://gitter.im/gride-grid/Lobby"><img src="https://img.shields.io/badge/gitter-join%20chat-1dce73.svg"></a>
  <a href="https://badge.fury.io/js/gride"><img src="https://badge.fury.io/js/gride.svg"></a> 
  <a href="https://github.com/guuibayer/gride/blob/master/LICENSE.md"><img src="https://img.shields.io/badge/licence-MIT-blue.svg"></a>
</p>

<p align="center">
  Gride is a stylus and scss, simple and flexible grid system, gride use simple units percent or fractions, use only display  <code>inline-block</code> and <code>vertical-align</code>, not floats, positions or flexbox.
</p>

## Table of Contents
- [Installation](#installation)
- [How use](#how-use)
  - [Stylus API](#stylus-api)
  - [Gulp](#gulp)
  - [Grunt](#grunt)
- [Grid](#grid)
  - [`row`](#row)
  - [`col`](#col)
  - [`span`](#span)
- [Utilities](#utilities)
  - [`offset`](#offset)
  - [`debug`](#debug)
- [Support](#support)
- [Thanks](#thanks)

### Installation

Install the current version from gride and save in dev dependencies with command below.

```bash
$ npm install gride --save-dev
```

**[:arrow_up: back to top](#table-of-contents)**
&nbsp;

### How use

##### Stylus API

The easiest way to use gride is by importing the file directly, see.

```stylus
@import 'node_modules/gride/gride'
```

**[:arrow_up: back to top](#table-of-contents)**
&nbsp;

##### Gulp

To use gride with gulp, needs use [gulp-stylus](https://www.npmjs.org/package/gulp-stylus) and include gride call in use option.  

```javascript
var gulp = require('gulp')
    , gride = require('gride')
    , stylus = require('gulp-stylus');
    
gulp.task('styles', function () { 
  gulp.src('assets/stylus/styles.styl') 
    .pipe(stylus({ 'use': gride() })) 
    .pipe(gulp.dest('assets/css')); 
  });
```

**[:arrow_up: back to top](#table-of-contents)**
&nbsp;

##### Grunt

This is a example to use gride with grunt.

```javascript
module.exports = function (grunt) {
  grunt.loadNpmTask('grunt-contrib-stylus');

  grunt.initConfig({
    'stylus': {
      'options': {
        'compress': false,
        'use': [
          require('gride')
        ]
      },
      'styles': {
        'files': {
          'assets/css/styles.css': 'assets/stylus/styles.styl'
        }
      }
    }
  };
};
```

**[:arrow_up: back to top](#table-of-contents)**
&nbsp;

### Grid

##### Row

For all collumns or spans were need a row, the row is a container to align the context, row accept a unique param, is the max width. 

```stylus
.container
  row(1024px)
```

The output from code above is

```css
.container {
  width: 100%;
  display: block;
  margin: 0 auto;
  padding: 0 0px;
  max-width: 1024px;
  font-size: 0;
}
```

**[:arrow_up: back to top](#table-of-contents)**
&nbsp;

##### Col

The collumns accept two parameters, the first is a fraction or percent, example `2/5` or `40%/100% ` where 5 is the total of collumns and this collumn will occupy **2** from **5**, or **40%** from **100%**, the last parameter is the vertical alignment, the possible values is `top`, `middle` and `bottom`, and col use gutters for space between the collumns.   

```stylus
aside
  col(2/5, top)
  
section
  col(3/5, top)
```

The output from this code is

```css
aside {
  width: 40%;
  padding: 0 15px;
  display: inline-block;
  vertical-align: top;
  font-size: initial;
}

section {
  width: 60%;
  padding: 0 15px;
  display: inline-block;
  vertical-align: top;
  font-size: initial;
}
```

**[:arrow_up: back to top](#table-of-contents)**
&nbsp;

##### Span

The span method is based and follows the same principle of calculation in the `col` method, accept fractions or percent in the first parameter and the last accept `top`, `middle` and `bottom`, but the difference is that he has no gutters.

```stylus
aside
  span(2/5, middle)
  
section
  span(3/5, middle)
```

```css
aside {
  width: 40%;
  padding: 0;
  display: inline-block;
  vertical-align: middle;
  font-size: initial;
}

section {
  width: 60%;
  padding: 0;
  display: inline-block;
  vertical-align: middle;
  font-size: initial;
}
```

**[:arrow_up: back to top](#table-of-contents)**
&nbsp;

### Utilities

##### Offset

The offset method is an auxiliary to be used along with the `col` or `span` in the example below, we move the column **aside** to the right, centering it.

```stylus
aside
  offset(1/3, left)
  col(1/3, top)
```

The output from this example is the aside centralized.

```css
aside {
  margin-right: 33,333333333%;
  width: 33,333333333%;
  padding: 0 15px;
  display: inline-block;
  vertical-align: top;
  font-size: initial;
}
```


**[:arrow_up: back to top](#table-of-contents)**
&nbsp;

##### Debug

```stylus
debug()
```

Output is

```css
* {
  background-color: rgba(255, 255, 255, 0.2);
}
```

**[:arrow_up: back to top](#table-of-contents)**
&nbsp;

### Support

### Thanks
