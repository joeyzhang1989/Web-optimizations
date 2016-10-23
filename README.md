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

* Inline and identify the **Critical CSS** in the head tag by using the [penthouse](https://github.com/pocketjoso/penthouse).
* Move the scripts and links to the end of body tag.
* Added media, defer and async attribute to the CSS and JavaScript links.
* Compress images and minify the js files.

####Part 2: Optimize Frames per Second in pizza.html
* Inline and identify the **Critical CSS** in the head tag by using the [penthouse](https://github.com/pocketjoso/penthouse).
* Add the CSS attribute for the mover class in style.css to improve the render speed (composite independent layers)

```css
.mover {
  -webkit-transform: translateZ(0);
          transform: translateZ(0);
  will-change: transform;
  -webkit-backface-visibility: hidden;
          backface-visibility: hidden;
}
```
* Replace the querySelector and querySelectorAll with getElementsByClassName and getElementById for faster speed.
* Minify the main.js files, use the minified files for production.
* Delete the determineDx function and move sizeSwitcher(size) to changePizzaSizes(size),move the DOM selector out of loop

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

    for (var i = 0, l = randomPizzas.length; i < l ; i++) {
      randomPizzas[i].style.width = newWidth + "%";
    }
  }
```
* Move the 'mover' selector out of loop and declaring the phase variable in the initialisation of the for loop prevent it from being created every time the loop is executed
```JS
function updatePositions() {
  frame++;
  window.performance.mark("mark_start_frame");

  var items = document.getElementsByClassName('mover');
  var top = document.body.scrollTop / 1250;
  
  for (var i = 0, l = items.length, phase i < l ; i++) {
    phase = Math.sin(top + i % 5);
    items[i].style.left = items[i].basicLeft + 100 * phase + 'px';
  }
```
* Move the 'movingPizzas1' selector out of loop and generate the number of pizzas to draw based on the resolution of screen
```JS
document.addEventListener('DOMContentLoaded', function() {
  var lWidth = window.screen.width;
  var iHeight  = window.screen.height;
  var s = 256;
  var cols = lWidth / s;
  var rows = iHeight / s;                  // Generate pizza number based on screen resolution
  var pizzas = Math.floor(cols * rows);     // calculate the integer for pizzas using Math.floor function     
  var movingPizzas = document.getElementById('movingPizzas1');
  for (var i = 0, elem; i < pizzas; i++) {
    elem = document.createElement('img');
    elem.className = 'mover';
    elem.src = "images/pizza.png";
    elem.style.height = "100px";
    elem.style.width = "73.333px";
    elem.basicLeft = (i % cols) * s;
    elem.style.top = (Math.floor(i / cols) * s) + 'px';
    movingPizzas.appendChild(elem);
  }
  updatePositions();
});
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

