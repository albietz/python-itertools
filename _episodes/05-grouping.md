---
title: "Grouping Data"
teaching: 5
exercises: 5
questions:
- "What is the best datatype to use when searching for elements?"
objectives:
- "Learn how dicts, sets, lists, and tuples are stored."
- "See the best way to find elements in a datatype."
keypoints:
- "Dicts and sets are fast when looking up elements."
- "Be mindful of the datastructures you use as it can have a big impact on performance."
---
The `groupby()` function returns an iterator that produces sets of values grouped by a common key.

This example from the standard library documentation shows how to group keys in a dictionary which have the same value:

~~~
from itertools import *
from operator import itemgetter
​
d = dict(a=1, b=2, c=1, d=2, e=1, f=2, g=3)
di = sorted(d.iteritems(), key=itemgetter(1))
for k, g in groupby(di, key=itemgetter(1)):
    print k, map(itemgetter(0), g)
~~~
{: .python}

This more complicated example illustrates grouping related values based on some attribute. Notice that the input 
sequence needs to be sorted on the key in order for the groupings to work out as expected.

~~~
from itertools import *
​
class Point:
    def __init__(self, x, y):
        self.x = x
        self.y = y
    def __repr__(self):
        return 'Point(%s, %s)' % (self.x, self.y)
    def __cmp__(self, other):
        return cmp((self.x, self.y), (other.x, other.y))
​
# Create a dataset of Point instances
data = list(imap(Point, 
                 cycle(islice(count(), 3)), 
                 islice(count(), 10),
                 )
            )
print 'Data:', data
print
​
# Try to group the unsorted data based on X values
print 'Grouped, unsorted:'
for k, g in groupby(data, lambda o:o.x):
    print k, list(g)
print
​
# Sort the data
data.sort()
print 'Sorted:', data
print
​
# Group the sorted data based on X values
print 'Grouped, sorted:'
for k, g in groupby(data, lambda o:o.x):
    print k, list(g)
print
~~~
{: .python}

> ## Challenge
> This task aims to help you appreciate the usefulness of the `groupby()` function of itertools.
>
> You are given a string S. Suppose a character 'c' occurs consecutively X times in the string. Write a function 
> called compress that will replace these consecutive occurrences of the character 'c' with (X, c) in the string.
>
> For a better understanding of the problem, check the explanation.
> 
> ### Input Format
>
> The function should accept a single argument containing the string S.
>
> ### Output Format
>
> The funcation should return the modified string.
>
> ### Constraints
>
> All the characters of S denote integers between 0 and 9.
> 1≤|S|≤104
>
> ### Sample Input
>
> 1222311
>
> ### Sample Output
>
> (1, 1) (3, 2) (1, 3) (2, 1)
>
> ### Explanation
>
> First, the character 1 occurs only once. It is replaced by (1,1). Then the character 2 occurs three times, 
> and it is replaced by (3,2) and so on.
>
> Also, note the single space within each compression and between the compressions.
>
> ### Tests
>
> Use the following tests to ensure your code is correct
>
> ~~~
> from nose.tools import assert_equal
> assert_equal(compress('1222311'), '(1, 1) (3, 2) (1, 3) (2, 1)')
> assert_equal(compress('2344244443222'), '(1, 2) (1, 3) (2, 4) (1, 2) (4, 4) (1, 3) (3, 2)')
> assert_equal(compress('9949333922222888888'), '(2, 9) (1, 4) (1, 9) (3, 3) (1, 9) (5, 2) (6, 8)')
> assert_equal(compress('11111111'), '(8, 1)')
> ~~~
> {: .python}
{: .challenge}