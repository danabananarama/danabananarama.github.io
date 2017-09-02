# Git init [working title]

## Dana Ma

### About me

* Worked in Tech for the last 3 years
* Started using Git when I joined Winton, about a year ago
 * Disclaimer: Not an expert!

???
Will be introducing Git, going over some basic concepts and sharing some tips for working with Git.  
Pitching talk at people who might have started using Git, or are thinking about using Git, to give a grounding in the Git model and hopefully get you a bit more comfortable with how it works.  
Please jump in and ask questions. Slides will be available


* Just an enthusiast. Started out finding out how to use it efficiently, or just without wiping all of my work. While reading about it I was interested by the model and what was going on under the covers, and bit by bit I'm learning more and more about Git as I work with it.
* I have never used Source Tree

---

# What is Git, and why should I care?

* Distributed version control system
* Basic model is simple - but there is a lot to learn
* Advantages
  * Doing things locally => fast!
  * Powerful for collaboration
  * Flexible workflows
* Disadvantages
  * Some tradeoffs when considering organisation of repos
  * Learning curve

???
* Way of organising your work, and how you work  
* Basic model is simple, as I hope to demonstrate  

* Commits don't have to communicate with your remote server, so they are fast, and enable you to work on the go
* Simple branching model helps you organise your work, collaborate with team, lots of tools to help
* Flexibility of model allows teams to use whichever workflow suits them best

---

# Distributed?

Some pictures should be drawn here.

* Git doesn't really know the difference between the repos
* Everyone has their own copy of the entire repo checked out 

---

# Let's get started!

`git init` to start a repo.


Now we have three **trees**!
* **tree**: snapshot of the files in the repo

Our trees are:
* **HEAD**: our 'last save point'
* **Working Area**: all of our local changes
* **Index / Staging Area**: what's going in the next commit


???
* git init adds a folder '.git' which has everything git needs to make this a repo.

* First thing we do is the initial or empty commit 

* Add some commits and draw the o -> o -> o

  1. Add a file "brownies.txt"
  2. `git status` -> HEAD still at initial commit, working area has the file, index is at initial commit
  3. `git add` -> HEAD at initial, working area and index have file
  4. Add a line to the file -> HEAD is at initial commit, index has first line, working area has second line.
  5. `git commit` -> HEAD and index at commit, working area ahead
  6. commit the last thing

---

# Commits

A **commit** in Git consists of:

* Pointer to a tree (i.e. a snapshot of the repo)
* Some info about the author and timestamp
* Commit message
* Parent commit (except for initial commit)

???
* Do a `git cat-file -p` to illustrate what's in a commit
* By following the pointers, you can see exactly what is being stored in the commit

---

# Branches

A **branch** is just a pointer to a commit.

By default a repository starts off with a `master` branch, which we can think of as the 'core' or 'trunk'.

**HEAD** is (usually) a pointer to the branch we have checked out.

* Create a branch with `git branch <branch>` command 
* Check it out (point HEAD to it) with `git checkout <branch>`

or use the shortcut `git checkout -b <branch>` to do both at once.

???
* Sticky note to denote master and another one for HEAD
* Create a branch - add a sticky note
* Check it out - so move HEAD
* `git branch -r`
* Add some commits to it and draw, pointing out that meanwhile master can have extra stuff added to it.

---

# Remotes

We can think of a **remote** as any other instance of the repository which lives somewhere else.

Typically we have a special remote called **origin**
* At Winton this would be Stash/Bitbucket

`git push` to push (check in) our changes into the remote

e.g. `git push origin master`

`git pull` to pull (check out) updates from the remote

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
* check the merge conflict resolution tool

---

# Workflow

---

# Authentication

There are several options for authentication, at Winton we usually use either https or ssh

To set up ssh:
* Generate ssh key
* Share public key with remote

---

# Helpful commands

* `git status` to check current state
* `git log` to view commit history
* `git reset` to revert changes
* `git reflog` to view ref history
* `git commit --amend` to modify the last commit (careful when doing this after pushing!)
* `git blame`...

---

# And more...

* Sources
* Play around with it! get familiar with the concepts!
* Feel free to ask!

# Questions?

???
I'm still learning too!

