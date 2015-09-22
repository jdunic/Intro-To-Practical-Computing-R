---
layout: page
title: Exercise 1
description: Subsetting vectors and data.frames
---


Here are some follow-up exercises for subsetting vectors and data.frames that 
you may wish to try.

In class, we have used the gapminder dataset. You might remember that this was a
data package that we had to manually install and then load into our workspace 
using `library()`. However, there are many other datasets that already come with 
R. You can checkout the list if you would like using `data()`. For these 
exercises, we're going to use the iris dataset.

~~~
iris
~~~

1. What are the column names and data types of the different columns in iris?

2. How many rows and columns does iris have?

3. Create a single vector called 'width' that is the Sepal.Width th column of iris.

4. What is the 100th value in your 'width' vector? 

5. What is the last value in your 'width' vector? Can you write code that 
returns this value even if you don't know how long 'width' is?

6. Select rows 10 to 20, with all columns in the iris dataset.

7. Select rows 10 to 20 with only the Species, Petal.Width and Petal.Length. Can you do this two different ways?

8. Select rows 1 to 10, 20, and 100 in the iris dataset. 

9. Select the first value in the Sepal.Length column of the iris dataset. Bonus - can you do this *three* different ways?

iris[1, 1]
iris[1, 'Sepal.Length']
iris$Sepal.Length[1]

10. *Bonus*: In class the other day I pointed out an odd behaviour, that when we extracted a single column of our data.frame, it lost its dimensions - `dim(new_object)`. We had expected that the dimensions would be however many rows there were and then one column. But the output returned *NULL*. We also noticed that this new object became a vector, not a data.frame like we started with. As a reminder below is a summary of what we saw in class.  

The bonus question is: Can you select a single column of the data.frame and retain the dimensions/type of object?  

Hint: The unnecessary dimension is 'dropped'. 

~~~
library(gapminder)

str(gapminder)

new_object <- gapminder[, 'country']

dim(gapminder)
is.data.frame(gapminder)

dim(new_object)
is.data.frame(new_object)
is.vector(new_object)
~~~


