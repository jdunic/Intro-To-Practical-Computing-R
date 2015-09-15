---
layout: page
title: Introduction to R
description: Meeting our dataset and understanding basic syntax in R
---

What are today's objectives?

- Familiarise ourselves with RStudio's layout
- use str() to see the structure of an object in R
- 

We're going to run through some things relatively quickly. 


~~~
2 + 2
~~~

Order of operations

~~~
(3 + 4 * (10 - 5)^2)
~~~

Scientific notation
~~~
0.0003
3 * 10^(-4)
3e-4
~~~

Mathematical functions

~~~
log(2) # natural log
log10(2) # base-10 log

exp(0.5) # e^(1/2)

~~~

Comparisons  

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

Tip: These are considered operators. They include things like 'or', 'and', 'divide', 'less than'. This is useful to know when googling!  

Tip from swc gapminder: Instead you should use the all.equal function. (make sure to bring up later in the course)  


Exercises:  

1) What is the problem here? And how can you fix it?  

~~~
> 1 + 
+
~~~

A: You can use Esc.  

2) Why doesn't `e^(1/4)` work? What do you have to write instead? A; `exp(1/4)`  


So you remember all the commands we just used right? No? Not a problem! You can always look these things up!



### Assigning variables

You will also have seen this in swirl. Variables are objects. As you've seen in Swirl, they can be single values, a list of values, or even contain nested objects. Like a list within a list. When naming variables, you typically want to keep the names short (since you have to type them out) but descriptive. I prefer to use use snake case or camel case rather than separating words by dots.  

So you've now seen that you can assign a variable using the `<-` operator. Has anyone found the keyboard shortcut to do this in RStudio? (option + -).  

Sometimes it is okay to just use very short variable names like `x`, but in cases where you have variables that really mean something, it can be more informative to you, or someone who will be reading your code later, to give it a name that is self explanatory. 

~~~
x <- 16 


# If we were to have a list of temperature values (obviously this is in celsius!), 'temp' might be an appropriate name
temp <- c(16, 12, 20, 13, 10)
~~~


### Basics of syntax - functions

You will use functions in almost everything you do in R. Later in the semester we're going to learn how to write them (which really isn't that bad). But for now, you need to be familiar with what a function is. 



### Gapminder dataset

Install your package (note the use of quotes, single or double doesn't matter)

~~~
install.packages('Gapminder')
~~~

~~~
library(Gapminder)
~~~


Now let's start taking a look at this dataset. 

~~~
str(gapminder)
~~~

Let's also look at the str() helpfile

~~~
?str()
~~~

Let's take a different look at the Gapminder data.

~~~
gapminder
~~~

Whoa, that's a bit too much information

~~~
head(gapminder)
tail(gapminder)
~~~

I use this all the time. Especially when you have too many columns to see them using head!
~~~
names(gapminder)
~~~

Let's take a look at country

~~~
gapminder$country
~~~

Notice how this matches up with the notation that you see when you look at `str(gapminder)`.


~~~
row.names(gapminder)
~~~

This shows us all the details about the gapminder dataframe. You can see that columns are denoted by the `$` symbol.

(Include a note on require() here?)

Broader vision - focusing on practical  

What does it look like to start a project in R? And start exploring data?

In this case, we're going to use a subset of the Gapminder dataset, aggregrated and cleaned by the wonderful Jenny Bryan at UBC. She's created a great tidy dataset that we can work with! Instead of having me tell you about it, let's just jump right in and take a look!




```{r}
install.packages(gapminder)
```


