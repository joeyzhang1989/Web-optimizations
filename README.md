## Website Performance Optimization portfolio project

This project aims to optimize and improve the webpage load speed based on critical rendering path, render blocking and other concepts to improve the webpage
speed and make the animation effect within the 60 fps require according to the optimization on HTML,CSS and JavaScript. Original code is from the Udacity front-end developer nano degree program's repository [frontend-nanodegree-mobile-portfolio](https://github.com/udacity/frontend-nanodegree-mobile-portfolio). 

### Getting started
##### Live demo on Github Page:[Website Performance Optimization](https://joeyzhang1989.github.io/Web-optimizations/). 
##### Locally

**1.** Clone this repo:

```
$ git clone https://github.com/joeyzhang1989/Web-optimizations.git
````

**2.** Serve the application:

```
###### Python 2
$ python -m SimpleHTTPServer 
###### Python 3 
$ python3 -m http.server.   ```
You can use the Python SimpleHTTPServer to serve this webpage game on your local machine.

**3.** Open the application:

```
$ open "http://localhost:8000"
```

### Optimized parts

####Part 1: Optimize PageSpeed Insights score for html files

1. Inline and identify the **Critical CSS** in the head tag by using the [penthouse](https://github.com/pocketjoso/penthouse).
1. Move the scripts and links to the end of body tag.
1. Added media, defer and async attribute to the CSS and JavaScript links.
1. Compress images and minify the js files.


####Part 2: Optimize Frames per Second in pizza.html


### Optimization Tips and Tricks
* [Optimizing Performance](https://developers.google.com/web/fundamentals/performance/ "web performance")
* [Analyzing the Critical Rendering Path](https://developers.google.com/web/fundamentals/performance/critical-rendering-path/analyzing-crp.html "analyzing crp")
* [Optimizing the Critical Rendering Path](https://developers.google.com/web/fundamentals/performance/critical-rendering-path/optimizing-critical-rendering-path.html "optimize the crp!")
* [Avoiding Rendering Blocking CSS](https://developers.google.com/web/fundamentals/performance/critical-rendering-path/render-blocking-css.html "render blocking css")
* [Optimizing JavaScript](https://developers.google.com/web/fundamentals/performance/critical-rendering-path/adding-interactivity-with-javascript.html "javascript")
* [Measuring with Navigation Timing](https://developers.google.com/web/fundamentals/performance/critical-rendering-path/measure-crp.html "nav timing api"). We didn't cover the Navigation Timing API in the first two lessons but it's an incredibly useful tool for automated page profiling. I highly recommend reading.
* <a href="https://developers.google.com/web/fundamentals/performance/optimizing-content-efficiency/eliminate-downloads.html">The fewer the downloads, the better</a>
* <a href="https://developers.google.com/web/fundamentals/performance/optimizing-content-efficiency/optimize-encoding-and-transfer.html">Reduce the size of text</a>
* <a href="https://developers.google.com/web/fundamentals/performance/optimizing-content-efficiency/image-optimization.html">Optimize images</a>
* <a href="https://developers.google.com/web/fundamentals/performance/optimizing-content-efficiency/http-caching.html">HTTP caching</a>


