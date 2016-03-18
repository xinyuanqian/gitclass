A set of GIT exercises for the QMUL CIS Software Workshop.

# Overview

The goal is to learn the basic Git commands and understand how it can help you write better software.

This class is split into two parts. In the first section, you can work individually. In the second section, you'll need to work in a group.

Rather than work on a program, we've decided to go with a more artistic, esoteric approach - combining lines of Shakespeare with contemporary Rap and Hip-Hop lyrics to create something new. 

# Before you begin

Make sure you have a good text editor available, that you are comfortable with. You will need to understand basic bash commands like cp, ls, touch, rm and similar.

You should also create a [http://github.com](github.com) account if you don't have one.

# Resources and other options

There are many ways to get help, and many great tutorials out there. We don't insist you follow this tutorial, although we'd like it if you did. Others we recommend include:

* [https://try.github.io/](https://try.github.io/) - Probably the best one out there, in my opinion.
* [https://guides.github.com/activities/hello-world/](https://guides.github.com/activities/hello-world/) - A little simple and github focused but not too bad. 
* [http://gitreal.codeschool.com/](http://gitreal.codeschool.com/) - Another tutorial.

## git scm book

This deserves it's own section, as the material is excellent. I refer to this page often. There is a paperback book with a PDF version also, if you prefer that sort of thing.

* [https://git-scm.com/doc](https://git-scm.com/doc)
* [https://git-scm.com/book/en/v2](https://git-scm.com/book/en/v2)


# Exercises

Please begin with part 1 and if you feel comfortable, you can move on to part 2.

## Part 1

### git clone

The first thing to do is to clone the repository. Navigate to a place in your home directory and run the command:

    git clone git@github.com:QMUL/gitclass.git

You should see a directory appear called gitclass that has all the files you need to get started

### git status

Run the following command from inside the gitclass directory:

    git status

You should see output similar to this



This command is very useful when you are making changes and you want to see what needs to be saved and what doesn't.

### Create a new file

Now, we can start with our new lyrical masterpiece, be it a song, poem or just something that sounds funny. Using your favourite text editor, create a file named something like *myfirstpoem.txt* or similar. Take a look at the two files, *shakespeare_corpus.txt* and *rap_lyrics_corpus.txt*. Select a few lines from each (say 5 to 10) and come up with something new.


### git add

Now we can add your new file to the repository. You can, if you like, run *git status* to see the status of your new file. We should add this file, so it is *tracked*  or *staged* within the git system. Run the command:

    git add <MYFILENAME>

... replacing *<MYFILENAME>* with the actual filename.

Run *git status* again and you should see that it is now tracked. 


### git diff

Sometimes, we'd like to see the differences between various commits before we decide to incorporate them. Lets run the following command:

    git diff --staged

You should see that your new file has been *staged*, which means it will be added in the next commit.

We can remove this change from any future commits with
    git reset <MYFILENAME>

... which means *unstage* this file.

### Fork the repository on github

We now have a clone of the master repository, but it's time to create your own copy on github.com. Login to github.com and navigate to [https://github.com/QMUL/gitclass](https://github.com/QMUL/gitclass). At the top right of the page you should see a button labelled *fork*. Press this and fork your own repository.

### git remote

The command *git remote* shows you the various remote repositories linked to this one. These repositories can be anywhere, not just on github.com but for now, that's the place we'll use. We need to add the repository you just forked as a new remote. Run the command:

    git remote add cis <address>

You will need to replace *<address>* with the github.com address of the repository you forked in the previous step. You can find this out by navigating to your forked repository and taking a look at the *ssh* text box at the top of the page. It will look something like this:

    git@github.com:MYUSERNAME/gitclass.git 

If you make a mistake, run the command:

    git remote --help

This will show you the commands needed to remove a remote and start again.

### git commit

Possibly one of the most useful and often used commands, *git commit* creates a snapshot of the repository, a note in the history of your project. Run the following command

    git commit --help

You should see all the variations of the git commit command and what all the various switches mean. For the most part however, we will use the following:

    git commit -a -m "<MY MESSAGE>"

The *-a* flag is quite special. This means that all the changes that have occurred should be added to this commit. The term is *staging* and it's something we will return to. It is possible for a file to have changed but you don't want to add these changes to the commit you are about to make. For now though, we will use this flag to submit *all* changes.

#### commit messages

Before we actually commit, we should take a short time to talk about commit messages. Take a look at this: [https://xkcd.com/1296/](https://xkcd.com/1296/). This sums up what developers often do when the commit to repositories. Please don't do this sort of thing. Commit message are quite useful and although you don't want to be too long winded, do please try and write useful comments. In our example, it might be somewhat difficult as we aren't writing code, but in general, make your comments meaningful.

#### Perform a commit

We are ready to perform our commit. Run the command:

    git commit -a -m "<MY MESSAGE>"

You will see some output that reflects the changes you have made to the repository. If all has gone well, you will a success message. If it does not, it's probably because you have a conflict or similar.

### git push 

We are ready to send our changes somewhere other than our local machine. Run the comamnd:

    git push cis master

This command has two parts. The first part *cis* refers to the name of the remote we want to push to. The word *master* refers to the branch we want to send to the remote.

If all goes well, you should see a success message. Navigate to your github.com page and you should see your file has appeared with the commit message you set.


### git diff (again)

Run this command

    git diff

It should show you the changes that have just taken place, between this commit and the list. Handy!


### Take a break

Excellent! You've managed to commit things and send things to other places. This means you know how to backup your code and keep track of the changes you've made. This is one of the most powerful and useful features of git.

### git log

Lets take a quick look at what we've done so far. Run the command:

    git log

You should see a list of commits, with their unique ID numbers and the messages you have written.

### git rm

Let us suppose you are not a fan of the prose you have just written. Let's delete it. Run the command:

    git rm <YOURFILENAME>

... replacing *<YOURFILENAME>* with the name of your file.

git will now delete the file in the next commit, removing it for future commits. Run the command

    git commit -a -m "Deleted our file"

You have now made a new commit with the file removed

### pointers

We should talk about pointers, in particular the *HEAD* pointer. This pointer is sort-of-like the default. You can typically think of this as 'which commit am I working on right now'. We will need this in our next example.


### git reset

The command *git reset* has many uses, but as it's name suggests, it resets various things in git to their previous state. Let's pretend we really did want that file we deleted after-all. How can we undo what we just did? 

We can use the following command:

    git reset --hard HEAD~1

**WARNING** this command will trash data and delete things potentially, so use it lightly!

Lets break that command down a little bit. The *--hard* flag means *really set everything back. delete, rename, do what you have to*. This means if you just created a new file it will be deleted when we *roll-back* so be careful.

The *HEAD~1* statement means *one commit before this one*. You can, if you prefer, replace this with the actual commit id instead, which you can find with *git log*

Run the command and see what happens. Your file should now have appeared and we have effectively, gone back in time, wiping out that commit we just made.

Another use case for reset might look like this. Say, you are working on a commit and you make a terrible mistake and you want to go back to where you started. You can use:

    git reset --hard HEAD

We are resetting to the beginning of the current commit we are working on. This is a destructive but useful command if you want to just forgot the mistakes you may have made. Combined with the *branch* feature, this is an excellent way to test and try-out new features.


### git branch

It's time to introduce one of the most used, and most powerful features of git, *branching*. Branching does exactly what it sounds like. If you imagine your commit history as a totally linear narrative, you'd get a straight line, each commit pointing to the last. A branch creates a fork in that line, splitting into two different paths.

Run the following command:

    git branch morespeare

This creates a new branch that forks at the current *HEAD* pointer. If you type the following command...

    git branch

... you should see that the branch has been added but you are still on the *master* branch.

### git checkout

Checkout is an odd command (I find) but what it does is effectively move you to a new branch or working tree. So lets do that:

    git checkout morespeare

Try running...

    git branch

You should see that you are now on the *morespeare branch* - your next commit will appear on this branch, and your *HEAD* pointer will be pointing to it as well.

### Add some more shakespeare

For arguments sake, lets alter the shakespeare corpus and add some more extracts to our list. Navigate to [Project Gutenberg](https://archive.org/details/gutenberg?and[]=shakespeare) and take a look at all the text files they have. Pick one of them (I'm a fan of the tragedies but you might like the sonnets?) and add the text you like to the *shakespeare_corpus.txt* file.

Lets commit out changes. Run a command like this one:

    git commit -a -m "Added more shakespeare to use"

We can make whatever changes we like on this branch, without affecting the master branch. 

### git merge

Lets switch back to our master branch.

    git checkout master

We are back to where we were before. Let us suppose we are happy with the changes we made in the morespeare branch. Lets merge these and clean up.

    git merge morespeare

You should see a message saying the *shakespeare_corpus.txt* file was updated. This will cause a new commit to be created.

#### conflicts

This is the real heart of version control in software engineering. What to do when things don't match up. Our above case is very simple, but sometimes you might see this:

    Auto-merging shakespeare_corpus.txt
    CONFLICT (content): Merge conflict in shakespeare_corpus.txt
    Automatic merge failed; fix conflicts and then commit the result.

If this happens, the file in question will contain portions of *both* sides and you'll need to decide which of the changes you want to keep. If you look at the file, typically, you'll see something like this:


    <<<<<<< HEAD:index.html
    <div id="footer">contact : email.support@github.com</div>
    =======
    <div id="footer">
    please contact us at support@github.com
    </div>
    >>>>>>> iss53:index.html

This example is taken from [https://www.git-scm.com/book/en/v2/Git-Branching-Basic-Branching-and-Merging](https://www.git-scm.com/book/en/v2/Git-Branching-Basic-Branching-and-Merging) and is unrelated to this project. However, it illustrates the point. There are two versions of the same set of lines in the file *index.html*. The current *HEAD* pointer is given first, and another commit from another branch called *iss53* is also shown. In such a case you must remove all the <, > and = signs and leave just the code you want. For example, if I wanted to accept the iss53 change I'd end up with this: 

    <div id="footer">
    please contact us at support@github.com
    </div>

Once we've made resolved this conflict we can use:

    git add <FILENAME>

... to stage the file for commiting.

### Take a break and find some friends

Part two of this couse will require some cross collaboration and is a little more freeform. We shall work with other people's repositories and create a rich tangle and weave of commits, in the hope's that some interesting lyrics might evolve. Try and find a couple of other people you might want to collaborate with, then move on to the next section.

## Part 2


 
# Credits

Inspired by [http://poly-graph.co/vocabulary.html](http://poly-graph.co/vocabulary.html).

All Shakespeare snippets are taken from Project Gutenberg. All rap lyrics are taken from Rap Genius.
