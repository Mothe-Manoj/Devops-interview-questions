### What is the difference between git rebase and git merge? When would you use each?

- git merge integrates changes by creating a new merge commit, preserving the history of both branches.
- git rebase moves your branch on top of another, rewriting commit history to create a linear sequence.

### Using git merge:

```
A---B---C (main)
     \
      D---E---F (feature)
             \
              G (merge commit)
```

Pros:

- Preserves full history and context
- Safer in teams: no history rewriting
- Good for long-lived shared branches

Cons:
- History becomes messy with many merge commits
- Harder to trace linear commit flow

### Using git rebase:

```
A---B---C (main)
             \
              D'---E'---F' (rebased feature)
```

Pros:

- Clean, linear history
- Easier to git log and git bisect
- Preferred before merging short-lived branches into main

Cons:

- Rewrites commit history
- Risky if already pushed and others have based work on it
- Not ideal for shared/public branches


git merge integrates changes by creating a new merge commit, preserving the history of both branches.

git rebase moves your branch on top of another, rewriting commit history to create a linear sequence.