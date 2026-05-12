### Explain the Git branching strategy you used in your company. Align it with the open-source branching strategy followed by Kubernetes.

- In my company, we followed a well-structured Git branching model similar to the Kubernetes project's workflow. Our strategy centered around four key branches:

```main``` – the default and stable development branch
```feature/*``` – for all new features and enhancements
```release/* ```– for preparing and testing production releases
```hotfix/* ```– for urgent bug fixes or patches to production
This helped us maintain stability while enabling parallel development and quick recovery from issues.


### Benefits of this Strategy:
- Supports parallel development and safe releases
- Keeps main clean and always deployable
- Makes it easy to trace features and bug fixes
- Aligns well with CI/CD automation and changelog generation


