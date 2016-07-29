---
id: 373
title: My Git Cheat Sheet
date: 2015-12-02T09:00:09+00:00
author: Adrian Eufracio
description: Here is my cheat sheet to start using git today with handy commands and terminology.
layout: post
guid: http://adrianeufracio.com/?p=373
permalink: /my-git-cheat-sheet/
categories:
  - tooling
---
Git is god. Not really but it is a powerful Version Control System (VCS). VCS&#8217;s can be hard to manage and understand but Git makes this relatively easy. On web projects, Git can be both a handy tool and a lifesaver in a developers arsenal . It is also a must have for any project with multiple collaborators. Git can be used right in the Command Line Interface. Here is my cheat sheet to start using git today.

## Git Terminology

**Repository**
  
A Repository, often called a repo, is basically the folder containing all of the projects files.

**Staging Area**
  
The Staging Area is a file in git that contains the information that will be added to your next commit.

**Commit**
  
A commit is a save to your project that takes a snapshot of all your projects files and records it with a unique ID. This makes it possible to go back in time if you need to make changes or revert to older version of your project.

**Branch**
  
A branch is a replicated repository. Branches make it possible to alter files without effecting the master branch or primary branch, creating something like an alternate reality of that repo. Branches come in handy when you want to experiment on a project or when adding a new feature to a product.

**Merge**
  
Merging grabs the changes from one branch and applies them to another. Once your branch is ready to make it to the big time, merging will add all your changes to your project to the primary branch. 

**Push**
  
Push refers to uploading your local repository to your remote repository. Remote repositories are hosted on sites like <a href="https://github.com/" target="_blank">github.com</a>, <a href="https://bitbucket.org/" target="_blank">bitbucket.com</a>, or <a href="http://beanstalkapp.com/" target="_blank">beanstalkapp.com</a>.

**Pull**
  
Pull refers to pulling down any changes from a remote repository and merging them in to your local repository. Pulling is common when you have changes being pushed to the remote repository and you need to add those changes to your local repository.

**Fetch**
  
Fetch pulls the latest changes in a remote repository but does not merge them into your local repository. Instead of merging you can compare the changes made on the remote and integrate them when ready.

## Git Commands

Initializes git in project folder

    git init

* * *

Returns files that are in/out of staging area

    git status

* * *

Returns list of commits

    git log

* * *

The way to add files to the staging area. Add file by typing file name at the end of the command <i class="code-term">git add text.html</i>

    git add

* * *

The way to remove files from the project. Remove file by typing file name at the end of the command <i class="code-term">git rm text.html</i>

    git rm

* * *

Takes a snapshot of current staging area and saves it with a unique ID.

    git commit

* * *

Performs <i class="code-term">git add</i> on all changed files while making a commit.

    git commit -a

* * *

Adding <i class="code-term">-m</i> with text in parenthesis leaves a message that describes why this commit is being made.

    git commit -m "Message goes here"

* * *

Display history of commits

    git log

* * *

Lists branches

    git branch

* * *

Creates a branch with the name passed at the end of the command

    git branch <name>

* * *

Switches to branch with the name passed at the end of the command. Can also be used to revert to older commits <i class="code-term">git checkout <commit></i>

    git checkout <name>

* * *

Create and switch to branch with the name passed at the end of the command

    git checkout -b <name>

* * *

Deletes the branch that is passed at the end of the command

    git branch -D <name>

* * *

Undoes a commit. It undoes the changes that are associated with that commit while creating a new commit acknowledging the revert

    git revert

* * *

Undoes changes and resets project to the last commit. It is similar to git revert but it does not create a commit which makes it impossible to keep track of this reset or go bring back a file to a previous state if need be.

    git reset

* * *

Removes untracked files from directory.

    git clean

* * *

Merges the branch that is passed at the end of the command to the branch you are currently in.

    git merge <name>

* * *

Duplicates an existing repository. The repository is located by the url passed at the end of the command

    git clone <url>

* * *

List all remote repo associated with the current repo, can also add, <i class="code-term">git remote add <name></i>, and remove, <i class="code-term">git remote rm <name></i>, remote repos from project.

    git remote

* * *

Pulls the latest changes in a remote repository but does not merge them into your local repository

    git fetch

* * *

Pulls the latest changes in a remote repository and merges them into your local repository

    git pull

* * *

Uploading your local repository to your remote repository

    git push

* * *

## Conclusion

Git has many more commands that can be used in your project but these should be enough to get you started. I will be posting an article soon on proper git workflow with multiple collaborators. 

## Git Resources

  * <a href="https://git-scm.com/" target="_blank">Official Git Website</a>
  * <a href="https://www.atlassian.com/git/tutorials" target="_blank">Atlassian Git Tutorials</a>
  * <a href="https://help.github.com/articles/github-glossary/" target="_blank">Github&#8217;s Git Glossary</a>