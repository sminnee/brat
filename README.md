Brat
====

Brat is an opinionated simplification of some common git operations.  It's intended to ease the transition from something like subversion to git.  It prints the key git commands that it uses, to ease the transition from brat to regular git usage.

Rather than give a large set of options, it makes some choices about how to interact with git. This is because the flexibility of git can itself be a barrier for new users.

You shouldn't think of brat as a replacement for git - it's not designed to replace git in its entirety.  Rather, it's a set of training wheels for some of the more common actions that new users to git will have to learn.  To help with this, it prints out the git commands that it's executing as well as an explanation of why it's doing this.

Key points:

 * It works with git-svn and regular repositories
 * It applies the philosophy of "rebase local changes before committing", to keep the repository history relatively flat.  It does not, however, perform any rebasing on shared branches (which is the devil's work).
 * It recommends the use of GitX for conflict resolution and committing.

Installation
------------

You install brat manually, although the process is simple.  Just download the package from git and copy the binary into your path:

    git clone git://github.com/sminnee/brat.git
    cd brat
    sudo cp brat/brat /usr/bin
    rm -rf brat
    
If you'd like to make it easier to get updates in the future, you can check out brat into a more permanent directory and then symlink the binary into your path.  I like to keep things like this in a directory called `~/Projects`, but you can put it wherever you like.

    cd ~/Projects
    git clone git://github.com/sminnee/brat.git
    cd /usr/bin
    sudo ln -s ~/Projects/brat/brat
    
In the the future, when you need to update, you can do so like this.

    cd ~/Projects
    brat pull

Commands
--------

### `brat type`

Print the type of the current repository: git-svn or regular git.

### `brat pull`

Pull changes from the central repository into your local one.  Any changes you have made on your local repository will be rebased onto the latest code from the central repository.

### `brat push`

Synchronise your local repository with the central one.  This calls `brat pull` first.

### `brat stashtobranch branchname "commit message"`

Stash the currently uncommitted changes into a new branch, and the check out the branch you were originally on.  This can be thought of as a slightly more permanent alternative to `git stash`.

### `brat resolved` and `brat skip`

These commands are used during conflict resolution.

 * To resolve a conflict, you should stage all the changes for the resolved commit and then run `brat resolved`.  To stage changes, you should move them to the right hand column of the GitX commit screen.
 * To skip a commit that is no longer relevant (for example, the same change was already made in a different way in the central repository), call `brat skip`.  Remember that this means you will lose your changes, so be careful!

Known issues
------------

 * Conflict resolution isn't yet tested