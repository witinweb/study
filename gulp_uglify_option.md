# gulp-uglify 

by [스키머](http://schemr.tumblr.com/)

gulp-uglify는 자바스크립트 파일을 병합하는 gulp-concat과 함께 많이 사용하고 있는 자바스크립트 파일 압축(Minify) 플러그인 입니다. 

## 설치

    npm install --save-dev gulp-uglify

gulp 및 gulp 플러그인 설치에 대한 자세한 내용은 [Gulp.js로 빌드 작업 관리하기](http://witinweb.tumblr.com/post/122258847897/gulp-js) 를 참고하세요.

## Gulpfile.js

    var gulp	 	= require('gulp');
	var concat   	= require('gulp-concat');
    var uglify		= require('gulp-uglify');
    
    gulp.task('combine-js', function () {
    	gulp.src('./js/*.js')
    		.pipe(concat('all.js'))
    		.pipe(uglify())
    		.pipe(gulp.dest('./dist/js'))
    });
    
    gulp.task('watch', function () {
    	gulp.watch('./js/*.js', ['combine-js']);
    });
    
    gulp.task('default', [
    	'watch'
    ]);

## all.js

    !function(e,t){"object"==typeof module&&"object"==typeof module.exports?module.exports=e.document?t(e,!0):function(e){if(!e.document)throw new Error("jQuery requires a window with a document");..........


## 옵션

### mangle 
false 로 설정시 변수 및 매개변수가 변경되지 않습니다. (default : true)

Gulpfile.js

    .pipe(uglify({
    	mangle: false
    }))

all.js
    		
    !function(global,factory){"object"==typeof module&&"object"==typeof module.exports?module.exports=global.document?factory(global,!0):function(w){if(!w.document)throw new Error("jQuery requires a window with a document");

### output 
[output 옵션](http://lisperator.net/uglifyjs/codegen)을 통해서 추가 출력 옵션을 지정할 수 있습니다.(기본값은 최적의 압축에 최적화되어 있습니다. 자세한 내용은 링크 참고.) 

### compress 
지정할 사용자 정의 [압축 옵션](http://lisperator.net/uglifyjs/compress)의 객체를 전달합니다. (자세한 내용은 링크 참고.)

### preserveComments 
주석에 대한 출력에 대한 옵션입니다. (기본값은 주석을 표시하지 않습니다)

    .pipe(uglify({
	    preserveComments : 'all' // all, some, function()
	}))

- all - 모든 주석을 표시합니다. 
- some - (!) 로 시작하는 주석 또는 Closure Compiler directive (@preserve, @license, @cc_on) 를 포함하는 주석만 표시합니다. 
- function - 주석 표시 조건을 지정 합니다. ( true 또는 false 반환 )


gulp-uglify를 이용해 자바스크립트 파일을 압축할 때에는 변수 및 매개변수의 변경과 공백이 없어져 의도하지 않은 오류가 생길 위험이 있습니다. 따라서 규칙을 잘 따라서 코딩하는 습관을 들여야 하고 JSLint와 같은 자바스크립트 검증툴을 이용하는 방법도 추천합니다. 특히 AngularJS 의 경우 주입하는 변수 명이 변경될 경우 injector 오류를 발생시킬 위험이 있습니다. (option  mangle : false 지정)

