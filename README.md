# Rush Sandbox

This is an example monorepo setup with [Rush](https://rushjs.io/).

## Purpose

[Rush](https://rushjs.io/) is a great tool to manage monorepos, but it does not provide examples or tutorials for uncommon workflows.

The purpose of this `rush-sandbox` repository is to provide a place to test out monorepo workflows and setups.

## Use Cases

Here are the use cases solved by `rush-sandbox`.

### Release Channels

Release channels allow you to publish versions in parallel, without disruption to stable releases from your `main` branch.

In our case here, we utilize [version policies](https://rushjs.io/pages/maintainer/publishing/#two-types-of-version-policies) and [publish prerelease options](https://rushjs.io/pages/commands/rush_publish/).

To avoid disrupting existing contributor workflows, we do the following:

- Lock major versions in [`common/config/rush/version-policies.json`](common/config/rush/version-policies.json).
- Add relevant policies to packages in [`rush.json`](rush.json).
- Set up `next/**` branches in the [`.github/workflows/publish.yml`](.github/workflows/publish.yml) workflow.

Note that `next/**` branches should also be set up with branch protection rules in GitHub.
