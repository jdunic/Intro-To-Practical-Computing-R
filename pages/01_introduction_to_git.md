---
layout: page
title: Introduction to Git
description: Setting up your first repository and making your first commit
---

####Current status
By now I expect that you have been through the software installs posted [here](pages/00_computer_setup.html)

#### Setting up git*
Since this is your first time using Git, we will need to configure a few things. This will require us to open up a terminal. For windows users, this will be the Bash shell that was included with yesterday's install.  

It doesn't matter what directory you are in for this because we are telling git to configure global (whole computer) settings.

~~~
git config --global user.name "Minnie Mouse"
git config --global user.email "Minnie.Mouse001@umb.edu"
git config --global color.ui "auto"
~~~

You can check your settings using

~~~
git config --list
~~~

These commands aren't as cryptic as they might seem. The syntax for git is typically

~~~
git verb
git do_something
~~~

#### Making a repository!

Somewhere on your computer, such as in your home folder, I suggest that you make a new folder called something like R_projects. From now on, this is where you will contain your R projects. It helps to keep things more organised and more simple on your computer.  

In your new directory, let's make another one called anything you like. This will be a folder for all the in-class exercises and such. For tomorrow you can make a repository for your homework. 

~~~
cd ~
ls
cd R_projects
mkdir class_exercises
cd class_exercises
~~~

Now I am in my new directory, class_exercises. Let's look inside of it, it should be empty.

~~~
ls
~~~

##### Initiate our repository!
~~~
git init
~~~

Now let's look again

~~~
ls
~~~

No change... that's weird.

~~~
ls -a
~~~

There is a new hidden directory called .git ! This is where your commit history is stored. If you delete this folder, you will lose your changes!  

Let's check our git status. This is a good command to get in the habit of seeing what's going on in git.

~~~
git status

#
# On branch master
#
# Initial commit
#
# nothing to commit (create/copy files and use "git add" to track)
~~~

Git is telling us that there is nothing to keep track of yet. For now, let's create an empty text file called hello_world.txt. You can do this through the command line as I will do, or you can save a text file into your directory.

~~~
touch hello_world.md
~~~

Go back and check out git status

~~~
git status
~~~

We can see that there is an 'untracked' file. This means that git is not yet keeping tabs on it. We must *add* this file to the staging area. 

~~~
git add hello_world.md
~~~

Check out git status again to see your 'staged' file.

~~~
git status
~~~

Now we're ready to make our initial commit!

~~~
git commit -m 'initial commit'
~~~

If we check git status again, we can see that there have been no changes since our commit.  
We can view our commit history by looking at the git log

~~~
git log
~~~

You have survived your first git cycle! It seems like a lot now, but it becomes second nature surprisingly quickly. 


Exercises:

1. How can you undo a git init?
2. How can you add multiple files at once?
3. What is .gitignore?

Bonus question: What does 'touch' do?


####Useful reference sheet!

There is a lot of new terminology that is introduced when we talk about version control. For example, 'repository', 'commit', 'merge'. [Software Carpentry](http://software-carpentry.org/) has created an awesome [reference sheet](http://swcarpentry.github.io/git-novice/reference.html) for new users!

A cheatsheet of Git commands that you may find useful as you continue to use Git can be found [here]()
