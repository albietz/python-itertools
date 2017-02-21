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

> ## Prerequisites
>
> The examples in this lesson can be run directly using the Python interpreter, using IPython interactively, 
> or using Jupyter notebooks.
{: .prereq}

*Thanks to [Mike Driscoll](https://www.blog.pythonlibrary.org/2016/04/20/python-201-an-intro-to-itertools/) for the content*
