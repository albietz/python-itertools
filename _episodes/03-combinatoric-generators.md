---
title: "Combinatoric Generators"
teaching: 25
exercises: 10
questions:
- How can we easily create combinations and permutations of data?
objectives:
- Learn about the main ways of creating combinations and permutations with `itertools`.
keypoints:
- The combinatoric generators provide an efficient way of iterating over combinations and permutations of data.
---
The `itertools` library contains four iterators that can be used for creating combinations and permutations of data. 
We will be covering these fun iterators in this section.

### `itertools.combinations(iterable, r)`

If you have the need to create combinations, Python has you covered with `itertools.combinations`. What `combinations` allows 
you to do is create an iterator that generates combinations of length 'r' from an iterable. Let’s take a look:

~~~
from itertools import combinations
print(list(combinations('WXYZ', 2)))
~~~
{: .python}

~~~
[('W', 'X'), ('W', 'Y'), ('W', 'Z'), ('X', 'Y'), ('X', 'Z'), ('Y', 'Z')]
~~~
{: .output}

When you run this, you will notice that `combinations` returns tuples. To make this output a bit more readable, let’s 
loop over our iterator and join the tuples into a single string:

~~~
from itertools import combinations
for item in combinations('WXYZ', 2):
    print(''.join(item))
~~~
{: .python}

~~~
WX
WY
WZ
XY
XZ
YZ
~~~
{: .output}

Now it’s a little easier to see all the various combinations. Note that the `combinations` function does its 
combination in lexicographic sort order, so if the iterable is sorted, then your combination tuples will 
also be sorted. Also worth noting is that `combinations` will not produce repeat values in the combinations 
if all the input elements are unique.

### `itertools.combinations_with_replacement(iterable, r)`

The `combinations_with_replacement`  iterator is very similar to `combinations`. The only difference is that it 
will create combinations where elements *do* repeat. Let’s try an example from the previous section to illustrate:

~~~
from itertools import combinations_with_replacement
for item in combinations_with_replacement('WXYZ', 2):
    print(''.join(item))
~~~
{: .python}

~~~
WW
WX
WY
WZ
XX
XY
XZ
YY
YZ
ZZ
~~~
{: .output}

As you can see, we now have four new items in our output: WW, XX, YY and ZZ.

### `itertools.product(*iterables, repeat=1)`

The `itertools` package has a neat little function for creating Cartesian products from a series of input iterables. 
Yes, that function is `product`. Let’s see how it works!

~~~
from itertools import product
arrays = [(-1,1), (-3,3), (-5,5)]
cp = list(product(*arrays))
print(cp)
~~~
{: .python}

~~~
[(-1, -3, -5),
 (-1, -3, 5),
 (-1, 3, -5),
 (-1, 3, 5),
 (1, -3, -5),
 (1, -3, 5),
 (1, 3, -5),
 (1, 3, 5)]
~~~
{: .output}

Here we import `product` and then set up a list of tuples which we assign to the variable `arrays`. Next we call `product`
with those arrays. Notice that we call it using `*arrays`. 

> ## Calling functions with `*args`
>
> The syntax `*args` can also be used when *calling* a function. This will cause the arguments to be “exploded” or applied 
> to the function in sequence.
>
> ~~~
> def fixed_args(first, second, third):
>   print("first arg: ", first)
>   print("second arg: ", second)
>   print("third arg: ", third)
>
> list = (1, 3, 'last')
> fixed_args(*list)
> ~~~
> {: .python}
>
> This produces the following output:
>
> ~~~
> first arg:  1
> second arg:  3
> third arg:  last
> ~~~
> {: .output}
{: .callout}

> ## Challenge
> Try calling `product` without the asterisk pre-pended to arrays and see what happens.
{: .challenge}

### `itertools.permutations(iterable, r=None)`

The `permutations` sub-module of `itertools` will return successive `r` length permutations of elements from the 
iterable you give it. Much like the `combinations` function, `permutations` are emitted in lexicographic sort order. 
Let’s take a look:

~~~
from itertools import permutations
for item in permutations('WXYZ', 2):
    print(''.join(item))
~~~
{: .python}

~~~
WX
WY
WZ
XW
XY
XZ
YW
YX
YZ
ZW
ZX
ZY
~~~
{: .output}

You will notice that the output it quite a bit longer than the output from `combinations`. When you use `permutations`, 
it will go through all the permutatations of the string, but it won’t do repeat values if the input elements are unique.

