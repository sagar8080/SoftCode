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

### Starting out
You typically obtain a repository in one of two ways:
  * Make a local dir into a project repo
    If you turn a local directory into a git repo, then initialize it by `git init`
  * Clone an existing Git repository from elsewhere.
    You clone a repository with `git clone <url>`.
    ```
    $ git clone https://link-to-git-repo
    ```
### Recording your changes
* Each file in your working directory can be in one of two states: tracked or untracked.
    * Tracked files are files that Git knows about, they can be unmodified, modified, or staged.
    * Untracked files are everything else — any files in your working directory that were not in your last snapshot and are not in your staging area.
* As you edit files, Git sees them as modified, because you’ve changed them since your last commit. As you work, you selectively stage these modified files and then commit all those staged changes, and the cycle repeats.
* Furthermore, to be able to collaborate on any Git project, you need to know how to manage your remote repositories.
* Managing a repo includes adding remote repositories, remove remotes that are no longer valid, manage various remote branches and define them as being tracked or not.

* `git status` - To check the current state of the file. use `-s` for short status
* `git add File` - To track some file
* `git add *` - Lazily track all the files
* `git diff` - To show unstaged changes, use `--cached` to see what you've staged so far
* `git commit -m` - Add a message regarding the changes and make a commit.
* `git commit -a -m` - Git automatically stages every file that is already tracked before doing the commit
* `rm file` - Removing a file from the working directory puts it in an sunstaged area
* `git log -p` - shows the git log with the commits in a pretty format
* `git commit -amend` - Redo a commit, make the additional changes, stage them, and commit again
* `git reset HEAD <file>` - To unstage a staged change (Covered in detail later)
* `git checkout -- <file>` - To discard changes in the working directory
* `git remote` - To see the remote servers that have been configured

### Dont be that guy who doesnt understand git branches
* Git doesn’t store data as a series of changesets or differences, but instead as a series of snapshots.
* Staging a file computes the checksum for that file and stores that version of the file in the repo as a `blob`
* When you make a commit:
    * git checksums each subdirectory
    * stores a commit object that contains a pointer to the snapshot of the content you staged
    * stores them as a tree object in the Git repository
* The commit object also contains the author’s name and email id and commits that directly came before this commit from its parent/'s:
    * zero parents for the initial commit
    * one parent for a normal commit
    * multiple parents for a commit that results from a merge of two or more branches.
* A branch in Git is a lightweight movable pointer to one of these commits. Default branch name is master
* As you make commits the branch pointer moves forward, with its head pointing to the latest commit.

* Create a branch
    * `git branch <branch-name>` or `git checkout -b <branch-name>`
* Switch to a branch
    * `git checkout <branch-name>`
* Delete a branch
    * `git branch -d <branch-name>`
* Delete remote-tracking branches
    * `git branch -d -r origin/<branch-name>`
* Create a New Branch and Switch Immediately
    * `git checkout -b <branch-name>`
* View local branches
    * `git branch`
* View remote branches
    * `git branch -r` but using `git branch -a` shows both the remote and local branches
* View Merged and Not merged local branches
    * `git branch --merged`
* Adding a new remote repository
    * `git remote add`
* To synchronize your work with a remote repository
    * `git fetch <remote>` remote can be `origin` or `origin/<branch>`

#### Stashing and Cleaning
* If your working directory or staging area has uncommitted changes that conflict with the branch you’re checking out, Git wont let you switch branches.
* Stashing takes the dirty state of your working directory — that is, your modified tracked files and staged changes — and saves it on a stack of unfinished changes that you can reapply at any time (even on a different branch).
* `git status` - to see your dirty state
* `git stash` - to stash changes
* `git stash list` - list the stash stack
* `git clean` - to get rid of unwanted files that are not meant to be stashed
* `git clean -f -d` - force clean the working tree
