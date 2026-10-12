# Git Flow

## Why change the branch strategy?

Earlier competitions used persistent `main` plus temporary feature/test branches. Without a deployed service this was manageable. For a deployed application, however:

- Unreviewed changes could enter the deployed branch and introduce serious bugs.
- Experimental functionality could be deployed unintentionally.
- Fixing and reviewing directly on the deployment branch complicated release management.

Before the prototype, merging changes into `main` caused errors and disrupted deployment work. The team concluded that a separate development branch was needed before an actual service outage could occur.

## Strategy

<img src="https://user-images.githubusercontent.com/67851701/217207335-382c3f47-290a-459b-b34c-3b9c7d90acd1.png" width="400">

Persistent branches:

- `main`: deployed version.
- `dev`: next release under development.

Temporary branches:

- `feat`: feature development.
- `release`: prepare and validate a release before deployment.
- `hotfix`: urgent fixes for the deployed version.

## Workflow

1. Develop on a feature branch.
2. Open a PR into `dev` when ready.
3. Delete the feature branch after merging; create a new one for the next task.
4. Branch `release` from `dev` when ready to ship.
5. Validate and fix issues on `release`.
6. Merge into `main` for deployment.
7. Create a hotfix branch for urgent bugs in the deployed version.

## Project Git graph

<img src="https://user-images.githubusercontent.com/67851701/217730239-d984b3cd-9915-452c-8894-28cda6f6e29f.png" width="400">

[Original reference: Woowa Brothers](https://techblog.woowahan.com/2553/)


---

[Wiki home](Home.md) · [Original Korean source](https://github.com/boostcampaitech4lv23recsys2/final-project-level3-recsys-12/wiki/Git-Flow)
