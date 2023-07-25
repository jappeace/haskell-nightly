# Haskell nightly template
With ghcup adding support for [nightly ghc builds](https://github.com/haskell/ghcup-hs/pull/825)
it's now possible to test your project with nightly ghc releases.
This allows detecting stability issues before a stable release happens.

This is an example github action of how to use nightly GHC builds
with [ghcup](https://www.haskell.org/ghcup/).
It's setup as a cron job,
which builds against the latest ghc-nightly release.

If a nightly build fails an issue is automatically created
with a link to the failed job.
Currently this shows up in recent activety,
but idealy it'd also show up as notification.
It doesn't do that because it thinks the user made the issue.
If anyonoe knows how to solve that please open an issue!

Note that I set it to once a week otherwise it'll burn
trough one's github action allowance fast.


## Usage

Copy over the file in .github/workflows/nightly.yaml
into your project.

for the token get it at https://github.com/settings/tokens
you need the public_repo permission only.
I'd set it to have infinite experiry so you don't end
up with silent failures.
Copy this token which you need in the next step.

In your repository settings,
go to `settings -> secrets and variables -> actions`
and click "new repository secret".
you need to add it with name `ISSUE_TOKEN`
and paste in the token you just made.
