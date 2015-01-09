---
layout: post
title: How D3 gets the job done
comments: true
---

![Image]({{ site.baseurl }}/images/d3-js.png)

<br /> <br /> <br />
&nbsp;&nbsp;&nbsp;&nbsp;For those that have yet to discover the multi-color awesomeness that is D3.js let me explain. D3.js is a data visualization library for javascript that makes graphing data points extremely simple. D3 also comes with a bunch of useful commands like "scale" that will scale your data points within the pixel range of the svg element automatically. Let's not forget the "transition" method and the "delay" attribute that allows us to create animations and control the time it takes to start making movements more realistic.
<br /> <br />
&nbsp;&nbsp;&nbsp;&nbsp;One of the many features I found particulary interesting was the "enter" method. D3 makes it easier to add items to a page when they are not there. When chaining together methods to add an element anywhere on the page you must declare the dataset you wish to use and the use the enter method. D3 will use the length of the dataset as the number of times to loop through the selecting of appending. See code below: 
<br /> <br />
## Code

{% highlight javascript %}
var svg = d3.select('body')
			.append('svg')
			.attr('w',1000)
			.attr('h',1000);
var data = [13, 100, 28, 40, 30];
svg.selectAll("circle")
			.data(data)
			.enter()
			.append("circle")
			.attr('cx', 50)
			.attr('cy', 50)
			.attr('r', 5)
			.attr("fill", "black" );

			
svg.selectAll("circle")
			.transition()
			.attr('cx', function(d){ return d })
			.attr('cy', 40)
			.attr('r', 5)
			.attr("fill", function(d){
			num = Math.floor( Math.random() * (20 - 10) + 10 );
			if (num <= 5) {
				return color = "red";
		}	else if (num <= 10) {
				return color = "blue";
		}	else if (num <= 15) {
				return color = "green";
		}	else if (num <= 20) {
				return color = "purple";
		}
			else {
				return color = 'black';
			}
						} );

{% endhighlight %}
<br /> <br />
&nbsp;&nbsp;&nbsp;&nbsp;So in conclusion when selecting items in the DOM D3 will check the length of the dataset then loop through the function call that many times. If there are any of the element you specified on the page already it will do the function for those then create new ones for the remaining loops. For example my dataset above has five elements. When I add circles in the svg.selectAll() it will look for any existing in the svg element and try to change its attributes or create them if none exist.  