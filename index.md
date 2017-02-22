---
layout: lesson
root: .
---
The *itertools* module implements a number of iterator building blocks that provide a set of fast, memory efficient tools. 
These building blocks can be used to form an “iterator algebra” making it possible to construct specialized tools succinctly 
and efficiently in pure Python.

Iterator-based code may be preferred over code which uses lists for several reasons. Since data is not produced from the 
iterator until it is needed, all of the data is not stored in memory at the same time. Reducing memory usage can reduce swapping and 
other side-effects of large data sets, increasing performance.

> ## What is an iterator? 
> An iterator is an object that provides two methods:
>
> * `__next__` which returns the next value from the iterator
> * `__iter__` which returns the iterator itself
> 
> An iterator behaves like a list of values, with some important differences:
> 
> * The values are generated on demand, so the entire sequence does not need to be stored in memory
> * The values can only be accessed sequentually, so an iterator cannot be accessed like an array
> * The values can only be accessed once
> 
> ~~~
> it = iter('PYTHON')
> 
> print(it.__next__())
> 
> for n, char in enumerate(it):
> 	print(n, char)
> 
> # Iterator completed at this point
> # so the following does nothing
> 
> for char in enumerate(it):
> 	print(n, char)
> 	
> it.__next__()
> ~~~
> {: .python}
> 
> ~~~
> P
> 1 Y
> 2 T
> 3 H
> 4 O
> 5 N
> Traceback (most recent call last):
>   File "<stdin>", line 1, in <module>
> StopIteration
> ~~~
> {: .output}
{: .callout}

> ## Prerequisites
>
> The examples in this lesson can be run directly using the Python interpreter, using IPython interactively, 
> or using Jupyter notebooks.
{: .prereq}

*Thanks to [Mike Driscoll](https://www.blog.pythonlibrary.org/2016/04/20/python-201-an-intro-to-itertools/) for the content*
