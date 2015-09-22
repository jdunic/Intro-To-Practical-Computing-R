---
layout: page
title: Introduction to R 
description: Basics of R - R syntax - Helping yourself
---

Sept 15


* [Version control review](### Version control review)

* [Some basics of R and R syntax](### Some basics of R and R syntax)

* [Helping yourself](### Helping yourself)


### Version control review

**Read** page two of this git cheatsheet if you haven't already! Read it every so often to remind yourself of what the point of version control is and how to use it most effectively. 

The take homes from lecture:

* commit often
* commit related changes
* commit messages are for you
* version control is not a replacement for backups


### Some basics of R and R syntax
This is a follow-up to the work you have done using the Swirl lessons 1 and 2. We will beging to familiarise ourselves we will learn about basic R syntax, some R functionality, and learn how to interpret the output of str().  

#### Basic mathematical operations *modified from swc

You can use R just like a calculator. 

~~~
2 + 2
~~~

Order of operations are followed. 

~~~
(3 + 4 * (10 - 5)^2)
~~~

**Scientific notation**  

Scientific notation can and is used in R. These three values are equivalent.  

~~~
0.0003
3 * 10^(-4)
3e-4
~~~

**Functions**  

R includes mathematical functions. Note in the examples below that `log()` is the natural logarithm in R, if you would like to use a logarithm with a different base, such as base 10, you need to include that explicitly, as demonstrated.  

~~~
log(2)  # natural log
log10(2)  # base-10 log

exp(0.5)  # e^(1/2)

~~~

**Comparisons**  

~~~
2 == 2

2 == 3
~~~

~~~
2 != 3
2 != 2
~~~

~~~
2 < 3
2 > 3

2 < 2
~~~

~~~
2 <= 2
2 <= 3
~~~

#### Floating point numbers
We can see that we can check equivalence using the `==` operator. However, you should be aware of an interesting behaviour. I'll expand the explanation soon and for those who want to know more, check it out on google. But essentially storing decimal values with perfect precision can cause difficulties on a computer. This can make doing comparisons tricky, where numbers that look and really are equal, do not satisfy the equivalence `==`. To really test whether values are equal (this does come up sometimes), you are best off to use the `all.equal()` function in cases where you suspect you may run across floating point issues.

Try this out

~~~
0.0003 == 3 * 10^(4)
~~~

Now try this

~~~
all.equal(0.0003, 3 * 10^(-4))
~~~



Tip: These are considered operators. They include things like 'or', 'and', 'divide', 'less than'. This is useful to know when googling!  

Tip from swc gapminder: Instead you should use the all.equal function. (make sure to bring up later in the course)  

#### Exercise 1

1. If you see this in your console, what happened? And how can you fix it?  

~~~
> 1 + 
+ 
~~~

2. What happens when you try and run: 

~~~
e^(1/4)
~~~

--------------------------------------------------------------------------------

### Basics of syntax - functions

You will use functions in almost everything you do in R. Later in the semester we're going to learn how to write them (which really isn't that bad). But for now, you need to be familiar with what a function is. The functions that you will use will have the following format.  

**function**(arg1, arg2, arg3, ... )  


--------------------------------------------------------------------------------

### Helping yourself

Today we looked at the help file for the mean function `mean()`. *Coming soon, screenshots and description of a help file*


There are multiple ways to access the helpfiles. Can you find them? One way we can do it is through the console using `?`. 

~~~
?mean()
~~~
