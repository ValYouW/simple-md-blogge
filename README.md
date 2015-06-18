# simple-md-blogger
Simple markdown parser to be used with Blogger.

This is a small script that can parse few markdown features into html, this is very handy for using with Blogger, the supported features are:

1. Titles - Easily mark a line as title using hash(es) (`#`)
2. Fenced code blocks - Wrap the code between 3 backticks (<code>```</code>) and it will be parsed into &lt;pre>&lt;code>  tags.
3. Code quotes - Wrap any characters between single backticks (<code>`</code>) and it will be parsed in a &lt;code> tag
4. Links - Create links using this pattern: \[text\](url){target}

An example blog post, with explanation of the code, can be found on my [blog](http://www.valyouw.com/2015/06/test-md.html).

##Usage
The script exposes one method on the `VYW` namespace.
### VYW.parse(postClass)
* `postClass {string}` - The CSS class of the blog posts, it will select all posts and parse them. `Deafult: post-body`

## Known Issues
* A single escaped backtick, followed by another non-escaped backtick, on the same line, won't work (no easy way for lookbehind regex in javascript)

## Benchmark
Checkout this [jsperf](http://jsperf.com/vyw-md-parsing)