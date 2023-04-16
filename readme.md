### What is the difference between push, pull, and fetch?

Git is a version control system that allows you to manage your code and collaborate with others. Three common Git commands are push, pull, and fetch. Here's how they work:

- `git fetch`: This command retrieves changes from a remote repository into your tracking branch without modifying your local branch. `git fetch` takes your current branch, checks to see if there is a tracking branch, looks for changes in the remote branch, and pulls them into the tracking branch. To change your local branch, you'll need to do `git merge origin/master` (for the "master" branch) to merge those changes into your branch.
- `git push`: This command sends changes from your local branch to a remote repository. `git push` takes the current branch and checks to see if there is a tracking branch for a remote repository connected to it. If so, your changes are taken from your branch and pushed to the remote branch. Doing this will make the remote branch resemble your branch. However, if the remote branch has diverged from your local branch, meaning not all the commits in the remote branch are in your local branch, `git push` will fail. In this case, you need to synchronize your local branch with the remote branch using `git pull` or `git fetch` followed by `git merge`.
- `git pull`: Git pull is actually a combination of two commands: `git fetch` and `git merge`. `git pull` first does `git fetch` to get changes from the remote branch into your tracking branch, and then it does a `git merge` to merge those changes into your local branch. While `git pull` is often described as equivalent to `git push`, they have different functionalities. `git pull` is more automated, but a manual `git fetch` followed by `git merge` creates an extra step so you can understand the changes you are merging into your branch before the merge happens.

Often `git push` and `git pull` are described as equivalent. This isn't entirely correct, since under the hood `git pull` does two things. `git push` takes your 
current branch, and checks to see whether or not there is a tracking branch for a remote repository connected to it. If so, your changes are taken from your 
branch and pushed to the remote branch. This is how code is shared with a remote repository, you can think of it as "make the remote branch resemble my 
local branch". This will fail if the remote branch has diverged from your local branch: if not all the commits in the remote branch are in your local 
branch. When this happens, your local branch needs to be synchronized with the remote branch with `git pull` or `git fetch` and `git merge`.`git fetch` again takes 
your current branch, and checks to see if there is a tracking branch. If so, it looks for changes in the remote branch, and pulls them into the tracking 
branch. It does not change your local branch. To do that, you'll need to do `git merge origin/master` (for the "master" branch) to merge those changes into 
your branch - probably also called "master".`git pull` simply does a git fetch followed immediately by git merge. This is often what you desire to do, but 
some people prefer to use `git fetch` followed by `git merge` to make sure they understand the changes they are merging into their branch before the merge 
happens.
