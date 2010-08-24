Brat
====

Brat is an opinionated simplification of some common git operations.  It's intended to ease the transition from something like subversion to git.  It prints the key git commands that it uses, to ease the transition from brat to regular git usage.

Rather than give a large set of options, it makes some choices about how to interact with git. This is because the flexibility of git can itself be a barrier for new users.

Key points:

 * It works with git-svn and regular repositories
 * It applies the philosophy of "rebase local changes before committing", to keep the repository history relatively flat.  It does not, however, perform any rebasing on shared branches (which is the devil's work).
 * It recommends the use of GitX for conflict resolution and committing.

Known issues
------------

 * If you don't stash anything, then git stash pop will pull off some legacy stash
 * Conflict resolution isn't yet tested