# Version Control Workflow

## Branching Strategy

- `main` — stable branch
- `develop` — development/integration branch
- `feature/add-classification-report` — feature development
- `conflict-demo-a` — conflict demonstration (Version A)
- `conflict-demo-b` — conflict demonstration (Version B)

## Pull Request Workflow

The classification report feature was developed in the feature branch and submitted as a Pull Request to the `develop` branch.

The Pull Request was reviewed and successfully merged into `develop`.

## Merge Conflict Resolution

A merge conflict was intentionally created between `conflict-demo-a` and `conflict-demo-b` by modifying the same line in `README.md`.

The conflict was resolved by keeping Version B, after which the resolved changes were committed and pushed.

## Verification

The repository was verified using Git commands including:

- `git status`
- `git branch -a`
- `git log --oneline --graph --all`

The working tree was clean after completing the workflow.