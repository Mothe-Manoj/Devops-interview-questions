### How do you combine multiple commits into a single commit in Git?

I use interactive rebase to squash multiple commits into a single, meaningful commit before pushing my changes. This helps in keeping the Git history clean and easy to read.

# Explanation

```
git log --oneline
```
Here’s how I do it:
``` 
git rebase -i HEAD~4 
git push origin branch-name --force
```
