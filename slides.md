# Git init [working title]

## Dana Ma

### About me

* Worked in Tech for the last 3 years
* Started using Git when I joined Winton, about a year ago
** Disclaimer: Not an expert!

???

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
* Parent commit (for non-tempty commits)

???
* Do a `git cat-file -p` to illustrate what's in a commit
* By following the pointers, you can see exactly what is being stored in the commit

---

# Branches

---

# Remotes

We can think of a **Remote** as any other instance of the repository which lives somewhere else.

Typically we have a special remote called **origin**
* At Winton this would be Stash/Bitbucket

`git push` to push (check in) our changes into the remote

e.g. `git push origin master`

`git pull` to pull (check out) updates from the remote

Both of these operations apply to the entire tree - you can't e.g. pull a single file

???
`origin` is again only special by convention
`git remote -v` lists remotes
Also has commands to add or modify remotes, but typically after setting up your remote you shouldn't need to touch it again.

Demonstrate by setting the remote and pushing to it

---

# Helpful commands

`git commit --amend` to modify the last commit (careful when doing this after pushing!)
