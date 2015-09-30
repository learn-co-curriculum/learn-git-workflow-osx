# Using git with Learn

## The Git CLI

We've talked a little bit about how git is a version control system. This means it allows you to store and manage different versions of your code over time. The most basic way to interact with git—in other words, the way you actually use it to store your code—is by running a series of commands from your command line. 

In this lesson, we'll show you the sequence of steps (or workflow) needed to use git to solve code labs on Learn. Don't worry too much about understanding the details of each command. We'll get into more detail in due course, and in fact, we've created some conveninent shortcuts for you that will let you circumvent a bunch of these steps. But like anything, we think it's crucial to have a basic understanding of what's going on behind the scenes so that this doesn't feel 100% like magic (it's OK if it feels a little big magical for now). 

## Step 1: Fork on Github

We mentioned previously that every lesson on Learn is actually stored as its own Github repo. The first step of solving any code lab on Learn is to "fork" the lab's repo to your Github account. Forking means that you're creating your own version of the original repository, where you can make changes that don't impact the original code. 

Here's how your fork a lab repository on GitHub:

1. On Learn, hit the View on GitHub button (SCREENSHOT NEEDED)
2. On Github, select Fork in the upper right of the UI (SCREENSHOT NEEDED)
3. When prompted, select your GitHub account

That's it. You've now forked the lab, and Learn makes this obvious to you by turning the Fork light green.

## Step 2: Clone it locally

Now you have your own fork of the lab, but this still exists on GitHub (e.g. in the cloud). In order to write code locally (that, is on your computer) you're going to need to pull this code down to your machine. In git, this is called cloning. 

Here's how you clone a lab to your computer:

1. On Github, find the SSH clone URL associated with your fork. Copy it to your clipboard. (SCREENSHOT NEEDED)
2. On your computer, open a Terminal
3. Type `git clone PASTED_URL` where PASTED_URL is the URL you would paste in

The code has now cloned to your computer, and stored in a directory one level down from your current working directory. Its directory name will be the name of the lesson. If you run `ls` from your Terminal, you should see it. 

## Step 3: Solve the lab!

The next step is all about you doing the work to solve the lab. To do this, you should have a good understanding from the instructions on Learn for what you need to do. You'll do your work in your text editor (most likely Sublime Text if you used the Learn app to set up your development environment). 

1. Start by moving into the labs directory by typing `cd LAB_NAME` where LAB_NAME is the name of the lab you want to work on
2. Now type `subl .` to open up the contents of this directory in Sublime Text

You will spend a lot of time in Sublime, this is where you'll write all of your code. You'll also frequently flip back and forth between writing code and running tests in your Terminal. You'll learn more about running tests soon, but in short, you will use the `learn` command to run the local test suite and see if you've solved the lab correctly by getting all tests to pass. Once you've done that, you're ready to submit your work back to Learn.

## Step 4: Staging your changes

Once you've solved the lab by getting all tests to pass, you want to save your work and submit it to Learn. The first step in doing this is to "stage" your changes, or prepare them for submission. You can stage all of your changes at once with the `git add .` command: that command is saying "add all of my changes in the current directory" which is generally what you want to do. 

## Step 5: Committing your changes

You're not quite ready to send your changes to GitHub. Before you can do so, you need to wrap all of your changes up into a tidy package called a "commit". Every commit has a commit message that tells the world what this change is about. You create a commit with the following git command: `git commit -am "YOUR_MESSAGE"` where YOUR_MESSAGE is the short commit message you write to describe your change. 

## Step 6: Pushing your code

With your commit created, you're now ready to push your code to GitHub. You'll do this with the very simple `git push` command. 

The code you wrote to solve the lab is now up on GitHub, stored on your forked version of the original lab repository. 

## Step 7: Opening a Pull Request

There is one final step to getting Learn to know about your solution. While your code has been pushed to your fork on GitHub, Learn doesn't yet know about it because your fork is separate from the original lab's repository. What you want to do is notify the original repository's owner (in this case, Learn) that you have some changes to submit from your fork. You do that on GitHub by opening a "Pull Request", so named because you are issuing a request to have your code pulled over to the original repository. 

To open a Pull Request on Learn: 

1. Go to your forked version of the lab on GitHub
2. Press the green button "pull request" button (SCREENSHOT NEEDED)
3. Hit the "Create Pull Request" button

Whew! That's it, that is the entire workflow for solving a lab on Learn. You may be thinking to yourself "wow, that seems like a lot of annoying work to perform just to solve a code lab" and to some degree you're right! It *is* a lot of work. BUT, and this is crucial, this is the very same workflow professional developers use every day as part of their job writing real code. So by using Learn, we actually want to teach you that real workflow, and re-inforce it as a habit of doing development work. 

## Up next: some shortcuts

However, we also recognize that this stuff is new, and somewhat tedious, particularly for new developers. And so we've created the Learn CLI, that has some convenient shortcut commands that you can use to accomplish all of the above behind the scenes. We'll go through that next, and take you through a slightly simpler workflow you can use to accomplish all the same good stuff. 
