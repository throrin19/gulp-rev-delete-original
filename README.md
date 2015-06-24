# gulp-rev-delete-original

Delete the original file rewritten by [gulp-rev](https://github.com/sindresorhus/gulp-rev).

## Installation

    npm i --save gulp-rev-delete-original
  
## Usage

    var gulp = require('gulp');
    var rev = require('gulp-rev');
    var revcss = require('gulp-rev-css-url');
    var revdel = require('gulp-rev-delete-original');
    
    gulp.task('rev', function () {
      return gulp.src('./app/**/*')
        .pipe(rev())
        .pipe(revcss())
        .pipe(revdel())
        .pipe(gulp.dest('./build/'))
      ;
    });

## Options

#### exclude 

A filter `RegExp` or `function` that allows you to exclude certain files. 

##### Example

RegExp:

    revdel({
      exclude: /build\.css$/
    });

Function: 

    revdel({
      exclude: function(file) {
        if (/build\.css$/.test(file.name)) {
          return true; //if you want to exclude the file from being deleted
        }
      }
    });