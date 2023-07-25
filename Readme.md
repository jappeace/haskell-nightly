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
Currently, this shows up in recent activity,
but ideally, it would also show up as a notification.
It doesn't do that because it thinks the user made the issue.
If anyone knows how to solve that, please open an issue!

Note that I set it to once a week; otherwise, it'll burn
through one's GitHub action allowance fast.


## Usage

Copy over the file in `.github/workflows/nightly.yaml`
into your project.

For the token, get it at https://github.com/settings/tokens
You only need the `public_repo` permission.
I'd set it to have infinite expiry so you don't end
up with silent failures.
Note that only the "classic" token supports infinite
expiry for some reason.
Copy this token which you'll need in the next step.

In your repository settings,
go to `settings -> secrets and variables -> actions`
and click "new repository secret".
You need to add it with the name `ISSUE_TOKEN`
and paste in the token you just made.
