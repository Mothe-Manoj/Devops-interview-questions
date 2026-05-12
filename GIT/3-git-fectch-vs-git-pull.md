### What is the difference between git fetch and git pull, and when would you use each?

- git fetch retrieves the latest changes from the remote repository **without merging** them into your current branch.

- git pull does the same as fetch but also **automatically merges** the changes into your current branch.

## Explanation

When you run git fetch, you’re asking Git to contact the remote (like GitHub) and download any changes (new commits, branches, tags) — but not apply them to your working directory.

```git fetch origin```


git pull, you're doing this plus merging the changes into your current branch in one step:

``` git pull origin main ```

That’s shorthand for:

``` git fetch origin && git merge origin/main```


Use git fetch when you want control.
Use git pull when you’re ready to sync changes directly.


I mostly use git pull because it streamlines my workflow by fetching and merging remote changes in one step. It’s convenient for staying up to date quickly, especially when collaborating in fast-moving branches.

This makes my routine faster and keeps my local branch synchronized with the remote without extra steps. It's particularly useful when:

- I’m working alone or in a small team where merge conflicts are rare
- I'm contributing to a feature branch that others aren’t modifying
- I want to frequently pull in the latest changes to test or deploy updates
