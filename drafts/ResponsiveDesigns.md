# Why Responsive?
*Jacob Thornton*
 
As a developer, you want your audience to have the absolute best experience possible, no matter their device, their location, the quality of their connection, etc. That’s why today, as loads of people move to browsing the web on phones and tablets, it’s more important than ever for us to be mindful of how we structure and deliver our content. 
 
One strategy which, over the last several years, has gained a lot of momentum is called “responsive design”. Responsive design makes use of CSS media queries, fluid grids, and flexible media to adapt the visual design of a web interface to the dimensions of a consumer’s viewport. A media query, if you’re unfamiliar, is a declarative CSS statement that allows you to apply a collection of CSS rule sets when a given condition is met. (http://www.w3.org/TR/css3-mediaqueries/#media0) 
 
For example, the following CSS statement would apply a background color of salmon to an element classified as "container" in the screen medium, when the screen width of the viewport is 500px or larger: 

```CSS
@media screen and (min-width: 500px) {  
    .container { background-color: salmon; } 
}
```
 
Building on this technology, several library and framework authors have released projects to make architecting responsive applications even easier. One such example is the Bootstrap web framework. Bootstrap aims to make your life easier by providing baseline implementations of many of the most popular components on the web today (like buttons, forms, navigational elements), as well as a super powerful grid system, and a bunch of helpful utilities — all of which are completely responsive. 
 
Depending on the scope of your project, Bootstrap can save you countless hours and get you up and running incredibly fast. There are [examples](http://getbootstrap.com/getting-started/) of common layouts as well as new “[themed toolkits](http://themes.getbootstrap.com/collections/all)” which offer even more components and ideas for specific types of projects like dashboards, marketing pages, and web apps.

### npm Packages to try
> ## Bootstrap 3.0
How to install: `npm install bootstrap`
 
> External requirements: none, all dependencies are installed by npm 
 
> Usage Example: 
Add the following to your website's markup
```HTML
<!-- Latest compiled and minified CSS --> 
<link rel="stylesheet" href="node_modules/bootstrap/3.3.5/css/bootstrap.min.css"> 
<!-- Optional theme --> 
<link rel="stylesheet" href="node_modules/bootstrap/3.3.5/css/bootstrap-theme.min.css"> 
<!-- Latest compiled and minified JavaScript --> 
<script src="node_modules/bootstrap/3.3.5/js/bootstrap.min.js"></script>  
```
 
> More info at https://www.npmjs.com/package/bootstrap
 
There are also many tools out there that help you with one particular aspect of your responsive design as well. One of best is "imager.js" which was actually built out of the BBC. Imager.js helps you load responsive images, it loads the best image for the device without loading excess content.

### npm Packages to try
> ## Imager.js
How to install: `npm install imager.js`
 
> External requirements: none, all dependencies are installed by npm 

> What does it do: Imager.js is an alternative solution to the issue of how to handle responsive image loading, created by developers at BBC News.
 
> Usage Example: 
```HTML
<div style="width: 240px"> 
<div class="delayed-image-load" data-src="http://placehold.it/{width}" data-alt="alternative text"></div> 
</div> 
<script> 
new Imager({ availableWidths: [200, 260, 320, 600] }); 
</script>  
```
> This will result in the following HTML output:
```HTML
<div style="width: 240px"> 
<img src="http://placehold.it/260" data-src="http://placehold.it/{width}" alt="alternative text" class="image-replace"> 
</div> 
<script> 
new Imager({ availableWidths: [200, 260, 320, 600] }); 
</script> 
```
 
> More info at https://www.npmjs.com/package/imager.js

For more information about responsive design, and responsive design tooling, check out the following: 
 
http://alistapart.com/article/responsive-web-design 

https://responsivedesign.is/podcasts/rwd-podcast-episode-18-aaron-gustafson 

https://www.aaron-gustafson.com/notebook/where-do-we-go-from-here/