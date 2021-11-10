# Get good at git

One thing i am slowly learning is how to work well in git. Today i
needed to clean up my main development that i had stuffed up. To do this
i ran
`git reset --hard origin/main`

This killed the current modifications. On the directory. If some things
aren't removed i can then run
`git clean -sdf`
To remove these files.

One issue i find is that i haven't always labelled the remote branch as
origin. To find out what this branch is called, i can either call 

`git remote show`
or
`git branch -vv`
Which will give me information on my current remote upstream.

I have also been looking at how to do breaking changes in development
and started looking into `git worktree`. There are a couple of good
articles out there including
(git-worktree)[https://opensource.com/article/21/4/git-worktree]
(best git
features)[https://levelup.gitconnected.com/git-worktrees-the-best-git-feature-youve-never-heard-of-9cd21df67baf]
(never switch
branches)[https://www.theserverside.com/blog/Coffee-Talk-Java-News-Stories-and-Opinions/Use-this-git-worktree-add-example-and-never-switch-branches-again]

There is so much more i need to learn about git but i am slowly getting
there.



