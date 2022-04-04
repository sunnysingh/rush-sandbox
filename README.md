# Rush Sandbox

This is an example monorepo setup with [Rush](https://rushjs.io/).

## Purpose

[Rush](https://rushjs.io/) is a great tool to manage monorepos, but it does not provide examples or tutorials for uncommon workflows.

The purpose of this `rush-sandbox` repository is to provide a place to test out monorepo workflows and setups.

## Use Cases

Here are the use cases demonstrated by `rush-sandbox`.

### Release Channels

Release channels allow you to publish a separate major version in parallel to your `main` branch.

In our case here, we utilize [version policies](https://rushjs.io/pages/maintainer/publishing/#two-types-of-version-policies) and [publish prerelease options](https://rushjs.io/pages/commands/rush_publish/).

To avoid disrupting existing contributor workflows, we do the following:

- Lock major versions in [`common/config/rush/version-policies.json`](common/config/rush/version-policies.json).
- Add relevant policies to packages in [`rush.json`](rush.json).
- Set up `next/**` branches in the [`.github/workflows/publish.yml`](.github/workflows/publish.yml) workflow.

Note that `next/**` is a convention which makes sense for publishing to a future major version of your package under a different [npm dist-tag](https://docs.npmjs.com/adding-dist-tags-to-packages). However, you can use a different convention for other use cases such as when you have to maintain older major versions. Also, if your packages form together into a framework, then you can use a single `next` branch. You will also likely want to use [lockstep versioning](https://rushjs.io/pages/maintainer/publishing/#two-types-of-version-policies).
