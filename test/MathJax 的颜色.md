# 改变 Mathjax 的颜色

----
## 第一种方法，Markdown

    \( \color{red}{ \sigma(y-x) } \) 

## 第二种方法，修改配置

config/MathJax.js 

     MathJax.Hub.Config({
       styles: {
         ".MathJax": {
           color: "#CC5522"
         }
       }
     });

但不能修改字体。字体由 MathJax 自己内部管理。

## 第三种方法，修改CSS

CSS stylesheet

    math, .MathJax {
        color: orange;
    }

错误的定义

    math, .MathJax {
        font-style: italic;
    }
for HTML-CSS; the font-style will still be normal.

MathJax sets the font and style of the individual characters itself, according to the rules of mathematical typesetting as implemented by TeX. You can not use CSS to change that, in general (but you can change some other CSS, like the color, as you have found). The usual way to typeset mathematics is to set variables in italics, but function names (like "sin") in an upright font, so \sin x will use normal for part of it and italics for part. A single CSS rule can't be used to handle that.

If you wish to affect the fonts within the mathematics, you would need to use one of the font commands in TeX or LaTeX, such as \rm, \it, or \bf, or \mathrm, \mathit, etc.

I'm not quite sure what you mean by the font-style will be normal, because it is not normal for many things, like variable names, for which it is italics by default. Perhaps if you were clearer about what output you are trying to produce (i.e., what you are trying to change about the default output), we could give you better advice on how to accomplish that.

## CSS Style Objects
Many MathJax components allow you to specify CSS styles that control the look of the elements they create. These are described using CSS style objects, which are JavaScript objects that represent standard CSS declarations. The main CSS style object is a collection of name:value pairs where the name is the CSS selector that is being defined, and the value is an object that gives the style for that selector. Most often, the selector will need to be enclosed in quotation marks, as it will contain special characters, so you would need to use "#myID" rather than just #myID and "ul li" rather than just ul li.

The value used to define the CSS style can either be a string containing the CSS definition, or a javascript object that is itself a collection of name:value pairs, where the name is the attribute being defined and value is the value that attribute should be given. Note that, since this is a JavaScript object, the pairs are separated by commas (not semi-colons) and the values are enclosed in quotation marks. If the name contains dashes, it should be enclosed in quotation marks as well.

For example, jax/output/HTML-CSS/config.js includes the following declaration:

    styles: {
    
        ".MathJax_Display": {
            "text-align": "center",
            margin:       "1em 0em"
        },

        ".MathJax .merror": {
            "background-color": "#FFFF88",
            color:   "#CC0000",
            border:  "1px solid #CC0000",
            padding: "1px 3px",
            "font-style": "normal",
            "font-size":  "90%"
        }

    }
    
This defines two CSS styles, one for the selector .MathJax_Display, which specifies its text alignment and margin settings, and a second for .MathJax .merror, which specifies a background color, foreground color, border, and so on.

You can add as many such definitions to a styles object as you wish. Note, however, that since this is a JavaScript object, the selectors must be unique (e.g., you can’t use two definitions for "img", for example, as only the last one would be saved). If you need to use more than one entry for a single selector, you can add comments like ``/* 1 */ and /* 2 */`` to the selector to make them unique.

It is possible to include selectors like "@media print", in which case the value is a CSS style object. For example:

    styles: {
        "@media print": {
            ".MathJax .merror": {
                "background-color": "white",
                border: 0
            }
        }
    }
    
The various extensions and output processors include more examples of CSS style objects, so see the code for those files for additional samples. In particular, the ''extensions/MathMenu.js, extensions/MathZoom.js, extensions/FontWarnsing.js, and jax/output/HTML-CSS/jax.js files include such definitions.    ''

## Way to change the font color of SVG output with Mathjax

You can use CSS to do this.  Here is an example: 

    <!DOCTYPE html> 
    <html> 
        <head> 
            <title>Use CSS to color SVG output</title> 
            <script type="text/x-mathjax-config"> 
                MathJax.Hub.Config({ 
                    jax: ["input/MathML","output/SVG"], 
                    extensions: ["mml2jax.js"] 
                }); 
            </script> 
            <script type="text/javascript" src="../MathJax/MathJax.js"></script> 
            <style> 
                .colored .MathJax_SVG SVG > g, 
                .colored .MathJax_SVG_Display SVG > g { 
                    fill: #F00; 
                    stroke: #F00; 
                } 
            </style> 
        </head> 
        <body> 
            <div class="colored"> 
                <math> 
                    <mi>x</mi><mo>+</mo><mn>1</mn> 
                </math>
            </div> 
            <div> 
                <math> 
                    <mi>x</mi><mo>+</mo><mn>1</mn> 
                </math> 
            </div> 
        </body> 
    </html> 

Well, it worked in IE9 when I wrote it.  But it does appear that IE10 and IE11 have trouble with it.

It turns out that the issue is in capitalization.  The SVG should be lower case for it to match the SVG tag in IE10+.  So it should be

    <style> 
        .colored .MathJax_SVG svg > g, 
        .colored .MathJax_SVG_Display svg > g { 
            fill: #F00; 
            stroke: #F00; 
        } 
    </style>

instead.  At least that works for me.
