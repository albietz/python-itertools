---
title: "Producing New Values"
teaching: 10
exercises: 10
questions:
- "How can I speed up my function?"
objectives:
- "Explain how built-in functions can be used to speed up your code."
- "Learn how intrinsic operators can be used to replace user defined functions."
keypoints:
- "Using built-in functions and intrinsic operators is much more efficient."
---
The count() function returns an interator that produces consecutive integers, indefinitely. The first number can be passed as an argument, the default is 
zero. There is no upper bound argument (see the built-in `range()` for more control over the result set). In this example, the iteration stops because 
the list argument is consumed.

~~~
from itertools import *
​
for i in izip(count(1), ['a', 'b', 'c']):
    print i
~~~
{: .python}

The `cycle()` function returns an iterator that repeats the contents of the arguments it is given indefinitely. Since it has to remember the 
entire contents of the input iterator, it may consume quite a bit of memory if the iterator is long. In this example, a counter variable is 
used to break out of the loop after a few cycles.

~~~
from itertools import *
​
i = 0
for item in cycle(['a', 'b', 'c']):
    i += 1
    if i == 10:
        break
    print (i, item)
~~~
{: .python}

The `repeat()` function returns an iterator that produces the same value each time it is accessed. It keeps going forever, unless 
the optional times argument is provided to limit it.

~~~
from itertools import *
​
for i in repeat('over-and-over', 5):
    print i
~~~
{: .python}

It is useful to combine `repeat()` with `izip()` or `imap()` when invariant values need to be included with the values from the other iterators.

~~~
from itertools import *
​
for i in imap(lambda x,y:(x, y, x*y), repeat(2), xrange(5)):
    print '%d * %d = %d' % i
 ~~~
{: .python}
