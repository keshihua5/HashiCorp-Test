## What is the difference between push, pull, and fetch?

- `git push` - send changes from a local branch to a remote repo.
- `git fetch` - get changes from a remote repo into your tracking branch.
- `git pull` -  get changes from a remote branch into your tracking branch and merge them into a local branch.

Often `git push` and `git pull` are described as equivalent. This is not entirely correct. Under the hood, `git push` does two things:

1.  `git push` takes our current branch and checks to see whether or not there is a tracking branch for a remote repository connected to it. 
2. If so, our changes are taken from our branch and pushed to the remote branch. 

This is how code is shared with a remote repository;  think of it as "make the remote branch resemble my local branch." This fails if the remote branch has diverged from your local branch. If not, all the commits in the remote branch are in your local branch. Your local branch needs to be synchronized with the remote branch using git pull or git fetch and git merge when this happens.

`git fetch` takes our current branch and checks to see if there is a tracking branch. If so, it looks for changes in the remote branch and pulls them into the tracking branch. It does not change your local branch. To do that, you need to do `git merge origin/master` (for the "master" branch) to merge those changes into your branch — also called "master."

`git pull` simply does a `git fetch` followed immediately by `git merge`. Some people prefer to use `git fetch` followed by `git merge` to make sure they understand the changes they are merging into their branch before the merge happens.
