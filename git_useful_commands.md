# Useful Git Commands 
Initialize git repo
>git init 

directory now has an empty repository in /.git/. The repository is a hidden directory where Git operates
type the git status command to see what the current state of our project is:

>git status

create text file sample.txt and again run 

>git status

Notice how Git says sample.txt is "untracked"? That means Git sees that  sample.txt is a new file
we first need to add it to the staging area by using git add.

>git add sample.txt

Git is now tracking our sample.txt file. Let's run git status again to see where we stand:

>git status

Git says changes to be committed? The files listed here are in the Staging Area, and they are not in our repository yet. We could add or remove files from the stage before we store them in the repository.
To store our staged changes we run the commit command with a message describing what we've changed. Let's do that now by typing:

>git commit -m "Add new sample story"

You also can use wildcards if you want to add many files of the same type. Notice that I've added a bunch of .txt files into your directory below
create additional .txt files and try to use wild card to add 

>git add '*.txt'
you've added all the text files to the staging area. Feel free to run git status to see what you're about to commit.

go ahead and run commit
>git commit -m "Add all .txt file"

So we've made a few commits. Now let's browse them to see what we changed.
>git log 

We've gone ahead and created a new empty GitHub repository for you to use with Try Git at  https://github.com/sample-git/sample_git.git. To push our local repo to the GitHub server we'll need to add a remote repository
>git remote add origin https://github.com/sample-git/sample_git.git

The push command tells Git where to put our commits when we're ready, and now we're ready. So let's push our local changes to our origin repo (on GitHub).
The name of our remote is origin and the default local branch name is master. The -u tells Git to remember the parameters, so that next time we can simply run git push and Git will know what to do. Go ahead and push it!

>git push -u origin master

Let's pretend some time has passed. We've invited other people to our GitHub project who have pulled your changes, made their own commits, and pushed them.

We can check for changes on our GitHub repository and pull down any new changes by running:

>git pull origin master

Uh oh, looks like there have been some additions and changes to the sample repo. Let's take a look at what is different from our last commit by using the git diff command.

In this case we want the diff of our most recent commit, which we can refer to using the HEAD pointer.

>git diff HEAD

diff is looking at changes within files that have already been staged. Remember, staged files are files we have told git that are ready to be committed.
Let's use git add to stage sample-repo/sample_v1.txt, which I just added to the family for you.
>git add sample-repo/sample_v1.txt

now go ahead and run git diff with the --staged option to see the changes you just staged. You should see that sample_v1.txt was created.
>git diff --staged

reset to remove sample_v1.txt.

You can unstage files by using the git reset command. Go ahead and remove samplerepo/sample_v1.txt.

>git reset samplerepo/sample_v1.txt

git reset did a great job of unstaging sample_v1.txt, but you'll notice that he's still there. He's just not staged anymore. It would be great if we could go back to how things were before 

Files can be changed back to how they were at the last commit by using the command: git checkout -- <target>. Go ahead and get rid of all the changes since the last commit for sample.txt

>git checkout -- sample.txt

>git status

When developers are working on a feature or bug they'll often create a copy (aka. branch) of their code they can make separate commits to. Then when they're done they can merge this branch back into their main master branch.

We want to remove all these additional files, so let's create a branch called clean_up, where we'll do all the work:

>git branch clean_up
>git branch

Now if you type git branch you'll see two local branches: a main branch named master and your new branch named  clean_up.

You can switch branches using the git checkout <branch> command. Try it now to switch to the clean_up branch:

>git checkout clean_up

so you're in the clean_up branch. You can finally remove all chnages by using the git rm command which will not only remove the actual files from disk, but will also stage the removal of the files for us.

You're going to want to use a wildcard again to get all the octocats in one sweep, go ahead and run:

>git rm '*.txt'

Now that you've removed all the required files you'll need to commit your changes.
Feel free to run git status to check the changes you're about to commit.

>git status
>git commit -m "Commit modified changes"

ou're almost finished with the cat... er the bug fix, you just need to switch back to the master branch so you can copy (or  merge) your changes from the clean_up branch back into the master branch.

Go ahead and checkout the master branch:

>git checout master

the moment has come when you have to merge your changes from the clean_up branch into the master branch.
We're already on the master branch, so we just need to tell Git to merge the clean_up branch into it:

>git merge clean_up

you're done with the clean_up branch you don't need it anymore.
You can use git branch -d <branch name> to delete a branch. Go ahead and delete the clean_up branch now:

>git branch -d clean_up

push everything you've been working on to your remote repository

>git push 