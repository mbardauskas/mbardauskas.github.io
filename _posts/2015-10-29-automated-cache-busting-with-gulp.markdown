title: Automated cache busting with Gulp
categories:
  - Development
date: 2015-10-29 20:46:58
tags: Gulp, JavaScript
---

You probably want most of your image and other resources to be cached, so the users would have fast page loads with each page reload. Cache is great until there's a need to update the website. Busting cache allows to have cached resources and painless updates.

<a href="https://css-tricks.com/strategies-for-cache-busting-css/">There are ways to bust cache</a>. Some use <a href="http://www.stevesouders.com/blog/2008/08/23/revving-filenames-dont-use-querystring/">filename revving</a>, some rely on query string for filenames. Some leave it to their CMS and others don't think about it at all. I'll cover only filename revving since it seems to be most effective.

<!--more-->

#### Configuring web server

The easy part is configuring your apache web server through `.htaccess`:
```apacheconf
<IfModule mod_rewrite.c>
    RewriteEngine On
    RewriteCond %{REQUEST_FILENAME} !-f
    RewriteRule ^(.+)\.(\d+)\.(bmp|css|cur|gif|ico|jpe?g|js|png|svgz?|webp|webmanifest)$ $1.$3 [L]
</IfModule>
```

Or the same thing with IIS `web.config`:
```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
    <system.webServer>
        <rewrite>
            <rules>
                <rule name="Rewrite Rule" stopProcessing="true">
                    <match url="^(.+)\.(\d+)\.(bmp|css|cur|gif|ico|jpe?g|js|png|svgz?|webp|webmanifest)$" ignoreCase="true" />
                    <conditions>
                        <add input="{REQUEST_FILENAME}" matchType="IsFile" ignoreCase="true" negate="true" />
                    </conditions>
                    <action type="Rewrite" url="{R:1}.{R:3}" />
                </rule>
            </rules>
        </rewrite>
    </system.webServer>
</configuration>
```

#### Renaming files with gulp build step

There are ways to implement this into the build step. Usually we incorporate it with bundling tasks (eg. <a href="http://requirejs.org/">requirejs</a> and <a href="https://www.npmjs.com/package/gulp-cssmin">gulp-cssmin</a>). The following is the most trivial task to handle filename revving with Gulp:
```js
// gulpfile.js
var gulp = require('gulp');
var rename = require('gulp-rename');
var moment = require('moment');

var cache_suffix = moment().format('X');

gulp.task('bust-cache', function() {
  gulp.src(['./temp/bundle.css', './temp/bundle.js'], {base: './temp'})
    .pipe(rename({
      suffix: '.' + cache_suffix
    }))
    .pipe(gulp.dest('./dist'))
});

gulp.task('default', ['bust-cache'], function() {});
```

Note that this can be easily achieved with <a href="https://github.com/hollandben/grunt-cache-bust">Grunt cache busting tool</a> or any other task runner. <a href="https://www.npmjs.com/package/gulp-buster">Gulp also has full plugins to bust cache</a>, though sometimes you end up with something completely custom just because you can. 

