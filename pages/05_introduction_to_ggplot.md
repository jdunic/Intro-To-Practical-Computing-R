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


