---
layout: post
title: So what exactly is insertion sort?
comments: true
---

![Image]({{ site.baseurl }}/images/insertion-sort.svg)

<br /> <br /> <br />
&nbsp;&nbsp;&nbsp;&nbsp;Today I've been assigned with the task (or better yet the glory) of finding out what insertion sort is and the practical uses of such and algorithm. After doing some research and watching a few informational videos on Youtube [here](https://www.youtube.com/watch?v=lEA31vHiry4), [here](https://www.youtube.com/watch?v=c4BRHC7kTaQ), and [this](http://www.sorting-algorithms.com/insertion-sort) helpful animation I was able to come to grips with the usefulness of this algorithm.
<br /> <br />
&nbsp;&nbsp;&nbsp;&nbsp;Insertion sort is an algorithm that compares the first element (farthest left in most cases) in your array or list to the next element checking if it is has a bigger value. This can be done for integers as well as putting strings in alphabetical order. Now most of you are probably reading this saying "Hey that sounds a lot like Bubble Sort man!". Well it's close but it's not. They key differentiator here is that insertion sort will hold a list with all the elements it's already iterated over and make sure those are sorted before moving onto the next. This is best shown in the picture I've provided above. See how all the elements that have been iterated over so far are emboldened with a red outline. Now notice that when 4 gets to the point of having 1 on the right side it doesn't swap with it. That is because the list it has created before (the list with all the red elements) is not sorted as of yet. Insertion sort will repeat the sorting process by starting at the beginning of it's self made list until everything is in order. After said operation is finished it will continue about it's business sorting the rest of the array. How's that for efficiency! Oh and for all you big data lovers out there just so you know the insert sort operates on a O(n^2) notation. Till next time young cyborgs and don't forget, there's always a chance to learn a new function everyday.
<br /> <br />
## Code

{% highlight python %}
def insertion_sort(list):
	for index in range(1, len(list)):
		value = list[index]
		i = index -1
		while i >= 0:
			if value < list[i]:
				list[i+1] = list[i] #shift numbe rin slot i to the right
				list[i] = value #shift number in slot i + 1 to the left
				i = i - 1
			else:
				break

{% endhighlight %}