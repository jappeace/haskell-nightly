# Haskell nightly template
With ghcup adding support for [nightly GHC builds](https://github.com/haskell/ghcup-hs/pull/825),
it's now possible to test your project with nightly GHC releases.
This allows for detecting stability issues before a stable release happens.

This is an example [GitHub action](https://github.com/features/actions)
of how to use nightly GHC builds
with [ghcup](https://www.haskell.org/ghcup/).
It's set up as a cron job,
which builds against the latest GHC-nightly release.

If a nightly build fails, an issue is automatically created
with a link to the failed job.

Note that I set it to once a week; otherwise, it'll burn
through one's GitHub action allowance fast.

## Usage
Copy over the file in `.github/workflows/nightly.yaml`
into your project.

## Projects with Dependencies

GHC prereleases often require patched versions of various package.
The GHC team maintains a collections of patched packages for
testing purposes, called [head.hackage](https://ghc.gitlab.haskell.org/head.hackage/).
When testing your code with a nightly version of GHC, you may need
to follow the instructions on the `head.hackage` page to enable it.

The patches in `head.hackage` have not necessarily been reviewed
or accepted by the package maintainers - it should only be used for
testing prelease compilers, and please don't report patch-related bugs
to the package maintainers.
