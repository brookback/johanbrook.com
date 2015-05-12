---
title: 'CSS variables soon to land in WebKit'
link: 'http://trac.webkit.org/browser/trunk/LayoutTests/fast/css/variables/colors-test.html'
date: '2012-05-18 18:03'
tags:
  - CSS
  - CSS3
  - variables
  - Webkit
  - experimental
category: CSS
---

CSS variables are powerful and almost vital for me nowadays. They are supported in SCSS, LESS and Stylus (all preprocessors). But now WebKit now seem to be on its way of implementing a pure CSS version:

    -webkit-var-foreground: green;
    -webkit-var-background: rgb(255, 255, 255);
    
    color: -webkit-var(foreground);
    background-color: red;
    background-color: -webkit-var(background);
[I've written about a CSS variable implementation before](http://johanbrook.com/design/css/webkit-css-variables-mixins-nesting/), and even back then I noted that the proposed syntax is bulky and ugly. In the example above you'll note verbosity and even a vendor prefix (!). 

    $foreground: green;
    $background: rgb(255,255,255);
    
    color: $foreground;
    background-color: red;
    background-color: $background;