# Browser Compatibility
*Jeff Burtoft*

When you are writing an web app, whether it be for the browser or targeting devices, browser compatibility is one of the most important aspects of development. Let's start by defining what we mean by browser compatibility—and to do that, let's start by clarifying what it is not: 
 
1. Browser compatibility isn't just about writing code that works on your preferred platform. 
1. Browser compatibility isn't making an identical experience for all users. 
1. Browser compatibility isn't directing users to change to a different or "more modern" browser in order to access your site. 
 
In its simplest term, browser compatibility is making sure your experience is accessible to all browsers, including browsers that haven't even shipped yet. This implies a few things. It might mean that you want to practice progressive enhancement so that you're supporting older browsers at the same time as supporting the latest and greatest version of each browser. At the minimum, it means that you don't have blatant bugs and that you don’t block particular browsers because they don't support a cutting-edge feature or weren't part of your test matrix. 
 
I've developed apps and worked with developers to build apps that target platforms specifically, rather than the browser. I work with a fantastic framework called Manifoldjs that lets you build hosted web apps to be released in app stores. In this area, where developers may assume they can let down their guard when it comes to browser compatibility, it's equally important, if not more important to make sure your code is cross browser compliant. Here's why: 
 
1. Modern platforms are evergreen. In platforms like Windows 10 and Android, your webview will get updates, sometimes more often than the browser. This means that the environment that runs your app may change on you (what does that remind you of?). 
 
1. Older platforms vary drastically in feature support. You may have cheered the day IE6 dropped off the usage chart (has that happened yet?), but that's onlyactually only a fraction of users compared to users on older versions of Android. And these old versions of Android also have old, ugly versions of the Android webview that are barely considered HTML5. Android is not just one runtime. 
 
What's the key to writing code that works in any browser and on any platform? It comes in three parts:

**Standards**: If you're writing to web standards, you'll be sure that you code continues to work even as the web changes and grows.

**Feature detection**: You need to execute code based on what your run time environment can support. If you're still delivering code based on a user agent string, then you're probably providing sub-par experiences across the board, and your code is not future-proof.

**Polyfills**: Don’t block a user because their browser doesn't support the latest and greatest. Give it to them with a polyfill and let them use most of your app instead of none of it. 
 
Luckily for us, it's easier than ever to make sure your code performs well for all of your users. Let's dig into each of these keys for more details. 
 
## Standards

Web standards are a great way to make sure that the code you write today will continue to perform for users for a long time to come. When you write code to the standards, even if a browser doesn't support it today, there is a strong likelihood that they will support it in the future. Additionally, writing standards based code is the basis to feature detection and polyfills, without standards, there is no point on doing the other two. 
There are a number of great tools out there today that help you check your code as you develop, so there are no surprises at the end:

### npm Packages to try
> ## JSLint
How to install: `npm install -g jslint`
 
> External requirements: none, all dependencies are installed by npm 
 
> What does it do: JSLint will run against your JavaScrit code to make sure it's standards complient as well as not breaking any of the "JS Lint" rules for good development 
 
> Usage Example: 
Use the default jslint 
```
> jslint lib/color.js 
```
> Pull it into your code with require: 
```JavaScript
var LintStream = require('jslint').LintStream; 
```
 
> More info at https://www.npmjs.com/package/jslint 

## Feature Detection

There are two approaches to determining if your user's browser can support the code you want to run. The first is browser detection, in which you determine the browser based on the user agent and then deliver code that you think will work on that browser. This method doesn't keep up with the ever changing web and funnels users into browser profiles that often represent a group of browsers and versions. This almost always results in users getting a less than optimal experience, as browser profiles get out-of-date very quickly, and aren't always correct. 
 
The second method, clearly preferred by the community, is that of feature detection. In this approach, you test for an existing feature before you try to use it. If the feature test works, execute the code, if it doesn't, then use a polyfill or alternate experience. You can see why this is preferred as it doesn't get out-of-date (when the browser starts supporting a standard, then the code detects it, and the native implementation is used) and it allows you to utilize features whenever possible, not just when the browser profile allows it.

![picture0](https://cloud.githubusercontent.com/assets/3271834/10375099/796403e2-6dab-11e5-9f18-a11f02dc77b3.png)
<sub>*Modernizr makes it easy to respond to your user's browser features*</sub>

### npm Packages to try

> ## Modernizr
How to install: `npm install -g modernizr`
External requirements: none, all dependencies are installed by npm 
 
> What does it do: Modernizr can be added to your website to provide simple, community tested feature detection. Modernizr lets you limit the tests you run to only the ones you need, so it's light, quick and focuses on tests you want to run. 

> Usage Example:
```JavaScript
var modernizr = require("modernizr");
modernizr.build({}, function (result) {
console.log(result); // the build
}); 
```

> More info at: https://www.npmjs.com/package/modernizr

> Modernizr is pretty much the gold standard for doing feature detection. It's own description says it best: "Modernizr makes it easy to deliver tiered experiences: make use of the latest and greatest features in browsers which support them, without leaving less fortunate users high and dry."

## Polyfills

It's wonderful to know what a user's browser supports and doesn't support, but what do you do when the browser doesn't support a feature that you need? In comes the polyfill. A polyfill is extra code you add to your website that backfills missing functionality. When the real API exists, it will use that; and when it doesn't, the polyfill will execute and approximate the missing functionality. Polyfills, are in a way, a nexus of the different keys to browser compatibility. In order to support different browsers that need different features, you use polyfills to provide a consistent feature set. To know when the polyfill should be utilized, you use feature detection to determine it. It's the circle of "Browser Compatibility Life." 
 
Polyfills allow you to use modern web patterns in older browsers, or even across modern browsers that each support different sets of web standards. There are many, many polyfills that target one particular feature, but there are also some frameworks that handle it from a Macro Level. FT Labs, the team that brought some of the most popular (like [FastClick](https://github.com/ftlabs/fastclick)) and most complex (like appcache primer) tools, have expanded into an entire service of polyfills. The good news is, it's all available here on npm.

![picture1](https://cloud.githubusercontent.com/assets/3271834/10375100/7a8b3da8-6dab-11e5-8265-04654ffafc34.png)
<sub>*Polyfill.io will help meet many of your polyfill needs*</sub>

### npm Packages to try
> ## polyfill-service using Polyfill.io
> How to install:

> 1. Add it to your `package.json` as a dependency: `npm install polyfill-service --save`
> 1. Rebuild your project using `npm install`
> 1. Use this API from your code

> External requirements: none, all dependencies are installed by npm 
 
> What does it do: Makes web development less frustrating by selectively polyfilling just what the browser needs.

> Usage Example:
```JavaScript
require('polyfill-service').getPolyfillString({
    uaString: 'Mozilla/5.0 (Windows; U; MSIE 7.0; Windows NT 6.0; en-US)',
    minify: true,
    features: {
        'Element.prototype.matches': { flags: ['always', 'gated'] },
        'modernizr:es5array': {}
    }
}).then(function(bundleString) {
    console.log(bundleString);
});
```
> More info at: https://www.npmjs.com/package/polyfill-service 

Building Web apps that work across every platform and every browser is easier than it's ever been. When you start with standard code, properly feature detect your functionality, and then implement quality polyfills, you can build incredible experiences for all your users. This list of packages are just a few of the amazing tools available on NPM to help you build great experiences for your users.