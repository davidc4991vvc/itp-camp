---
layout: lab
title: Prep - Creating Local and Remote Repositories
prefix: ../../
---
# Lab 7 - Prep - Creating Local and Remote Repositories, Warm-Up Programs

In this lab, you'll be:

1. creating two repositories, one local and one remote
2. linking the two with each other so that they can be synchronized
3. associating a name and email address with your local repository
4. creating a program that calculates the area of a rectangle
5. \* creating a program that calculates the area of a triangle
6. sending these programs to github

## Instructions

### Set up Your Local Repository

This will create a local git repository to store your work for this lab.  The repository will be in ~/Desktop/yourname/lab-07-if-while.

* open terminal
* (if doesn't already exist) create a folder that consists of your first initial and last name on your Desktop
{% highlight bash %}
cd ~/Desktop
mkdir your_first_initial_last_name
{% endhighlight %}
* within that folder, create another folder called __lab-07-if-while__ and __change into it__
{% highlight bash %}
cd your_first_initial_last_name
mkdir lab-07-if-while
cd lab-07-if-while
{% endhighlight %}
* use pwd to verify that you're in the correct folder
	* you should be in __~/Desktop/your_first_initial_last_name/lab-07-if-while__
	* if you're not, cd into it
* to prove that this is not yet a repository, list __all__ files in your current directory 
{% highlight bash %}
ls -al
{% endhighlight %}
* it should mostly be empty
{% highlight bash %}
total 0
drwxr-xr-x  2 joe  staff   68 Mar 18 18:03 .
drwxr-xr-x  3 joe  staff  102 Mar 18 18:03 ..
{% endhighlight %}
* in your lab-07-if-while folder, create your repository!
{% highlight bash %}
git init
{% endhighlight %}
* it should say:
{% highlight bash %}
Initialized empty Git repository in /Users/joe/Desktop/jversoza/lab-07-if-while/.git/
{% endhighlight %}
* show that this worked by listing __all__ files in your current directory
{% highlight bash %}
ls -al
{% endhighlight %}
* check that this shows __.git__ 
* use ls .git to show the contents of your repository (it should contain a configuration file, for example)
{% highlight bash %}
ls .git
{% endhighlight %}
* configure your name and email for your commits (these do not have to be the same as your github account)
{% highlight bash %}
# in the directory of your repository
git config user.name  "my first and last name"
git config user.email "my@email.address"
{% endhighlight %}
* finally, use git config again to see if this worked:
{% highlight bash %}
git config -l
{% endhighlight %}
* (use should see your name and email appear in the configuration)

### Create Your Remote Repository

This will create a remote git repository on github.  It will also link your local repository with this remote repository.  In order to submit your work, you will send your files / changes from your local repository to the remote repository on github.

* log in to github; you should see the list of repositories on the right	
![Repository List](../../resources/img/repos-screen.png)
* you should have all of the previous lab related repositories 
* go back to terminal
* using the commandline, create a remote repository on github by using the command below...
* substitute your github username where it says "your github user name" (keep the single quotes and __KEEP "name":__ at the end of the line; don't change that!).  the name of the repository is lab-07-if-while (you can see that specified at the end of the command)
{% highlight bash %}
curl -u 'your github user name' https://api.github.com/user/repos -d '{"name":"lab-07-if-while"}'
{% endhighlight %}
* it should output a bunch of text!
{% highlight bash %}
Enter host password for user 'jversoza':
{
  "id": 17210769,
  "name": "lab-07-if-while",
  "full_name": "jversoza/lab-07-if-while",
  "owner": {
    "login": "jversoza",
	...
}
{% endhighlight %}
<!--_-->
* refresh your page on github
* you should see the new repository added
* go back to terminal
* make sure you're in your local repository folder for __lab-07-if-while__
	* use __pwd__ to do this
	* you should be in __~/Desktop/yourname/lab-07-if-while__
	* if you're not in your lab folder, change your directory to it
* run this command to show that you have not linked your local repository to any remote repository yet
{% highlight bash %}
git remote -v
{% endhighlight %}
* it should _do nothing_
* now, link your local repository to your remote repository on github by using git remote add 
* make sure to substitute the two spots where it says "your_github_user_name" with your github username
<!--_-->
{% highlight bash %}
git remote add origin https://your_github_user_name@github.com/your_github_user_name/lab-07-if-while.git 
{% endhighlight %}
* (alternatively, if you click on your repo you can see your remote repository's url on the lower right hand side of the page...)
![Repository List](../../resources/img/repos-url.png)
* to check that you've linked properly, run the following command again:
{% highlight bash %}
git remote -v
{% endhighlight %}
* it should show origin ... and your repository url:
{% highlight bash %}
origin	https://jversoza@github.com/jversoza/lab-07-if-while.git (fetch)
origin	https://jversoza@github.com/jversoza/lab-07-if-while.git (push)
{% endhighlight %}

### Creating and Saving Changes Locally, Sending to Remote Repository

In this part of the lab, you will create a text file in your local repository, and then you'll send it to your remote repository.

* open terminal
* make sure you're in your local repository folder for lab-07-if-while
	* use __pwd__ to do this
	* you should be in __~/Desktop/yourname/lab-07-if-while__
	* if you're not in your lab folder, change your directory to it
	* if this doesn't exist yet... make sure you completed the beginning part of this lab
* use __git status__ to show that there aren't any changes yet
{% highlight bash %}
git status
{% endhighlight %}
* it should give the following output
{% highlight bash %}
# On branch master
#
# Initial commit
#
nothing to commit (create/copy files and use "git add" to track)
{% endhighlight %}
* create a file called __README.markdown__ using __SublimeText__ (see below...)
* go to Applications &rarr; SublimeText (or use Command+Spacebar to activate spotlight search, then start typing Sublime)
* once SublimeText is open, go to File &rarr; New (or Command+n) to create a new file
* save your file by going to File &rarr; Save As to save your files as __README.markdown__ in your __~/Desktop/yourname/lab-07-if-while__
![Save As](../../resources/img/sublime-save-as-menu.png)
* make sure you navigate to your __~/Desktop/yourname/lab-07-if-while__ before saving!
![Save As](../../resources/img/sublime-save-as.png)
* add text to your file: 
{% highlight bash %}
lab 7, if and while
{% endhighlight %}
* switch back to terminal
* use __git status__ to show that you've made changes
{% highlight bash %}
git status
{% endhighlight %}
* it should give the following output; notice that it contains README.markdown 
{% highlight bash %}
# On branch master
#
# Initial commit
#
# Untracked files:
#   (use "git add <file>..." to include in what will be committed)
#
#	README.markdown
nothing added to commit but untracked files present (use "git add" to track)
{% endhighlight %}
* if we want to save this file in the repository, we have _stage_ it (that is, mark it as something that we're ready to save / commit)
{% highlight bash %}
git add --all
{% endhighlight %}
* to check that you've staged your commit, use __git status__ again
{% highlight bash %}
git status
{% endhighlight %}
* it should output the following text (note that README.markdown moved from _untracked_ to _Changes to be committed_)
{% highlight bash %}
# On branch master
#
# Initial commit
#
# Changes to be committed:
#   (use "git rm --cached <file>..." to unstage)
#
#	new file:   README.markdown
#
{% endhighlight %}
* now we're ready to commit (that is, save the file to the local repository); everything after the -m is the message that will be associated with the changes that you've made
{% highlight bash %}
git commit -m "added a README file"
{% endhighlight %}
* the output of the command should be:
{% highlight bash %}
[master (root-commit) 5b24d27] added readme
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 README.markdown
{% endhighlight %}
* check the status again 
{% highlight bash %}
git status
{% endhighlight %}
* notice that there is nothing staged and no more changes!
{% highlight bash %}
# On branch master
nothing to commit, working directory clean
{% endhighlight %}
* to show the changes that you've saved so far, use __git log__
{% highlight bash %}
git log --color
{% endhighlight %}
* it should show you the following...
{% highlight bash %}
commit 5b24d2777a602908978916ca8fe9c8dd2ed6036b
Author: joe <jversoza@citytech.cuny.edu>
Date:   Wed Mar 18 18:42:33 2014 -0500

    added readme

{% endhighlight %}
* you can share your changes / send them to a remote repository by using __git push__
{% highlight bash %}
git push origin master
{% endhighlight %}
* it should result in:
{% highlight bash %}
Counting objects: 3, done.
Writing objects: 100% (3/3), 242 bytes | 0 bytes/s, done.
Total 3 (delta 0), reused 0 (delta 0)
To https://github.com/jversoza/lab-07-if-while.git
 * [new branch]      master -> master
{% endhighlight %}
* go back to github and look in your repository.  you should see that file appear.

<hr>

### area of a rectangle

Write a program that takes user input and calculate the area of a rectangle based on that input

* using SublimeText, create a new file called __rectangle.html__ in your repository directory: __~/Desktop/jversoza/lab-07-if-while/__
* setup an html file, and add script tags... start writing your JavaScript between the script tags
* the program should ask for a length: "Give me a length"
* the program should ask for a width: "Give me a width"
* the program should calculate the area of a rectangle with that length and width
* it should about the resulting value to the  __JavaScript console__ 
	* for example, if someone enters "5" and "7"  in the prompt dialogs
	* the output in the console would be "The area is 35"
* example interaction is below (everything after the greater than sign (&gt; is user input using the prompt function):
{% highlight bash %}
(prompt) Give me a length
> 7
(prompt) Give me a width
> 5
The area is 35.
{% endhighlight %}
* save your file in SublimeText
* use git status, add,  commit, and push to save your file in version control and submit it

