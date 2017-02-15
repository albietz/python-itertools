---
title: "Filtering"
teaching: 5
exercises: 5
questions:
- "Do functions affect my program's performance?"
objectives:
- "See the impact of functions on program performance."
- "Learn ways of improving performance by eliminating function call overhead."
keypoints:
- "Functions have a lot of overhead in Python."
- "It is possible to reduce this overhead without sacrificing readability."
---
The `dropwhile()` function returns an iterator that returns elements of the input iterator after a condition becomes false 
for the first time. It does not filter every item of the input; after the condition is false the first time, all of the 
remaining items in the input are returned.

~~~
from itertools import *
​
def should_drop(x):
    print 'Testing:', x
    return (x<1)
​
for i in dropwhile(should_drop, [ -1, 0, 1, 2, 3, 4, 1, -2 ]):
    print 'Yielding:', i
~~~
{: .python}

The opposite of `dropwhile()`, `takewhile()` returns an iterator that returns items from the input iterator as long as the test function returns true.

~~~
from itertools import *
​
def should_take(x):
    print 'Testing:', x
    return (x<2)
​
for i in takewhile(should_take, [ -1, 0, 1, 2, 3, 4, 1, -2 ]):
    print 'Yielding:', i
~~~
{: .python}

`ifilter()` returns an iterator that works like the built-in `filter()` does for lists, including only items for which the test function 
returns true. It is different from dropwhile() in that every item is tested before it is returned.

~~~
from itertools import *
​
def check_item(x):
    print 'Testing:', x
    return (x<1)
​
for i in ifilter(check_item, [ -1, 0, 1, 2, 3, 4, 1, -2 ]):
    print 'Yielding:', i
~~~
{: .python}

The opposite of `ifilter()`, `ifilterfalse()` returns an iterator that includes only items where the test function returns false.

~~~
from itertools import *
​
def check_item(x):
    print 'Testing:', x
    return (x<1)
​
for i in ifilterfalse(check_item, [ -1, 0, 1, 2, 3, 4, 1, -2 ]):
    print 'Yielding:', i
~~~
{: .python}

