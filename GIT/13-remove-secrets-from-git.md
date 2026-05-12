### A teammate accidentally committed a Kubernetes Secret (base64 encoded) to Git. What should you do?

Immediately remove the secret from the Git history using tools like git filter-repo or BFG, rotate the compromised secret, and enforce better secret management policies (e.g., use sealed secrets or external secret stores).

- Step 1: Rotate the compromised secret
    ``` kubectl create secret generic my-secret --from-literal=password=newpassword --dry-run=client -o yaml | kubectl apply -f -```
- Step 2: Remove the secret from Git history
```
git reset HEAD~1
git restore --staged secret.yaml
rm secret.yaml
git commit -m "Remove secret from repo"
```

But this only removes it from the latest commit. To fully remove it from entire history:

Use git filter-repo (preferred over filter-branch):

```git filter-repo --path secret.yaml --invert-paths```

- Step 3: Prevent it from happening again

Add sensitive files to ```.gitignore```

Summary:
Rotate → Remove → Recommit safely → Enforce policies.