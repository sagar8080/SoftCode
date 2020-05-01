As a developer you are going to write a lot of code. A hell lot.
But that needs to be synchronized with your team members as they should always have the latest copy of code with them.

I have found  myself in a fix a multiple times when one of my team members used to have an older version of code and he hadnt updated his codebase. Your best bet to keep it in check would be to use a version control.

A verison control not only lets the whole team to have a centralized updated codebase but also solves the whole chaos and mess that an unregulated development brings.

# What is a version control

* Version control is a system that records changes to a file or set of files over time so that you can recall specific versions later.
* It allows you to revert selected files back to a previous state, revert the entire project back to a previous state, compare changes over time, see who last modified something that might be causing a problem, who introduced an issue and when, and more.
* Using a VCS also generally means that if you screw things up or lose files, you can easily recover. In addition, you get all this for very little overhead.

### Local VCS
* Many people’s version-control method of choice is to copy files into another directory.
* A simple yet error prone approach.
* To deal with this issue, programmers long ago developed local VCSs that had a simple database that kept all the changes to files under revision control.

![local VCS](local-vcs.png)

Downsides:
* Doesnt allow for multiple system collaboration

### Centralized VCS
* The local VCS limited the tracking of changes to a single system only.
* To deal with this problem, Centralized Version Control Systems (CVCSs) were developed.
* These systems (such as CVS, Subversion, and Perforce) have a single server that contains all the versioned files, and a number of clients that check out files from that central place.

![central VCS][central-vcs.png]

Downsides:
* Single point of failure
* If the data on te central repo gets corrupted then it becomes unusable to the lot.

### Distributed VCS

This is where Distributed Version Control Systems (DVCSs) step in by replicating a clone of your project on a network of remote servers
* In a DVCS (Git, Mercurial), clients don’t just check out the latest snapshot of the files; rather, they fully mirror the repository, including its full history.
* Thus, if any server dies, the client repositories can be copied back up to the server to restore it.
* Every clone is really a full backup of all the data

![Distributed VCS](distributed-vcs.png)

Upside:
* This allows you to set up several types of workflows that aren’t possible in centralized systems

## GIT - The VCS of choice.

Make sure you have git installed on your system

```
sudo apt install git-all
```

### Getting a GIT repository
You typically obtain a repository in one of two ways:
  * Make a local dir into a project repo
    If you turn a local directory into a git repo, then initialize it by `git init`
  * Clone an existing Git repository from elsewhere.
    You clone a repository with `git clone <url>`.
    ```
    $ git clone https://link-to-git-repo
    ```
### Recording your changes

### Git branching
Git doesn’t store data as a series of changesets or differences, but instead as a series of snapshots.
When you make a commit, git stores a commit object that contains a pointer to the snapshot of the content you staged.
This object also contains the author’s name and email id and commits that directly came before this commit from its parent/'s:
    * zero parents for the initial commit
    * one parent for a normal commit
    * multiple parents for a commit that results from a merge of two or more branches.
