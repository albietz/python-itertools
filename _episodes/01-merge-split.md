---
title: "Merging and Splitting Iterators"
teaching: 5
exercises: 0
questions:
- "Why is Python slower than compiled languages like C and C++?"
objectives:
- "Explain the key differences between Python and compiled languages."
- "Explain what a dynamic language is."
keypoints:
- "Python is a dynamic interpreted language."
- "The flexibility of dynamic languages comes at a cost in terms of performance."
- "There are ways to improve the performance of Python, but it will never be as fast as compiled languages."
---
The `chain()` function takes several iterators as arguments and returns a single iterator that produces the contents of 
all of them as though they came from a single sequence.

~~~
from itertools import *
​
for i in chain([1, 2, 3], ['a', 'b', 'c']):
    print i
~~~
{: .python}

The `izip()` function returns an iterator that combines the elements of several iterators into tuples. It works like the built-in 
function `zip()`, except that it returns an iterator instead of a list.

~~~
from itertools import *
​
for i in izip([1, 2, 3], ['a', 'b', 'c']):
    print i
~~~
{: .python}

The `islice()` function returns an iterator which returns selected items from the input iterator, by index. It takes the same 
arguments as the slice operator for lists: start, stop, and step. The start and step arguments are optional.

~~~
from itertools import *
​
print 'Stop at 5:'
for i in islice(count(), 5):
    print i
​
print 'Start at 5, Stop at 10:'
for i in islice(count(), 5, 10):
    print i
​
print 'By tens to 100:'
for i in islice(count(), 0, 100, 10):
    print i
~~~
{: .python}

The `tee()` function returns several independent iterators (defaults to 2) based on a single original input. It has semantics 
similar to the Unix tee utility, which repeats the values it reads from its input and writes them to a named file and standard output.

~~~
from itertools import *
​
r = islice(count(), 5)
i1, i2 = tee(r)
​
for i in i1:
    print 'i1:', i
for i in i2:
    print 'i2:', i
~~~
{: .python}
