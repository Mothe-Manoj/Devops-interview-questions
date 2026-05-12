### How do you handle merge conflicts in Git?

When I encounter a merge conflict, I pause to understand which files are affected, examine the conflicting changes, and manually resolve them using a visual diff tool or editor. Once resolved, I mark the conflicts as resolved, stage the changes, and complete the merge or rebase.

# Explanation

Merge conflicts usually happen when:

- Two branches modify the same lines in a file
- One branch deletes a file the other modifies
- A rebase applies commits that overlap with existing changes

**Step 1: Identify the conflict**

Git clearly indicates the files with conflicts during a git merge or git rebase:

```
Auto-merging app.py  
CONFLICT (content): Merge conflict in app.py  
```

**Step 2: Open and resolve the conflict**
```
<<<<<<< HEAD
print("Hello from main")
=======
print("Hello from feature-branch")
>>>>>>> feature-branch
```

**Step 3: Mark as resolved**
