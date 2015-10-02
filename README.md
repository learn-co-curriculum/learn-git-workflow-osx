# Using git with Learn

## The Git CLI

The deep integration of Learn, Git, and GitHub means that you can actually use the native `git` command line application to work on Learn. The `git` command line is something every developer uses hundreds of times a day, so while a bit technical, it's a good thing know.

In this lesson, we'll show you the sequence of steps (or workflow) needed to use git to solve labs on Learn. Don't worry too much about understanding the details of each command. And there is a simpler workflow that you're going to learn about soon using the `learn` command line application that automates all of this, so really, don't worry if this seems overly complex or cumbersome. Be brave.

## Step 1: Fork on Github

The first step of solving any code lab on Learn is to "fork" the lab's repo to your GitHub account.

Forking means that you're creating your own copy of the lab so that you can solve it.

![Forking](http://ironboard-curriculum-content.s3.amazonaws.com/front-end/lab-assets/git-workflow-1.png)

Every lab is initially stored in GitHub in an account called `learn-co-students`. Every student has access to that lab. But if you solve that copy of the lab, the next student to attempt the lab will find it already solved. We can't all work on the same copy. Every student on Learn needs their own copy of the original lab. When you fork a lab, that's what you're making, your own copy of a lab. We call the original lab the "Upstream" and we call your version of the lab the "Origin". These copies are called "Remotes". The original lab is the "Upstream" remote, your fork is your "Origin" remote. This is the standard convention for open soure.  When you clone your copy (fork) of the lab, we call that copy your local copy.

### How to Fork a lab

To get started, in Learn click "View on GitHub".

![View on GitHub](https://dl.dropboxusercontent.com/s/4wmbuywfusq8l51/2015-09-30%20at%208.17%20PM.png)

Next on Flatiron's Github page for the lab click the Fork button.

<img width="100%" height="auto" src="http://ironboard-curriculum-content.s3.amazonaws.com/front-end/lab-assets/ironboard-labs-step-1.jpg" alt="Ironboard Labs Step 1">

Then select your personal Github account as the location to fork to.

<img width="100%" height="auto" src="http://ironboard-curriculum-content.s3.amazonaws.com/front-end/lab-assets/ironboard-labs-step-1b.jpg" alt="Ironboard Labs Step 1B">


## Step 2: Clone it Locally

Cloning is the process of making a local copy of the lab from the personal remote of your fork on GitHub, called "Origin".

<img width="100%" height="auto" src="http://ironboard-curriculum-content.s3.amazonaws.com/front-end/lab-assets/git-workflow-2.png" alt="Git Workflow 2">

To clone, make sure you've first clicked on the SSH link, then click the
copy button next to the Clone URL to copy it to your clipboard.

<img width="100%" height="auto" src="http://ironboard-curriculum-content.s3.amazonaws.com/front-end/lab-assets/ironboard-labs-step-2.jpg" alt="Ironboard Labs Step 2">

Next, in Terminal navigate to the parent directory where you would like to place this lab. Then type:  `git clone <paste the clone URL here>`  

Note: You should replace the `<paste the clone URL here>` including the `<` and `>` symbols in the snippet above with your actual clone URL by pressing command+v on mac or ctrl+v on windows. Example: `git clone git@github.com:jongrover/first-lab-000.git`

<img width="100%" height="auto" src="http://ironboard-curriculum-content.s3.amazonaws.com/front-end/lab-assets/ironboard-labs-step-2b.png" alt="Ironboard Labs Step 2b">

Don't forget to `cd` into the lab directory that was made when you cloned the lab. Once in the directory, open the directory with your favorite text editor. Try `subl .` to open in Sublime or `atom .` to open in Atom.

![Work mode](https://dl.dropboxusercontent.com/s/je5pazo2edy5cwl/2015-09-30%20at%207.34%20PM.png)

This setup, a terminal in the lab's directory and the lab directory open in an editor like Sublime or Atom, that's the state you want to be in when working on a lab on Learn. It means you're ready.

## Step 3: Solving the Lab

Once you've forked and cloned the lab, you're ready to solve it. All of the labs on Learn are written with an RSpec test suite that you can use to confirm that you've fulfilled the requirements of the lab. RSpec is a testing library that ruby developers use everyday, so again, as you work on Learn, you're also learning the same tools and workflows that developers use.

### Test Driven Workflow

When you work on a lab, we recommend the following workflow:

#### Reading the README

Read the lab's README on Learn and get a sense of what the lab is about and what it is asking you to build. Read the entire README and then work on the lab and as you hit hurdles you'll have a context for where to look for clues and hints in the README.

#### Run the tests with `learn`

2. Before doing any work, run the test suite from your local clone with the `learn` CLI command. From your terminal, in a lab's directory, run `learn`, you'll see something similar to:

![Failing Test](https://dl.dropboxusercontent.com/s/0ik01a1urmuw7o6/2015-09-30%20at%207.46%20PM.png)

I know error messages or failure messages are intimidating, but try to read them. Developers are detectives, constantly sleuthing for the bug that's the culprit. Errors and failures are our clues, they illuminate the path forward.

We know that the idea of "things being broken" is frightening at first. Broken things are stressful and frustrating! But guess what? As an engineer, as a programmer, the default state of anything you work on is broken. The things you are programming are always broken. Get used to it. Your job is to fix broken things. You can do it. If your code isn't broken, if your code works, you are no longer programming, you're job is done, things work. Embrace the errors. The obstacle is the way.

#### Read the tests

Read the test suite in `spec/`. Open up the lab in your text editor, open the files in the `spec` directory that are not named `spec_helper.rb`. `spec_helper.rb` is a helper file to configure your tests which you can ignore. Any file in `spec` that ends in `_spec.rb` though is a test file and while testing code and RSpec are advanced, we believe the semantics are easy to understand, the meaning of the test is comprehensible, even if the code is not. For example, soon you'll be solving your first lab. The lab includes a file `spec/first_lab_spec.rb`. The contents will be:

```ruby
describe 'First Lab:' do
  it 'you made a change' do
    new_file_made = Dir["*"].size > 5
    file_edited = !File.read("./edit-me.txt").empty?
    expect((new_file_made || file_edited)).to be_truthy, "Make sure you have added a new file or edited edit-me.txt"
  end
end
```

You haven't even written a line of code yet and we're asking you to read some very abstract and complex code and try to reach for any footing or understanding. We believe in you. We believe you can infer and deduce and understand a bit of the code above, even with no experience. Your mind incredibly powerful, challenge it confronting the unknown.

Beyond all the syntax and code above, can you decipher what we're asking for? What the lab requires you to do? How the test works? Again, even if you only get 10% of the expectations of the test, that's still something. And while you do that, 4 things will happen.

1. You'll have 10% more understanding of how to solve the lab.

2. You'll get better at reading tests and we bet that the next test you read you'll get 12% of it and constantly see improvement through old fashion practice and determination.

3. Almost unconsciously, like Mr. Miyagi in the Karate Kid, you'll actually learn how to read and write tests proficiently, "Wax on, wax off" style.

![Wax On, Wax Off](https://38.media.tumblr.com/a5dc9f34d87226be8f31f5c982c8af7b/tumblr_mklzm4VeUq1rwt2uzo1_500.gif)

4. You'll have learned Test-Driven-Development, TDD, one of the most sought after skills of a professional developer.

This cycle, reviewing the README, running the tests, reading failure messages, reading the tests, editing your code, and trying it all again, is how you are supposed to code, it's what programmers do all day. We break things, we define the error with a test, we fix the code, we pass the test, we repeat.

#### Write Your Code

After forking and cloning the lab, opening the lab in a text editor, reading the README, running the test suite, reading the errors, and reading the tests themselves in `spec`, you're ready to code. You've armed yourself with every weapon available in the arsenal of your intellect and we know you can program triumphantly.

You should understand the point of the lab.

You should be able to identify the objectives and topics the lab is exercising so you can google for more information.

You should know the expected behavior or outcome of the solution.

You should know what files you need to create or edit.

You should know what those files and code should define, provide, and do.

You should constantly test your code with every significant change or attem.

You should read error messages and glean insight into the solution with every new failure.

You should keep on trying until you get it working. It doesn't matter how many times you fail as long as it is one less than the times you tried.

You should ask for help on Learn.

Programming is never about getting it all right at once. Programming is like solving a puzzle, you don't try to put it together immediately, you approach it one piece at a time. The workflow we're describing optimizes this process, trial and error, attempts and feedback, insight through failure. Most of our time as programmers is spent staring at error message and code wondering, "Hmm".

<iframe src="https://vine.co/v/hPXTA6l9AqQ/embed/simple" width="600" height="600" frameborder="0"></iframe>

Follow this workflow, running tests, reading errors, writing code, running tests, reading errors, consulting the README, googling for more context on a topic, writing more code, running the tests again, reading errors, and repeat. You'll get it, you'll surprise yourself and find a confidence within you. And if you're just stuck or tired and just need some help, Ask a Question and the Learn community is here for you.



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
