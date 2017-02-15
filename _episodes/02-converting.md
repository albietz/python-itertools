---
title: "Converting Inputs"
teaching: 5
exercises: 5
questions:
- "How can I tell how long my python code takes to run?"
objectives:
- "Explain how to time Python programs and snippets of Python code."
keypoints:
- "There are a variety of ways to time Python code."
- "The best way depends on what environment you are using."
---
The `imap()` function returns an iterator that calls a function on the values in the input iterators, and returns the results. 
It works like the built-in `map()`, except that it stops when any input iterator is exhausted (instead of inserting `None` values to 
completely consume all of the inputs).

In the first example, the lambda function multiplies the input values by 2. In a second example, the lambda function multiplies 2 
arguments, taken from separate iterators, and returns a tuple with the original arguments and the computed value.

~~~
from itertools import *
​
print 'Doubles:'
for i in imap(lambda x:2*x, xrange(5)):
    print i
​
print 'Multiples:'
for i in imap(lambda x,y:(x, y, x*y), xrange(5), xrange(5,10)):
    print '%d * %d = %d' % i
~~~
{: .python}

The `starmap()` function is similar to `imap()`, but instead of constructing a tuple from multiple iterators it splits up the 
items in a single iterator as arguments to the mapping function using the * syntax. Where the mapping function to `imap()` 
is called `f(i1, i2)`, the mapping function to `starmap()` is called `f(*i)`.

~~~
from itertools import *
​
values = [(0, 5), (1, 6), (2, 7), (3, 8), (4, 9)]
for i in starmap(lambda x,y:(x, y, x*y), values):
    print '%d * %d = %d' % i
~~~
{: .python}