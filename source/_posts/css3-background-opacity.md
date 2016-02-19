---
title: CSS3 Background Opacity
date: 2016-02-18 14:16:01
category:
- CSS
---
![CSS3 Background Opacity](/images/css3-background-opacity.jpg)

Here's something that I came across recently that proved incredibly useful. Most CSS experts out there are already going to know this one, but for those of you that are just learning, here's a quick tip that could help you out in the long run.

## Opacity Problem

What I needed was to set the background color of a div and then adjust its opacity to give it that cool see-through look. However, when setting the opacity property to something like 0.5 it adjusted the text inside the div along with the background. Not very cool.

Usual CSS block (sets opacity of box and text within it:

``` css
    .box {
        background-color: #000;
        opacity: 0.5;
    }
```

### Solution:

Here's the quick little snippet that I came across that is sure to save you a bunch of time: RGBA values.

Better to use:

``` css
    .box {
        background-color: rgba(0, 0, 0, 0.5);
    }
```

That's right. Set your background color using rgba. The syntax for this is: rgba(0, 0, 0, 0.5). Basically you set your red, green and blue values between 0 and 255. Then you set your opacity level just as you would with opacity such 0.5 for 50% opacity.

You can see an example of this in the following Codepen:

<p data-height="350" data-theme-id="0" data-slug-hash="RWjadj" data-default-tab="result" data-user="clintlosee" class='codepen'>See the Pen <a href='http://codepen.io/clintlosee/pen/RWjadj/'>RGBA Example</a> by Clint Losee (<a href='http://codepen.io/clintlosee'>@clintlosee</a>) on <a href='http://codepen.io'>CodePen</a>.</p>
<script async src="//assets.codepen.io/assets/embed/ei.js"></script>

The first box shows the RGBA example where the text still has no opacity level applied to it but the background has 50% opacity applied. The second box has the opacity set to 50% but it is applying to the box and text within, making them all lighter than what the intended outcome should be.

For the CSS veterans out there, this won't be anything new. But for those getting into CSS, it can be a huge help.
