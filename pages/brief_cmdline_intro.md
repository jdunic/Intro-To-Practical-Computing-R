---
layout: page
title: The Command Line
description: A very brief introduction - navigating the file system
---

First we must start by opening our terminal. Remember, on a Mac, you can go to spotlight and just type terminal. On Windows, I think that you can use the Bash Shell that came packaged with the Git install from yesterday/last night. If you can't find it, don't fret, you can use an emulator in your regular internet browser [bellard.org/jslinux/](bellard.org/jslinux/). 


We will spend a few minutes working on this. If it all goes over your head or you forget the commands, that is okay. What is important is that you have seen this once before because when it comes up, which it very well may, it won’t seem quite as intimidating and it will be easier for you to talk to someone who knows what they are doing. My hope is that you leave here with enough of a memory to Google or ask your way to a solution.

#### Let's Go!

To start, let's all make sure we're working in our home directory. Note that the tilde means home. 

~~~
cd ~ 
~~~

You should see something like 

~~~
MacBook-Air:~ jillian$
~~~
*The $ means that the terminal is waiting for commands.*  

Alternatively we can ask for the path of our working directory (our current directory). This tells the computer to print out the hierarchy of the folders that we can see.

~~~
pwd
~~~

You should see something like:  
/Users/jillian  


Now that we're here, to make things easier for those on the emulator, let's make a new directory called 'new_directory'

~~~
mkdir new_directory
~~~

Ok, does anyone know how to see see our new directory? What command can we use?

~~~
ls
~~~

Any ideas on what happens if we now go

~~~
ls new_directory
~~~

So you get it, ls, lists the things in a directory.  

Now compare these two commands. What is different?

~~~
ls

ls -a
~~~

Compare those lists to the files that you see in Finder. Notice anything?  

So you can see that some files are hidden. This is something that is important to be aware of because sometimes programs as you to make changes to hidden files. I do want to put a word of caution though. Be careful when you follow instructions off the internet that start to modify things that you don't know much about. Some commands can do bad things to your computer depending on where you are working (particularly if you're working in the root). This is not meant to scare you away from using the terminal. So far I've only broken one thing and even then, I knew exactly what and why I broke something so I was able to ask for help (which was just encouraging someone who knew slightly more than me to Google for the solution because I knew that he would understand the answers better than I).

Okay. Last thing for now. Let's move through our directories. If you are working on your own computer (not the emulator in the browser) feel free to try moving to different folders. But for the demonstration I will just use the directory new_directory.

~~~
cd new_directory
~~~

Check the new path

~~~
pwd
~~~

Great. Now how do we go back to where we were? There are two ways. Two periods in a row denotes the folder that is the next level up (in this case our home directory). One period means the current directory. 

~~~
cd ..
~~~

Alternatively, since we want to go to our home folder, we can use a tilde. 

~~~
cd ~
~~~

####Reference
This brief run through was adapted from the [second module](http://swcarpentry.github.io/shell-novice/01-filedir.html) of the [Software Carpentry tutorial on The Unix Shell](http://swcarpentry.github.io/shell-novice/index.html).  

If you are interested in learning more, I suggest that you check it out!