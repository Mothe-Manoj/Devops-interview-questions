### Explain a recent challenge you faced with Git and how you addressed it.

A recent challenge I faced was implementing a consistent Git branching strategy across 100+ repositories used by multiple teams in my organization. Each team followed their own style — some had main/dev, others used master/feature, and a few used no long-lived branches at all. This inconsistency made CI/CD pipelines error-prone, releases chaotic, and collaboration difficult.

To solve this, we standardized on a lightweight **trunk-based branching strategy** with well-defined rules around main, release/*, and feature/* branches — and rolled it out in phases across teams.


# Explanation

At a company-wide level, multiple teams were independently managing Git repos, and the lack of a unified branching approach caused several issues:

- CI pipelines were failing due to missing expected branches like main or release.
- Some teams rebased public branches, which broke collaborators' work.
- Merge conflicts were common in integration environments.
- Releases were often delayed due to confusion about which branch was production-ready.


The result was:

95%+ repos aligned within 2 months.
CI/CD pipeline reliability improved significantly.
Teams were clearer on how and when to branch or merge.
It became easier to onboard new developers and automate release workflows.