---
title: The FizzBuzz Test
date: 2015-12-22 03:37:32
intro:
category: JavaScript
tags:
- Development
---
![The FizzBuzz Test](/blog/images/The FizzBuzz Test - Couple Riding Bikes.jpg)

The more and more I read and find new things to learn to help progress my web development career, the more I come across one of the many tests given to programmers in the interview stage: __The FizzBuzz test__.

## What is the FizzBuzz Test?

Writing a simple program is one of the things I've found that are necessary to grasp the basic skills of a language. That is where the FizzBuzz test comes in. The FizzBuzz test is where you are tasked with writing a program that prints the numbers from 1 to 100. But for multiples of three print "Fizz" instead of the number and for the multiples of five print "Buzz". For numbers which are multiples of both three and five print "FizzBuzz".

This sounds easy enough, but when I first attempted it I got stuck. So more reading and more research helped me through this and I came up with as basic example solution:

``` javascript
for (var i = 1; i &lt;= 100; i++) {
    if (i % 15 == 0) {
        console.log('FizzBuzz');
    } else if (i % 3 == 0) {
        console.log('Fizz');
    } else if (i % 5 == 0) {
        console.log('Buzz');
    } else {
        console.log(i);
    }
}
```

And after more researching, I came across an even more consolidated and concise version of the above:

``` javascript
for (var i = 1; i &lt;= 100; i++) {
    var f = i % 3 == 0, b = i % 5 == 0;
    console.log(f ? b ? "FizzBuzz" : "Fizz" : b ? "Buzz" : i);
}
```

It still takes me a few times reading through that last version to fully grasp how it is doing what it is in only four lines of code compared to 11. It's always great to see differing versions of how to solve the same concept.

If you're trying to get the basics of JavaScript down and are looking for some coding exercises, I highly recommend looking into tests such as __the FizzBuzz Test__ as well and the many JavaScript assessments and articles regarding [JavaScript interview questions](https://medium.com/javascript-scene/10-interview-questions-every-javascript-developer-should-know-6fa6bdf5ad95). They have helped me out tremendously in my journey.
