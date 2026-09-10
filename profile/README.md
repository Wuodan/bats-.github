# Fork of org [bats-core](https://github.com/bats-core) and its repos

This org holds my forks of the repositories in `bats-core` (called `upstream` in this document).

Contributions should normally go upstream; this org is primarily a space for testing and hardening changes.

## Summary of changes per repo

> This information might be outdated or incomplete.

### Repo bats-action

Reduced to what an action should do - setup `bats` in a GitHub runner environment.

Changes:

- Removed caching: was broken and not needed for the tiny tarballs.
- Removed alternative installation paths, especially those needing `sudo`.  
  Was not needed for GitHub runners and blew up the number of necessary tests.
- Removed options to use older versions of bats repos. Pin to specific versions per action release instead.  
  The previous tests only covered the versions in the action input defaults.
- Harden downloads of bats repos by SHA-256 checksums.
- Add daily workflow checks of bats repo versions and create PRs for new versions and checksums.
- Simplify the installation of bats repos by not using npm.

Planned changes:

- Download release tarballs for bats repos instead of tarballs for git tags. Possibly split tarballs for running and for
  testing. Reasons: git tags are movable, GH release can be made immutable. Release artifacts allow splitting.
- Add linter workflows/setup and use them for an initial linting of the repo.

### Repo bats-assert

Only cleanup is planned.

Changes:

- Fix permissions in a test workflow. See [upstream PR #96](https://github.com/bats-core/bats-assert/pull/96).
- Add/use dependabot. See [upstream PR #97](https://github.com/bats-core/bats-assert/pull/97).

Planned changes:

- Add linter workflows/setup and use them for an initial linting of the repo.
- Review tests, some may be disabled on macOS.

### Repo bats-support

Only cleanup is planned.

Changes:

- Fix tests so they pass on Windows. See [upstream PR #22](https://github.com/bats-core/bats-support/pull/22).

Planned changes:

- Add linter workflows/setup and use them for an initial linting of the repo.
- Review tests, some may be disabled on macOS.

### Repo .github

Only cleanup is planned. This repo holds workflows for `bats-assert` and `bats-support`.

Changes:

- Add windows to the test matrix. See [upstream PR #15](https://github.com/bats-core/.github/pull/15).

Planned changes:

- Add linter workflows/setup and use them for an initial linting of the repo.
