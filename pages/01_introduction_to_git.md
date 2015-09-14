---
layout: page
title: Introduction to Git
description: Setting up your first repository and making your first commit
---

####Current status
By now I expect that you have been through the software installs posted [here](00_computer_setup.html)

#### Setting up git
Since this is your first time using Git, we will need to configure a few things. This will require us to open up a terminal. For windows users, this will be the Bash shell that was included with yesterday's install.  

It doesn't matter what directory you are in for this because we are telling git to configure global (whole computer) settings. Note, you're name is probably *not* Minnie Mouse... adjust accordingly. Also, use the email address that you used 

~~~
git config --global user.name "Minnie Mouse"
git config --global user.email "Minnie.Mouse001@umb.edu"
git config --global color.ui "auto"
~~~

Let's also choose a default text editor for git. For some actions, such as merging branches, git will open a text file that let's you state the reason for the merge. To set the program that this text file will open in, let's set our default text editor. Choose the text editor that you use on your computer. (For the most part Macs will be TextEdit, while Windows users will use Notepad++)

{:.table}
Editor                     | command                        |
-------------------------- | ------------------------------ |
TextEdit             | `$ git config --global core.editor "textedit -w"`   |
Notepad++            | `git config --global core.editor "'c:/program files (x86)/Notepad++/notepad++.exe' -multiInst -notabbar -nosession -noPlugin"`          |


You can check your settings using

~~~
git config --list
~~~

These commands aren't as cryptic as they might seem. The syntax for git is typically

~~~
git verb
git do_something
~~~

#### Making a local repository!
Local means, making something on your computer.

Somewhere on your computer, such as in your home folder, I suggest that you make a new folder called something like R_projects (note that I avoided spaces because spaces in filenames can cause difficulties). From now on, this is where you will contain your R projects. It helps to keep things more organised and more simple on your computer.  

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
We can initiate a git repository by running `git init` in a terminal when we are in the folder that we will be tracking changes in (e.g., class_exercises).

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

Git is telling us that there is nothing to keep track of yet. 


#### Your first commit
Let's create an empty text file called storytime.md. You can do this through the command line as I will do, or you can save a text file using an editor like RStudio, TextEdit, or NotePad, in your directory.

~~~
touch storytime.md
~~~

Go back and check out git status

~~~
git status
~~~

We can see that there is an 'untracked' file. This means that git is not yet keeping tabs on it. We must *add* this file to the staging area. 

~~~
git add storytime.md
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

Software Carpentry has a great figure showing you the git commit workflow. On the left, you can see the files that you have made changes to. You must then tell git that you are interested in tracking those changes. You start this by 'adding' a file to a staging area using `git add`. Then you must make a commit. This is the step where the change is officially added to your repository and the change is tracked. 

![Git staging area](../images/git-staging-area.svg "git staging area")  
**Git staging area**  

This is all happening locally--on your computer. The next step would be to 'push' these changes to your Github account. You'll learn more about this in the next walkthrough. 


Checkout the web to see if you can figure out the answers to these questions:

1. How can you undo a git init?
2. How can you add multiple files at once?
3. What is .gitignore?

Bonus question: What does 'touch' do?  


####Useful reference sheet!

There is a lot of new terminology that is introduced when we talk about version control. For example, 'repository', 'commit', 'merge'. [Software Carpentry](http://software-carpentry.org/) has created an awesome [reference sheet](http://swcarpentry.github.io/git-novice/reference.html) for new users!

Here is a [cheatsheet of Git commands](http://www.git-tower.com/blog/git-cheat-sheet/) that you may find useful as you continue to use Git.
