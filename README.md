# simple-md-blogger
Simple markdown parser to be used with Blogger ([explanation post](http://www.valyouw.com/2015/06/test-md.html))

This is a small script that can parse few markdown features into html, this is very handy for using with Blogger, the supported features are:

1. Titles - Easily mark a line as title using hash(es) (`#`)
2. Fenced code blocks - Wrap the code between 3 backticks (<code>```</code>) and it will be parsed into &lt;pre>&lt;code>  tags.
3. Code quotes - Wrap any characters between single backticks (<code>`</code>) and it will be parsed in a &lt;code> tag
4. Links - Create links using this pattern: \[text\](url){target}

An example blog post, with explanation of the code, can be found on my [blog](http://www.valyouw.com/2015/06/test-md.html).

##Usage
The script exposes one method on the `VYW` namespace.
### VYW.parse(postClass)
* `postClass {string}` - The CSS class selector of the blog posts, it will select all posts and parse them. `Deafult: .post-body`

### Adding to a Blogger blog
In order to use this in your blog:

* Edit your blog's template HTML
* Find the &lt;head> tag and add the following script:
```html
<script src='//cdn.rawgit.com/ValYouW/simple-md-blogger/8a142bd56bd29221e5a73e746f49462b7046ebc4/blogger-md.js'/>
```
* Then add a script tag that will parse the blog posts when the page loads:
```html
<script type='text/javascript'>
document.addEventListener(&quot;DOMContentLoaded&quot;, function(event) {
    // NOTE: Check what is the CSS class of the posts in your blog
    var postsSelector = '.post-body';
    window.VYW.parse(postsSelector);
    // If you have some library to format code blocks (like highlight.js), call it now.
});
</script>
```
* Titles are converted to &lt;h1> &lt;h2> etc tags, you can set the style for those tags as the default might not suit your needs, for example I added the following style tag:
```css
<style type='text/css'>
.post-body h2 {
    font-size: 1.5em;
    font-weight: bold;
}
.post-body h3 {
    font-size: 1.2em;
    font-weight: bold;
}
</style>
```

## Known Issues
* A single escaped backtick, followed by another non-escaped backtick, on the same line, won't work (no easy way for lookbehind regex in javascript)

## Benchmark
Checkout this [jsperf](http://jsperf.com/vyw-md-parsing)