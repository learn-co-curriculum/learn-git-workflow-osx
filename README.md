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

### Write Your Code

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

##### Programming in Movies vs Real Life
<iframe src="https://vine.co/v/hPXTA6l9AqQ/embed/simple" width="600" height="600" frameborder="0"></iframe>

Follow this workflow, running tests, reading errors, writing code, running tests, reading errors, consulting the README, googling for more context on a topic, writing more code, running the tests again, reading errors, and repeat. You'll get it, you'll surprise yourself and find a confidence within you. And if you're just stuck or tired and just need some help, Ask a Question and the Learn community is here for you.

Eventually your local tests will pass and Learn.co will indicate your success.
![Pass](https://dl.dropboxusercontent.com/s/36nudmkxwmvrow9/2015-10-01%20at%2011.38%20PM.png)

On the left is a passing test run in the terminal, on the right is what the right column in Learn for a passing local test (which we currently call a "Local Build").

## Step 4: Stage and Commit Your Solution with `git`

You solved the lab, your tests are passing, and now you need to submit a solution. With the `git` Learn workflow, you'll need to stage your changes, commit them locally, push them to GitHub, and finally open a Pull Request. You don't need to fully understand everything because if you just execute the commands we describe in order, it'll work. But, let's take a second and briefly talk about what's actually going on when you run `git add .`, `git commit -am `, and `git push`.

Remember that `git` was invented to allow developers to create discrete, isolated, yet shareable, versions of their code. That's Version Control. The first step in telling `git` what changes to your code you want to be included as a new version or "commit" is called "Staging".

We might make 100 changes while programming relating to 100 different features or bugs. After we're done coding, we want to isolate each of those different units of work, each different thread of code, each change that fixes something, into separate, organized versions so that the other developers on the team can easily integrate the changes.

If we integrated all 100 updates at once and just 1 of the updates breaks the code, our entire program breaks. Git allows us to craft granular and specifc commits and versions by allowing us to explicitly tell `git` what changes we want to add to the next commit. When you "Stage" a change, you're not making a new version yet, you're simply telling Git, "Hey, this change is going to be included in the next version commit". Any change you don't tell git about will still exist, it just won't be considered a new version to git and everyone else on your team until you stage it and commit it.

I can only imagine how confusing that sounds, but really, don't worry about it, the truth is that for work on Learn, there is never an instance where you care about "Staging" vs "Committing". You'll always want to stage all your changes and commit them. Because that's always true, you can just follow the workflow below and it'll just work, even if you don't entirely understand it.

To stage your changes for a commit, we use `git add`. To stage all changes for a commit, you can type `git add .`, which means "Hey, Git, please stage all the new changes in the current directory."

`git add .`

![1](https://dl.dropboxusercontent.com/s/55myv88uo7gu24d/2015-09-30%20at%208.34%20PM.png)

Now that all the changes are staged, you can create a new commit, a new version of the code with your changes, with `git commit`. When we make a commit, we need to provide Git with a message describing the work done. Since you've solved a lab, "Solution" is a great commit message. You can commit all changes with a commit message by using `git commit -am "Message"`.

`git commit -am "My first commit"`

![1](https://dl.dropboxusercontent.com/s/9y3zt153pvaabh0/2015-05-03%20at%209.14%20PM.png)

After this you have a new version of your code in a new git commit on your local copy of the lab. But you got to get your solution code to Learn, how does that work?

## Step 5: Pushing Your Solution to GitHub

With your commit created, you're now have upload your local code and commits to your fork/copy of the lab, "Origin", on GitHub. We do that with the `git push` command, instructing `git` to take your local changes and upload them to the `origin` remote, which is always your fork, on your GitHub account.

<img width="100%" height="auto" src="http://ironboard-curriculum-content.s3.amazonaws.com/front-end/lab-assets/git-workflow-4.png" alt="Git Workflow 4">

You can think of `git push` as the opposite of `git clone`.

To push your local code to GitHub, just type `git push` in Terminal.

![1](https://dl.dropboxusercontent.com/s/7qta395mpnmst7x/2015-05-03%20at%209.15%20PM.png)

The code you wrote to solve the lab is now up on GitHub, stored on your forked version of the original lab repository.

![1](http://flatiron-videos.s3.amazonaws.com/ironboard/ironboard-tutorial/7-solving-the-lab.png)

We're not done yet, the final step is to tell Learn that you have finished the lab. We do this using a feature of GitHub called a Pull Request.

## Step 6: Submitting Your Solution via a GitHub Pull Request

A Pull Request is a feature of GitHub that allows developers to collaborate on code safely.

### Pull Requests are Worth Over a Billion Dollars. Here's Why.

Imagine working on a project with 1000s of people across the planet that you've never met. And then imagine that this spontaneous collaboration was all happening at the exact same time, for free, without anyone ever asking anyone to do anything. That's open source software. The Ruby on Rails framework is written by 4,083 people. Linux has had over 12,000 people contribute to the free operating system. Open Source is the entire world working together to build free, superior software. It's magic.

Literally thousands of people that have never met, who share no bond or  common language beyond a love of code, all over the planet, are working together every single second. How is that even possible? How is it not chaos? How are people not breaking things, stepping on each other's toe, doing redundant unneeded work, and just creating a giant unmanageable mess?

The answer to what makes this massively open, spontaneous, free, and world-wide collaboration possible, is GitHub. Specifically, it is GitHub Pull Requests.

Remember that when you work on a project via GitHub the first step is always forking it? When you fork a project, you're creating your own copy so that you can work on it without conflicting with other people. The official project on GitHub is called the "Upstream" remote, it is the code you based your fork or copy on. Your fork or copy is called your "Origin". When you want to integrate changes from your fork/copy to the official project, you create a Pull Request.

<img width="100%" height="auto" src="http://ironboard-curriculum-content.s3.amazonaws.com/front-end/lab-assets/git-workflow-5.png" alt="Git Workflow 5">

A Pull Request on GitHub informs the owners and maintainers of the official project that you want to submit some of your code changes in the form of commits to the official project. The entire world gets to review your changes and manage integrating them in an organized fashion. Through Pull Requests we can make sure that the code that gets added to an open source project is correct and desired. Everyone gets to work but when they want to contribute, Pull Requests give us a chance to vet, discuss, and integrate. At any given point on an open source project, there are literally [hundreds of open Pull Requests](https://github.com/rails/rails/pulls).

Suffice to say, Pull Requests are a powerful social feature that allow the developers to collaborate in an unprecedented scale. The Pull Request workflow is what makes GitHub social. Pull Requests are why GitHub is worth over 2 billion dollars. GitHub Pull Requests are the music of a global software orchestra.

If any of that sounded intimidating, great news, you're not going to be using Pull Requests in that Open Source Workflow because you're not trying to contribute to Open Source yet.

The entire point of our workflow is to prepare you for that - to be in the top 1% percent of developers who contribute to Open Source and make the world a better place through software every single day.

### Creating a Pull Request to Submit Your Solution

For the purposes of Learn, we only require a GitHub Pull Request as a mechanism to inform Learn that you're done with a lab and you're to submit it, have your solution automatically tested so you get credit for solving the lab, and providing a mechanism for the community to review and comment on your solution.

Here's how to open a Pull Request form GitHub to submit your solution to a lab you've forked and have pushed your solution commit to.

Open your fork by clicking "View" in GitHub from Learn or just opening your forked repo on GitHub directly. From your forked repository on GitHub, click the green Pull Request Button.

<img width="100%" height="auto" src="https://dl.dropboxusercontent.com/s/oj85qs5u079i8ub/2015-10-02%20at%201.14%20AM.png" alt="Ironboard Labs Step 4">

GitHub will prompt you to review the Pull Request before submitting and tell you to "Create Pull Request". Click the green "Create Pull Request" button on the review page. You do not need to review anything on this page and can skip it entirely by just immediately click the "Create Pull Request" button.

<img width="100%" height="auto" src="http://ironboard-curriculum-content.s3.amazonaws.com/front-end/lab-assets/ironboard-labs-step-4e.jpg" alt="Ironboard Labs Step 4e">

GitHub will then again prompt you to describe the Pull Request and you can just skip this and again click the green "Create Pull Request" button.

<img width="100%" height="auto" src="http://ironboard-curriculum-content.s3.amazonaws.com/front-end/lab-assets/ironboard-labs-step-4f.jpg" alt="Ironboard Labs Step 4f">

Once the Pull Request is created, you're done and Learn will update the lesson progress accordingly and allow you to proceed to the next lesson.

![PR](https://dl.dropboxusercontent.com/s/zw5axlrl07e4yj3/2015-10-02%20at%201.25%20AM.png)

## Conclusion

The `git` CLI workflow might seem tedious and unnecessary to learning to program. People call `git`, GitHub, and Version Control an "incidental complexity" to learning how to code and insist that you can learn to code without ever even needing to learn about `git`, GitHub, or Version Control. We're not sure, but who knows.

What we do know, what we are absolutely sure about, is that there is no way you're ever becoming a professional software developer without `git` and GitHub.

Learn is about teaching you how to be a professional using and embracing professional tools. And our hope is that not only do you learn to code and get a job, but that you become a part of the open source software community and contribute to humanity through code. That's what we're preparing you for, that's why Learn is hard, because we don't just want you to teach you to code, we want you to make the improve the world with your code.

### Good news

Every single step described and explained in this README is automated via the Learn CLI that we describe in the next lesson. You can get through every single lesson on Learn without ever interacting with `git`, GitHub, open source, version control, pull requests, commits, or any of these technical details.

We don't force you to learn everything at once, but we also won't ever shy away from telling you about the profoundly powerful tools programmers use to make the world a better place. We took a moment to tell you about `git` and GitHub because those technologies are important. Don't worry if it all didn't make sense, Git is actually hard. After this README, if you choose, you will never have to worry about Git again.

## Super Important PS

The next lesson in going to teach you about the `learn` CLI that automates everything in this README. The `learn` CLI workflow is a way easier, but just as professional and real so don't feel bad about using `learn` and never using `git`.

However, sometimes in a lesson on Learn, we'll tell you to Fork and Clone a lab to get started or say something like "Fork this repo". We might use language relating to Git and GitHub to communicate to you that a lesson is a lab and you need to solve it by writing code and submitting it.

**Every single time you see a refernce to forking, cloning, or GitHub to get started on a lab, you can just use `learn open` and the Learn CLI.** The `learn` CLI is exactly equivalent to the `git` workflow it's just automated. So understand that equivalence, GitHub Fork and `git clone` are the same as `learn open` which you're about to learn.
