

03_introduction_to_ggplot.md


Some data subsetting:


We briefly touched on using $ to select a column of a dataframe. Let's start there and build our way up.

Let's remind ourselves of the structure of the gapminder dataset


So remember that when we look at our object, if it is quite large this can be unwieldy. Therefore, there are a few tricks we can use. str() is always what I do first. If we would like to just look at the top and bottoms of our dataframes, you can also use head()/tail()

~~~
gapminder

str(gapminder)

# Great, so we can see that gapminder is a *dataframe*i with 1704 rows, and 6 columns. 
# We have two factor (categorical variables) - country and contintinent
# Four numeric - variables. From a quick pass, some are discrete, others are continuous

# You may not recognize one of the most special features of this dataset. This is a 'tidy' dataset. 

~~~
head(gapminder)
~~~

* Each column is a single variable.
* Each row is a single observation.

This allows us to plot effectively.

~~~
tail(gapminder)

#Let's also look at the dimensions of the dataframe more explicitly. What does this match up with?

dim(gapminder)


# RStudio has a very nice viewer to look at data opbects/dataframes

View(gapminder)
~~~
And Chris pointed out to me yesterday, that there is a new order by feature that you can use. We'll talk about programmatic ways to sort, but for now this can be a great way to resort your data visually. (Note - doing anything in View() like this will not change anything in your dataframe. This is only a visual tool.)  


`dim()` is surprisingly useful as a quick check that your df is what you actually want it to be

--------------------------------------------------------------------------------

Remember from the last bit of class that we can index columns in a data frame using $

Let's play with this:
Indexing single vector

~~~
gapminder$lifeExp

But just printing it out is a bit useless, it just barfs up a bunch of life expectancies at us. Let's assign it as a variable. 

life <- gapminder$lifeExp
~~~

Now let's look at some properties of this vector

~~~
str(life)

head(life)

length(life)

dim(life)

# WEIRD! What would you expect the dimensions to be???

# A data.frame should have dimensions! We can check in on R objects more specifically than using str. 

is.data.frame(life)
is.vector(life)
~~~

We'll talk about this more I think next week, or the week after when we start to talk more in depth about objects in R. For the next few lessons, we'll just start to introduce you to some, seemingly peculiar behaviours, because they'll come up in your life!  


Okay, let's start dabbling with plots - we'll start by using some of the built in plotting with R. Personally, I do not use plot, almost ever. There are some cases where it comes up. But I find it too hard. 

Today we're going to introduce you to ggplot2.




Back to playing with our data just a little bit more, then we'll jump into some plotting. Let's do some indexing.  

Starting with our single vector. Let's get the first element. For those of you who have programming experience using other languages, you'll notice that indexing starts at 1, not 0. 

~~~
life[1]

life[2]

life[3]

life[1704]
~~~

Getting single elements seems easy enough. How can we get more?

~~~
life[1:2]

life[1:10]

life[(1704 - 10):1704]

# Note that the same can be done using c()

life[c(1, 2)]

life[c(1, 2, 3, 4, 100)]
~~~


Great, so working a single vector is okay. How do we expand this to a data.frame?  

Indexing rows and columns in a dataframe

Row, column format

~~~
gapminder[1, 1]

names(gapminder)

gapminder[1, 'country']

gapminder[1, c('country', 'year')]

gapminder[1:2, c('country', 'year')]
~~~

What if I want the whole first row?

~~~
gapminder[1, ]

# Same goes for columns

gapminder[, 'country']

Syntax (on board)
# [ROW, COL]
~~~

## Exercises:

1. Select row 100 of gapminder.

gapminder[100, ]

2. Select rows 40 – 50 of the gapminder country, continent, and life expectancy columns (in a single dataframe)

gapminder[40:50, c('country', 'continent', 'lifeExp')]

3. Select the first, second, tenth, and last five elements of life expectancy in a single vector. (using your life expectancy vector)

life[c(1:2, 10, (1704 - 5):1704)]
life[c(1:2, 10, 1699:1704)]


WHEW! Okay, time for some plots. A much more rewarding endeavor.  


You'll see 

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


### Touching on scales

~~~
ggplot(data = gapminder, aes(x = year, y = lifeExp, by = country, colour = log(gdpPercap))) + 
  geom_point()

ggplot(data = gapminder, aes(x = year, y = lifeExp, by = country, colour = log(gdpPercap))) + 
  geom_point() + 
  scale_colour_gradient(low = 'blue', high = 'red')

ggplot(data = gapminder, aes(x = lifeExp, y = gdpPercap)) + 
  geom_point() + 
  scale_y_log10()


ggplot(data = gapminder, aes(x = lifeExp, y = log(gdpPercap))) + 
  geom_point()

~~~


ggplot(data = gapminder, aes(x = lifeExp, y = gdpPercap, colour = gdpPercap)) + 
  geom_point()



Facets

~~~
ggplot(data = gapminder, aes(x = year, y = lifeExp, color=continent)) +
  geom_line() + facet_wrap( ~ country)
~~~

p + geom_smooth(colour = 'black')
~~~
Let's add lines for the different continents - this will be a stat because we're summarising our data.



~~~

Exercise:
read.csv(); write.csv()


Data and aesthetic mappings - what data point goes where (x, y coordinates), and how it looks, size, colour

geometric objects (geoms) - representation of data points - these control the type of plot you create. e.g., box_plot, point = scatterplot, 

scales - map values to aesthetics - colour, size, shape - they show up as axes and legends 

facet specification - different subsets of an entire dataset

statistical transformations

coordinate system



layers

Let's start with a basic scatterplot of population and year


Now we can add some colour

ggplot(data = gapminder, aes(x = year, y = pop, colour = continent)) + 
  geom_point()


~~~
ggplot(data = gapminder, aes(x = year, y = pop, colour = country)) + 
  geom_point()
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




04_ggplot_continued?.md

05_data_aggregation_dplyr.md
talk abut dplyr in the context of another grammar of dealing with data
- uses verbs for commonly used actions taht you would use on data frames to 
manipulate and organise it in preparation for analysis and visualisation.


