---
layout: post
title: Jekyll Test Post
date:   2016-02-26 09:28:01 -0700
categories: jekyll test metalsmith
published: false
---
Hi, this is my second blog post.

# Header 1

## Header 2

- List item 1

{% highlight javascript %}
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
    // .use(htmlMinifier())
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
{% endhighlight %}
