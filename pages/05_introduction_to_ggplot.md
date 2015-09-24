---
layout: page
title: Introduction to R 
description: Basics of R - R syntax - Helping yourself
---



WHEW! Okay, time for some plots. A much more rewarding endeavor. Plot making!  

### Basics.  

Here is a brief description of the basic building blocks of a creating a ggplot.  

argument        | description of component
--------------- | ------------------------------------------------------------ |
data            | as a data.frame (long format!)
aesthetic (aes) | mapping variables to visualise properties - position, colour, 
                  line, type, size.                                            |
geom            | actual visualisation of the data                             |
scale           | map values to the aesthetics, colour, size, shape (show up as 
                  legents and axes)                                            |
stat            | statistical transformations, summaries of data (e.g., line 
                  fits, etc., )                                                |
facet           | splitting data across panels based on different subsets of the 
                  data                                                         |


~~~
# Basic scatterplot
ggplot(data = gapminder, aes(x = year, y = lifeExp)) +
  geom_point()
~~~

~~~
# Let's add colour - let's look at a discrete variable - continent
ggplot(data = gapminder, aes(x = year, y = lifeExp, colour = continent)) +
  geom_point()
~~~

~~~
You can assign ggplots to variables.

p <-
ggplot(data = gapminder, aes(x = year, y = lifeExp, colour = continent)) +
  geom_point()

p
~~~


### Layering

~~~
ggplot(data = gapminder, aes(x=year, y=lifeExp, by=country, color=continent))

ggplot(data = gapminder, aes(x=year, y=lifeExp, by=country, color=continent)) +
  geom_line()

ggplot(data = gapminder, aes(x=year, y=lifeExp, by=country, color=continent)) +
  geom_line() + 
  geom_point()


We can also be more specific with our layering and aesthetics.

ggplot(data = gapminder, aes(x=year, y=lifeExp, by=country)) +
  geom_line(aes(color=continent)) + 
  geom_point()

~~~

Exercise 1  

Black dots behind coloured lines.

~~~
ggplot(data = gapminder, aes(x = year, y = lifeExp, by = country)) + 
    geom_point() +
    geom_line(aes(colour = continent))
~~~

### Touching on scales

What is something that you notice between these two graphs?

~~~
ggplot(data = gapminder, aes(x = year, y = lifeExp, by = country, colour = log(gdpPercap))) + 
  geom_point()

ggplot(data = gapminder, aes(x = year, y = lifeExp, by = country, colour = continent)) + 
  geom_point()

# Now let's look back at our data

str(gapminder)

# What do you guys notice?
~~~

Cool! There is a difference in the way that the default colour scale operates for discrete and continuous variables!!!!!

Ok, now that we've figured that you, we can change the colour scales for our variables. With your neighbour see if you can change the colour scales that are being used. You'll likely need to use the scales cheatsheet section and a little bit of googling. Let me know if you guys need a hint. But I want you to take try first. 

Exercise 2

~~~
ggplot(data = gapminder, aes(x = year, y = lifeExp, by = country, colour = log(gdpPercap))) + 
  geom_point() + 
  scale_colour_gradientn(colours = topo.colors(10))
~~~

Use ggsave() to save one of your plots to a file. I'll give you some time to work with your neighbour to figure this out:  


~~~
# Continuous variable examples

ggplot(data = gapminder, aes(x = lifeExp, y = log(pop))) + 
  geom_point(aes(colour = continent)) + 
  facet_wrap(~ continent)

ggplot(data = gapminder, aes(x = lifeExp, y = log(pop), colour = log(gdpPercap))) + 
  geom_point() + 
  scale_colour_gradient(low = 'blue', high = 'red')
~~~

~~~
ggplot(data = subset(gapminder, year == 2007)) +
  geom_bar(aes(x = country, fill = continent)) 
~~~

~~~

ggplot(data = gapminder, aes(x = lifeExp, y = gdpPercap)) + 
  geom_point() + 
  scale_y_log10()


ggplot(data = gapminder, aes(x = lifeExp, y = log(gdpPercap))) + 
  geom_point()

~~~

Take a look under the scales section. You'll see that there 



### Playing with other aesthetics to visualise trends

Let's take a brief interlude and learn a new function. I would like you to use subset() to select data from the year 2007.

subset(gapminder, year == 2007)


~~~

subset(gapminder, year == 2007)


, aes(x = lifeExp, y = gdpPercap, colour = gdpPercap)) + 
  geom_point(aes(size = ))
~~~


Exercise 3


~~~
# Demo this one:

ggplot(data = gapminder, aes(x = gdpPercap, y = lifeExp)) + 
  geom_point() +
  geom_smooth()
~~~

~~~
# Build this one:

ggplot(data = gapminder, aes(x = gdpPercap, y = lifeExp)) + 
  geom_point() +
  scale_x_log10() +
  stat_smooth(method = 'lm')



#### Other cool tips and tricks

Let's return to our boring basic scatter plot

~~~
ggplot(data = gapminder, aes(x = year, y = lifeExp)) +
  geom_point()
~~~

This isn't necessarily the best example of when you would use these tricks, but it will do. 

~~~
ggplot(data = gapminder, aes(x = year, y = lifeExp)) + 
  geom_point(alpha = 0.4)
~~~

Another alternative when you have lots of data points on top of each other can be to use the geom_jitter()

~~~
ggplot(data = gapminder, aes(x = year, y = lifeExp)) + 
  geom_jitter()
~~~


The last thing we'll talk about is facetting. This allows you to create panels of graphs

#### Facets

~~~
ggplot(data = gapminder, aes(x = year, y = lifeExp, color=continent)) +
  geom_line() + facet_wrap( ~ country)
~~~

Work with your neighbour now to familiarise yourself with the different ways you can facet your variables - using the faceting section on the ggplot2 cheatsheet.

You may need to subset. Some subsets to work with are year or continent. 

e.g., 

~~~

~~~

p + geom_smooth(colour = 'black')
~~~
Let's add lines for the different continents - this will be a stat because we're summarising our data.



~~~
ggplot(data = gapminder, aes(x = year, y = pop, colour = country)) + 
  geom_point()
~~~



~~~
ggplot(data = gapminder, aes(x = year, y = pop, colour = continent)) + 
  geom_point() + 
  scale_y_log10()

ggplot(data = gapminder, aes(x = year, y = log10(pop), colour = continent)) + 
  geom_point()

ggplot(data = gapminder, aes(x = year, y = log10(pop), colour = country)) + 
  geom_point() + 
  stat_smooth()

ggplot(data = gapminder, aes(x = year, y = log10(pop), colour = continent)) + 
  geom_point() + 
  stat_smooth()
~~~


Exercises:

~~~
ggplot(data = subset(gapminder, year %in% 1982:2007)) + 
  geom_boxplot(aes(continent, gdpPercap))
~~~

Let's go back to the first line plot we made. There are faster ways of doing this, but for now, let's use ggplot. 

~~~
ggplot(data = gapminder, aes(x = year, y = lifeExp, by = country, colour = continent)) + 
  geom_point()
~~~

What if we want to quickly see what the outliers are? 

~~~
ggplot(data = gapminder, aes(x = year, y = lifeExp, by = country, colour = continent)) + 
  geom_point() + 
  geom_text(aes(label = country))

ggplot(data = gapminder, aes(x = year, y = lifeExp, by = country, colour = continent)) + 
  geom_point() + 
  geom_text(aes(label = year))

~~~


~~~
ggplot(data = gapminder, aes(x = year, y = pop, colour = continent)) + 
  geom_point() + 
  scale_y_log10()
~~~


Homework: 

~~~
ggplot(data = subset(gapminder, year %in% 1982:2007)) + 
  geom_boxplot(aes(continent, gdpPercap, colour = continent)) + 
  facet_wrap(~ year)
~~~

~~~
ggplot(data = subset(gapminder, year %in% 1997:2007)) + 
  geom_density()

~~~





