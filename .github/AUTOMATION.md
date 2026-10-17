# Maintenance automation

The release port, flake lock sync, and vendor hash workflows run in upstream
and fork repositories. They use the repository's `GITHUB_TOKEN` with explicit
write permissions unless both `APP_ID` and `APP_PRIVATE_KEY` secrets are set.
With both secrets configured, they use a GitHub App installation token instead.
Partial App configuration falls back to `GITHUB_TOKEN`; invalid configured
credentials fail rather than silently changing identities.

Repository and branch policies must allow the workflow to push. Ports also
require the target release branch to exist and allow issue creation.

Pushes made with `GITHUB_TOKEN` do not trigger further push workflows. Configure
the GitHub App secrets if bot commits must trigger CI or follow-up automation.
The manual flake sync and vendor hash workflows remain available from Actions.
