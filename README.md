# simple-md-blogger
Simple markdown parser to be used with Blogger.

This is a small script that can parse few markdown features into html, this is very handy for using with Blogger, the supported features are:

1. Titles - Easily mark a line as title using hash(es) (`#`)
2. Fenced code blocks - Wrap the code between 3 backticks (<code>```</code>) and it will be parsed into &lt;pre>&lt;code>  tags.
3. Code quotes - Wrap any characters between single backticks (<code>`</code>) and it will be parsed in a &lt;code> tag

An example blog post, with explanation of the code, can be found on my [blog](http://www.valyouw.com/2015/06/test-md.html).

##Usage
The script exposes one method on the `VYW` namespace.
### VYW.parse(postClass, method)
* `postClass {string}` - The CSS class of the blog posts, it will select all posts and parse them. `Deafult: post-body`
* `method {string}` - In the blog post I describe 2 methods for parsing the html
    * `regex` - Parse the entire post using a sequence of regular expressions, this requires to escape all backticks written in code blocks.
    * `array` - Default. Splitting the post into array of lines, and then parse each line using regex.
    This method does not require to escape backticks in code blocks, it does require to escape a sequence of 3 backticks (otherwise it will think this is the end of the code block).

## Benchmark
Checkout this [jsperf](http://jsperf.com/vyw-md-parsing)