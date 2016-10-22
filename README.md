## Website Performance Optimization portfolio project

This project aims to optimize and improve the webpage load speed based on critical rendering path, render blocking and other concepts to improve the webpage
speed and make the animation effect within the 60 fps require according to the optimization on HTML,CSS and JavaScript. Original code is from the Udacity front-end developer nano degree program's repository [frontend-nanodegree-mobile-portfolio](https://github.com/udacity/frontend-nanodegree-mobile-portfolio). 

### Getting started
##### Live demo on Github Page: [Website Performance Optimization](https://joeyzhang1989.github.io/Web-optimizations/). 
##### Locally

**1.** Clone this repo:

```
$ git clone https://github.com/joeyzhang1989/Web-optimizations.git
````

**2.** Serve the application:


###### Python 2

```bash
$ python -m SimpleHTTPServer 

```
###### Python 3 

```bash
$ python3 -m http.server.   
```
You can use the Python SimpleHTTPServer to serve this webpage game on your local machine.

**3.** Open the application:

```bash
$ open "http://localhost:8000"
```

### Optimized parts

####Part 1: Optimize PageSpeed Insights score for html files [PageSpeed Tools](https://developers.google.com/speed/pagespeed/insights/)

1. Inline and identify the **Critical CSS** in the head tag by using the [penthouse](https://github.com/pocketjoso/penthouse).
1. Move the scripts and links to the end of body tag.
1. Added media, defer and async attribute to the CSS and JavaScript links.
1. Compress images and minify the js files.

####Part 2: Optimize Frames per Second in pizza.html
1. Inline and identify the **Critical CSS** in the head tag by using the [penthouse](https://github.com/pocketjoso/penthouse).
2. Add the CSS attribute for the mover class in style.css to improve the render speed (composite independent layers)

```css
.mover {
  transform: translateZ(0);
  will-change: transform;
  backface-visibility: hidden;
}"
```
3. Replace the querySelector and querySelectorAll with getElementsByClassName and getElementById for faster speed.
4. Minify the main.js files, use the minified files for production.
5. Delete the determineDx function and move sizeSwitcher(size) to changePizzaSizes(size),move the DOM selector out of loop

```JS
function changePizzaSizes(size) {
    switch(size) {
      case "1":
        newWidth = 25;
        break;
      case "2":
        newWidth = 33.3;
        break;
      case "3":
        newWidth = 50;
        break;
      default:
        console.log("bug in sizeSwitcher");
    }

    var randomPizzas = document.getElementsByClassName("randomPizzaContainer");

    for (var i = 0; i < randomPizzas.length; i++) {
      randomPizzas[i].style.width = newWidth + "%";
    }
  }
}"
```
6. Added getRandomIntInclusive function to generate random integer number from 0-4, and update the updatePositions function
```JS
function updatePositions() {
  frame++;
  window.performance.mark("mark_start_frame");

  var items = document.getElementsByClassName('mover');

  function getRandomIntInclusive(min, max) {
    min = Math.ceil(min);
    max = Math.floor(max);
    return Math.floor(Math.random() * (max - min + 1)) + min;
  }
  
  for (var i = 0; i < items.length; i++) {
    var randomNumber = getRandomIntInclusive(0,4);
    var phase = Math.sin((document.body.scrollTop / 1250) + randomNumber);
    items[i].style.left = items[i].basicLeft + 100 * phase + 'px';
  }
```
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

##License
This project is a public domain work, dedicated using
[MIT](https://opensource.org/licenses/MIT). Feel free to do
whatever you want with it.

