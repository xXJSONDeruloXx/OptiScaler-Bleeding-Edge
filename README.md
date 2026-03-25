# OptiScaler-Bleeding-Edge

GitHub Actions workflows for building [`optiscaler/OptiScaler`](https://github.com/optiscaler/OptiScaler) from source in this repository.

## Channels

### Upstream Master Build
- daily scheduled build of upstream `master`
- creates a prerelease only when a new upstream `master` HEAD is detected
- manual runs upload workflow artifacts by default; enable `publish_release` to publish a prerelease
- release tag format: `master-<sha8>`

### Upstream Latest Any Branch Build
- daily scheduled build of whichever upstream branch head has the newest commit
- creates a prerelease only when that resolved branch head has not been released yet
- manual runs upload workflow artifacts by default; enable `publish_release` to publish a prerelease
- release tag format: `any-<branch>-<sha8>`

## Release assets

Each successful build produces:
- a `.7z` package
- a JSON metadata file containing the resolved branch, commit SHA, tag, and build timestamp

Release bodies are intentionally minimal and contain only the upstream commit link.

## Notes

- Builds are unsigned
- Releases are built from source in this repository, not from upstream Actions artifacts
- Dependency bundling is not included
