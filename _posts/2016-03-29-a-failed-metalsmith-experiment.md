---
layout: post
title: A Failed Metalsmith Experiment
date:   2016-03-29 15:00:00 -0700
categories: jekyll metalsmith
---
It's a bit hard to believe that my first blog post here is a story of failure, but I've learned not to care, so here goes.<!--more-->

I initially started working on this site several months ago as a place to share stories about my personal journey into the world of software development. In the past I tinkered with various blogging platforms such as WordPress, Kirby, Blogger (long ago), and a variety of lesser known services and frameworks. Every thing I tried felt overly complicated for my needs, bloated, or some combination of the two. Until I came across [Metalsmith](http://www.metalsmith.io/). 

If you followed that link, you'll have likely seen that Metalsmith bills itself as "An extremely simple, pluggable static site generator." This is mostly true. Metalsmith was extremely easy to get the hang of and reminded me a great deal of [Gulp](http://gulpjs.com). While this isn't intended to be a tutorial on creating a Metalsmith site, I would like to walk through a bit of the setup for Metalsmith. 

Metalsmith comes in both API and CLI flavors. I opted for the API flavor. This meant creating a build.js file that would be referenced and used by Metalsmith similarily to a gulpfile.js. After npm installing metalsmith, I had to decide which plugins would be needed. After lots of research and tinkering I ultimately decided on the plugins below, installed them as dev dependencies, and required them in my build.js file.

``` javascript
var Metalsmith    = require('metalsmith'),
    markdown      = require('metalsmith-markdown'),
    htmlMinifier  = require('metalsmith-html-minifier'),
    layouts       = require('metalsmith-layouts'),
    autoprefixer  = require('metalsmith-autoprefixer'),
    cleanCSS      = require('metalsmith-clean-css'),
    concat        = require('metalsmith-concat'),
    drafts        = require('metalsmith-drafts'),
    excerpts      = require('metalsmith-excerpts'),
    collections   = require('metalsmith-collections'),
    permalinks    = require('metalsmith-permalinks'),
    beautify      = require('metalsmith-beautify'),
    branch        = require('metalsmith-branch');
```

Chaining all of these plugins together to do something useful resulted in the code below.

``` javascript
Metalsmith(__dirname)
    .metadata({
      site: {
        title: 'ajc.la',
        url: 'https://ajc.la'
      }
    })
    .use(drafts())
    .use(markdown({
      smartypants: false,
      gfm: true,
      tables: true
    }))
    .use(excerpts())
    .use(collections({
      posts: {
        pattern: 'posts/**.html',
      }
    }))
    .use(branch('posts/**.html')
      .use(permalinks({
        pattern: 'posts/:title',
        relative: false
      }))
    )
    .use(layouts('jade'))
    .use(htmlMinifier())
    .use(autoprefixer())
    .use(concat({
      files: ['styles/normalize.css','styles/icomoon.css','styles/style.css','styles/solarized-dark.min.css'],
      output: 'styles/app.min.css'
    }))
    .use(cleanCSS({
      files: 'styles/**/*.css'
    }))
    .use(beautify())
    .build(function(err) {
      if (err) {
        throw err;
      } else {
        console.log("Build complete");
      }
    });
```

As you may be able to infer from the code above, Metalsmith can be great for highly customizing very simple sites. Unfortunately, the larger the site grows the more difficult it becomes to maintain the Metalsmith build file, not that it can't be done. 

Instead of going into elaborate detail about what the code above does in the Metalsmith pipeline, I'll save that for a future blog post. In the end I decided to power this site with Jekyll, primarily for the extremely simple integration with [Github Pages](https://pages.github.com/), which I also plan to write about in the future.

If Metalsmith looks like something that could possibly be useful to you then I would highly encourage you to dig into it a bit. It's relatively simple to get started and can be really fun to play with. There are also some very powerful plugins that will allow you to elevate the functionality well beyond what Jekyll and many other static site/blog generators are capable of.

Expect much more to come on this site in the future. Good luck and feel free to reach out to me anytime via [email](mailto:andrew@ajc.la) or <a href="https://twitter.com/corc" target="_blank">Twitter</a>!