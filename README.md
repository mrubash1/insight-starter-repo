# Welcome to the insight starter repo

This repo is organized as a standard python package. To learn more about how
packages are organized, check out this blog post:

[https://realpython.com/python-application-layouts/](https://realpython.com/python-application-layouts/)


## First steps

### 0) Clone this repo

### 1) Make this repo your own

Lets start with a blank slate: remove `.git` and re initialize the repo

    $ rm -rf .git   
    $ git init   
    $ git status   

You'll see a list of file, these are files that git doesn't recognize. At this
point, feel free to change the directory names to match your project. i.e.
change the parent directory `insight-starter-repo` and the project directory
`insight_starter_repo`

Now commit these:

    $ git add .
    $ git commit -m "Initial commit"

### 2) Set up a virtual environment

The first thing we need to do is set up a virtual environment. A virtual
environment is a way of freezing all of your python versions; so, if you try
to run this script again in 2 year (or even 2 months) it wont break due to
tensorflow being updated (for example).

Setting up an environment is easy: make sure you're `cd`'ed into your package
root dir and run the following commands:

    $ python3 -m venv insight_venv
    $ source insight_venv/bin/activate
    (insight_venv) $ pip install numpy ipython matplotlib tensorflow keras 

This created an environment `insight_env` (if you `ls` your root directory you'll
see the folder `insight_env`) and installed some basic packages (you're
probably going to want to install more, but these will get you started). These
packages were installed into that folder, you can type `which python` or `which
pip` to confirm this. 

In a little bit we're going to want to set up an AWS instance, and we're going
to want to mirror this repo there. So we don't have to remember all the
packages we installed lets, "freeze" the environment. 

    (insight_env) $ pip freeze > requirements.txt

This way, if we want to install everything in a different location, we can do
it simply by:

    (some_new_env) $ pip install -r requirements.txt

### 3) Set up your .gitignore

You're going to be pushing your code up to github, and you have a limited
amount of space there. We need to tell git not to include things like logs, or
model checkpoints, when pushing up code. We do this by setting the `.gitignore`
file. In this repo there is a basic one included, lets add the `insight_env`
folder to it (we only want to include the `requirements.txt` file, never the
environment)

For started, run `git status` and confirm the your environment is included in
the list of git files

Open up `.gitignore` with your favorite editor, and at the bottom add:

`*_venv/`

This will ignore any directory that has the ending `_env`

Lets run `git status` again and confirm git not longer recognizes that
directory


### 4) Push to git hub

Now that we've change the code, we need to do another commit. Typically, you
should stay away from commits like the first one we did. Commit messages need
to be a bit more descriptive.

First lets set an editor. 

```
$ git config --global core.editor "vim"
```

If you don't want to use vim, no worries, you can set any editor you want:
https://stackoverflow.com/questions/2596805/how-do-i-make-git-use-the-editor-of-my-choice-for-commits

Now lets commit:

```
git add .
git commit
```

Without the `-m` flag, git will open your editor of choice. You can then write
a better commit message.  Check out this post for inspiration on how to write a
good commit message https://chris.beams.io/posts/git-commit/

To push to git hub, follow these instructions.
https://help.github.com/articles/adding-an-existing-project-to-github-using-the-command-line/

### 5) Misc. advice

 1. Don't push separate commits with messages like 'Fix typo'. These should be
    included into your last commit. To do this use `git --amend`
 2. Because you're going to be doing rapid prototyping, your experience with
    git will be a little different from the standard workflow. But, to get an idea
    of how git is used at larger companies and on more mature projects, check
    out this blog post. https://nvie.com/posts/a-successful-git-branching-model/


## Next Steps

### 1) Set up AWS
