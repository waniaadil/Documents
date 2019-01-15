# Git *-distributed VCS*

VCS : version control system

A repository, or Git project, encompasses the entire collection of files and folders associated with a project, along with each file’s revision history. 

The file history appears as snapshots in time called **commits**, and the commits exist as a linked-list relationship, and can be organized into multiple lines of development called **branches**.

## Git workflow

1. Branch
    1. Safe environment
    2. Make changes
    3. No effect on master branch

2. Commit

    1. Snapshot of  repositories with all changes made
    2. Keep commit as small as possible

3. Pull request

    1. Comparison of two branches, 
    2. Easy for other people to see changes and comment on them

4. Commit 
    1. after pull request make more commits

5. Merge
    1. after final review merge code with the master

## Workflow strategies

    * Workflow is a change management
    * No universal solution 
    * Tools , processes and people
    * DevSecOps
    * Working locally
    * Git clone
    * Copies repo
    * All branches
    * All history

# Models for collaborative development
* There are two primary ways people collaborate on GitHub:

1. Shared repository
2. Fork and pull

## Shared repository
* With a shared repository, individuals and teams are explicitly designated as contributors with read, write, or administrator access.

## Git Fork
* A fork is a copy of a repository. Forking a repository allows you to freely experiment with changes without affecting the original project. 
* Command : Git remote -v



## Git status
* Where head is pointing
* What is going in working directory
* Comparison of remote tracking branch 
* Suggestions about files in working directory etc about what files are to be going in staging stage

# Saved changes … Now what ?

Save file >> exists in working directory

Commit >> nothing will happen to the file without adding the changes

With **git add** the file is added to staging area andis used to add big changes to be added to the main snapshot


**git add .** will add all changes and new files to stagging 

View history by using **git log** And see difference by **git dif**


## Git pull 
* Update local branch you are checked out to  with new changes
* Combination of git fetch and git merge

## Git push
* Update the current branch but it is the same branch on remote 
* Any new commits locally are updated to remote directory


## Git reset 
* Move commits from history to earlier stages of work
* Change the commit id
* **git commit --soft** Small commit to large commit
* **git reset** Changes back to working directory
* **git reset** hard Keep no changes made recently 


## Merge strategies:
1. Fast forward merge: 
* Command used : **Git rebase**  
* history is straight line - Linear history
* No new commits on master
* No merge commit


2. Recursive merge
* command used : Git merge --no -ff
* Non linear line of history
* New commits
* Merger commit created
* Commit to parent

* * *
* when  **Git init** is executed a ** .git ** folder is created in home direcoty or where the git installed
* Git add abc.de >> file is staged and is ready to commit
* If changes are made to above file the the files needs to be added again to the current checked out in order to be committed
* Otherwise the older version of the file will be committed and we will lose all the changes to the file

* * * 

## Basic Git Commands:
* **Git commit -m ‘changes made in repo’** : commit changes with a comment 
* **Git log** : log details about the commit
* **Git add .** : add all pending changes(old and new) to the staging 
* **Git add *.html** : to add only particular types of file to staging 
* **Git ignore *.filetype** : ignore other file types
* **Git branch mybranch** : create a new branch
* **Git checkout mybranch** :move to new branch
* Stage  the change by **git add .**
* Commit by using git **commit -m ‘new changes’**
* **Git checkout master** :switch t master
* **Git status** :  check location

* The changes made to the branch have to be merged to the master or any Destination branch

* Git merge mybranch : merger the branch to mybranch

**To avoid merge conflicts using git merge tool or track changes manually (ask neo what is best**


## Stash
* Group of unfinished changes that can be reapplied anytime
* Command : **Git stash apply**

## Working with remote repositories 
* Manually retrieve or push changes 
* **Git clone urlfortherepo**
* **Git remote** : 
* **Git remote -v** : to show urls as well

### To keep branch up to date
1. **Git fetch origin** 
* Pull data to local repo but not merged to master
* will go out to server and get all changes made since u last cloned or fetched
* Commit will be manual
* Git commit -a -m ‘comment abt the change’

2. **Git pull origin** 
* will automatically fetch and merge changes from remote branch into current branch
* **Git push origin master**
* ready to submit changes

* to add a new repository: **Git remote add myrep0name  repotaddress**
* to fetch a particular repository **Git fetch myrepo**
## Fetching a remote
* When working with other people's repositories, there are a few basic Git commands to remember:

1. git clone
2. git fetch
3. git merge
4. git pull

1. Clone
To grab a complete copy of another user's repository, use git clone like this:

git clone https://github.com/USERNAME/REPOSITORY.git
## Clones a repository to your computer
You can choose from several different URLs when cloning a repository. While logged in to GitHub, these URLs are available below the repository details:

Remote URL list

When you run git clone, the following actions occur:

A new folder called repo is made
It is initialized as a Git repository
A remote named origin is created, pointing to the URL you cloned from
All of the repository's files and commits are downloaded there
The default branch (usually called master) is checked out
For every branch foo in the remote repository, a corresponding remote-tracking branch refs/remotes/origin/foo is created in your local repository. You can usually abbreviate such remote-tracking branch names to origin/foo.

2. Fetch
Use git fetch to retrieve new work done by other people. Fetching from a repository grabs all the new remote-tracking branches and tags without merging those changes into your own branches.

If you already have a local repository with a remote URL set up for the desired project, you can grab all the new information by using git fetch *remotename* in the terminal:

git fetch remotename
## Fetches updates made to a remote repository
Otherwise, you can always add a new remote and then fetch.

3. Merge
Merging combines your local changes with changes made by others.

Typically, you'd merge a remote-tracking branch (i.e., a branch fetched from a remote repository) with your local branch:

git merge remotename/branchname
## Merges updates made online with your local work
4. Pull
git pull is a convenient shortcut for completing both git fetch and git mergein the same command:

git pull remotename branchname
## Grabs online updates and merges them with your local work
Because pull performs a merge on the retrieved changes, you should ensure that your local work is committed before running the pull command. If you run into a merge conflict you cannot resolve, or if you decide to quit the merge, you can use git merge --abort to take the branch back to where it was in before you pulled.