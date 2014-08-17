---
layout: post
title: 快速定位ie6中的javascript错误
date: 2014-08-15 09:14
---




ie6出现js错误后，提示的行号，有些莫名其妙。

{% highlight js %}
// Example can be run directly in your JavaScript console

// Create a function that takes two arguments and returns the sum of those arguments
var adder = new Function("a", "b", "return a + b");

// Call the function
adder(2, 6);

// > 8
{% endhighlight %}
