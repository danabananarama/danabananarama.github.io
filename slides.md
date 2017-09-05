name: title

# Git init

## Dana Ma

???

Pitching talk at people who might have started using Git, or are thinking about using Git, to give a grounding in the Git model and hopefully get you a bit more comfortable with how it works. I remember living in fear... 

Please jump in and ask questions. Slides will be available

Will be introducing Git, going over some basic concepts and sharing some tips for working with Git.  

* Just an enthusiast. Started out finding out how to use it efficiently, or just without wiping all of my work. While reading about it I was interested by the model and what was going on under the covers, and bit by bit I'm learning more and more about Git as I work with it.

* I have never used Source Tree

---

# What is Git?

* **Distributed** version control system
* Many use cases
  * Share code and peer review via pull requests
  * Easily revert to last stable version if you make mistakes
  * Develop features in an isolated environment using branches
* Basic model is simple - but there is a lot to learn

---

# And why should I care?

* **Advantages**
  * Doing things locally => fast!
  * Powerful for collaboration and facilitates many different workflows
  * Easy to recover the past
  * It's really nice and fun to use!
* **Disadvantages**
  * Learning curve
  * Often more than one way to do things
  * Some tradeoffs when considering organisation of repos

???

* Draw central repository/distributed repository

* Share code - if Iw anted to look at Rahul's WANDA work, or Chunli wanted to reproduce some research work from three yers ago

* Basic model is simple, as I hope to demonstrate  

* Commits don't have to communicate with your remote server, so they are fast, and enable you to work on the go
* Flexibility of model allows teams to use whichever workflow suits them best

---


# Let's get started!

`git init` to start a repo
* All this really does is add a `.git/` folder

Git conceptually stores everything as snapshots
* A **tree** is a snapshot of the files in the repo

We have three trees:
* **Working Area**: all of our local changes
  * Git doesn't know anything about what is happening here
* **Index / Staging Area**: what's going in the next commit
* **HEAD**: our 'last save point'
  * Last commit that we've been working from

Now let's do some stuff...

???
* git init adds a folder '.git' which has everything git needs to make this a repo.

* First thing we do is the initial or empty commit 

* Add some commits and draw the o -> o -> o

  1. Add a file "brownies.txt"
  2. `git status` -> HEAD still at initial commit, working area has the file, index is at initial commit
  3. `git add` -> HEAD at initial, working area and index have file
  4. Add a line to the file -> HEAD is at initial commit, index has first line, working area has second line.
  5. `git commit` -> HEAD and index at commit, working area ahead

---

# Commits

We save our work to git's history with **commits**.

`git commit -m <message>` to add a commit of all changes in the index (staging area)

A commit consists of:

* Pointer to a tree (i.e. a snapshot of the repo)
* Pointer to a parent commit (except for initial commit)
  * Allows us to step back through history
* Some info about the author and timestamp
* Commit message

???
* Do a `git cat-file -p` to illustrate what's in a commit

---

# Branches

A **branch** is just a pointer to a commit.

By default a repository starts off with a `master` branch, which we can think of as the 'core' or 'trunk'.

**HEAD** is (usually) a **ref** (i.e. a pointer) to the branch we have checked out. We can think of this as the branch we're currently 'in'.

Create a branch with `git branch <branch>` command 

Check it out (point HEAD to it) with `git checkout <branch>`

or use the shortcut `git checkout -b <branch>` to do both at once.

???
* Sticky note to denote master and another one for HEAD
* Commit and move the note
* Create a branch - add a sticky note
* Check it out - so move HEAD
* `git branch -r`
* Add some commits to it and draw, pointing out that meanwhile master can have extra stuff added to it.

---

# Remotes

We can think of a **remote** as any other instance of the repository which lives somewhere else.

Typically we have a special remote called **origin**
* At Winton this would be hosted on Bitbucket

`git push` to push our changes into the remote

e.g. `git push origin master`

`git pull` to pull updates from the remote

Both of these operations apply to the entire tree - you can't e.g. pull a single file

Branches can be set up to **track** the remote, i.e. establish a link.

???
`origin` is again only special by convention

`git remote -v` lists remotes

Also has commands to add or modify remotes, but typically after setting up your remote you shouldn't need to touch it again.

Demonstrate by setting the remote and pushing to it

Go through the step of what pulling does.

---

# Pull Requests (PR)

A **pull request** is a request to merge one branch into another

* Often a request to merge a branch into `master`, but not always the case

Bitbucket has a nice interface for pull requests where we can review the changes made and approve or mark as 'needs work'

# Merge conflict

A **merge conflict** occurs when an attempt is made to merge together two branches which have modified the same thing.

Git marks where the conflicts exist and we manually resolve.

???
* Push the branch to origin and master too

* I usually manually resolve my merge conflicts...

* Demonstrate merge conflict

---

# Forking

Sometimes you may want to contribute to a repository which you don't have permission to write to. In this case, you can **fork** the repository.

Forking sets up your own remote copy of the repository. When working with a fork, you'll generally have two remotes:

* `origin` - your remote copy of the repository
* `upstream` - the original copy of the repository

You can then pull updates from `upstream` (the original repository), and push your changes to `origin`.

When your changes are ready to be reviewed, you can set up a pull request into the original repository.

???

Draw a picture of the fork

---

# Helpful commands

* `git status` to check current state
* `git log` to view commit history
* `git reset` to revert changes
* `git reflog` to view ref history
* `git commit --amend` to modify the last commit (careful when doing this after pushing!)
* `git blame`...

---

# Tips

### Authentication

There are several options for authentication, at Winton we usually use either https or ssh

To set up ssh:
* Generate ssh key ([Instructions](https://confluence.atlassian.com/bitbucketserver/creating-ssh-keys-776639788.html))
* Share public key with remote

---

# Tips

### Keep it clean

Commit everything and often - the more git knows, the more it can help you! Also you will make more friends with meaningful commit messages.

### Create aliases for frequently used commands

Can do this in git config.

---

# And more...

* The [docs](https://git-scm.com/docs/) are pretty good
* Atlassian has some nice [tutorials](https://www.atlassian.com/git/tutorials)
* Google, StackOverflow, etc
* Play around with it and get familiar with the concepts
* Feel free to ask!

# Questions?

???
I'm still learning too!

