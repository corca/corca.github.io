---
layout: post
title: A Work in Progress
date:   2016-02-27 09:28:01 -0700
categories: jekyll metalsmith test
published: false
---
This page is currently under development.

# Header 1

## Header 2

### Header 3

#### Header 4

##### Header 5

###### Header 6

- List item 1
- List item 2
- List item 3

A sentence with **strong** *emphasis* and __more__ _emphasis_.

Some **combined _emphasis_**.

Strike ~~that~~.

1. List item 1
2. List item 2
3. List item 3

[I'm an inline-style link](https://www.google.com)

[I'm an inline-style link with title](https://www.google.com "Google's Homepage")

[I'm a reference-style link][Arbitrary case-insensitive reference text]

[I'm a relative reference to a repository file](../blob/master/LICENSE)

[You can use numbers for reference-style link definitions][1]

[arbitrary case-insensitive reference text]: https://www.mozilla.org

[1]: http://slashdot.org

[link text itself]: http://www.reddit.com

Inline-style:
![alt text](https://github.com/adam-p/markdown-here/raw/master/src/common/images/icon48.png "Logo Title Text 1")

Reference-style:
![alt text][logo]

[logo]: https://github.com/adam-p/markdown-here/raw/master/src/common/images/icon48.png "Logo Title Text 2"

How about some `inline code` to look at?

> Or maybe some blockquotes
> Fap asymmetrical cliche, knausgaard tofu schlitz mlkshk street art messenger bag listicle cardigan sriracha shabby chic. Banjo heirloom distillery, disrupt ramps kombucha shoreditch jean shorts knausgaard next level craft beer plaid paleo lo-fi fashion axe. Tote bag blue bottle bicycle rights dreamcatcher, everyday carry slow-carb gastropub bespoke kale chips fingerstache. Before they sold out literally ethical, swag raw denim cold-pressed mumblecore everyday carry authentic. Meh everyday carry 8-bit, keytar kombucha tumblr sustainable street art freegan knausgaard. Pour-over deep v poutine, sriracha tilde tofu 90's mixtape locavore vinyl intelligentsia meggings. Occupy cred direct trade, taxidermy raw denim chicharrones keffiyeh.

```js
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
