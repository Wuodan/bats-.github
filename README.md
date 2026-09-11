# .github

Reusable workflows found in `.github/workflows`.
GitHub does not distinguish workflows that should run in this repository,
from reusable workflows that are expected to be called elsewhere.
The only way to tell is that reusable workflows include `workflow_call` event trigger.

## Releasing

Consumers should pin reusable workflows to a full commit SHA and use Dependabot
to keep those references up to date.

```yaml
jobs:
  test:
    uses: bats-hardened/.github/.github/workflows/test.yml@bf6af8f41d7743ef9d0f69a35e93a3800d07131f # v1.1.1
```

Pushing a full SemVer tag, such as `v1.2.3`, for a commit on the default branch
runs the tests and publishes a GitHub Release with generated release notes.
