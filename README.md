# tg-infrastructure-example

This repository is where infrastructure deployments would be invoked from. There should be no module definitions here. You will find references to module definitions, commonly via pinned version using git tag.

This is a minial representation of how renovate interacts with this scenario (requiring exactly 2 modules, each module has exactly 1 reference defined within this repository).

## Observed Outcome

Renovate is unable to identify distinct dependencies, and see's both modules as being a single dependency using the git repository as the cannonical reference rather than the full folder which includes the location of the modules themselves.

As such, Renovate can not be configured to ignore module-1 whilst continuing to raise PRs for module-1.

## Expected Outcome

It is desired for Renovate to allow granular control of excluding modules which are defined by folder path within a git mononrepo.

This requires the dependencies to be identified by the full source path (see the source attribute definition in the terragrunt.hcl examples provided here), not just the repository.
