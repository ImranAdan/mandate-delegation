# mandate-delegation

The owner's delegation to **Mandate**: which pull requests Mandate may authorize
on its own, what evidence each class needs, and what always goes back to the
owner.

This repository is deliberately **separate from every repository Mandate
governs**. A pull request in a governed repository can never change the rules
that judge it.

## Rules for this repository

- **Only the owner changes it.** Changes arrive as owner-merged pull requests.
  Force-pushes and branch deletion are blocked by a ruleset.
- **No agent and no App writes here.** The Mandate App is not installed on this
  repository. Mandate reads it at a pinned commit, and every decision receipt
  records that commit.
- **Public on purpose.** It contains no secrets, and on GitHub Free only public
  repositories can enforce the ruleset that protects it. Mandate's safety does
  not depend on hiding these rules: it classifies the actual diff and checks
  evidence instead of trusting a PR's description.
- **Reserved categories can't be delegated in version 1.** Credentials,
  permission or authority widening, IAM, permanent infrastructure, migrations,
  merge authority, this delegation and enforcement settings always escalate to
  the owner. Mandate's loader rejects a file that tries to authorize them.

## Layout

```
repositories/<repository-name>.yaml   one governed repository per file
```

Each file follows the delegation contract:
https://project-mandate.atlassian.net/wiki/spaces/KAN/pages/131135

## Status

`mode: shadow`: Mandate records decisions and receipts but merges nothing.
Enforcement is a separate, later owner decision.
