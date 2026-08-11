# Workflows

Upptime ships two more than these: `setup.yml`, which rewrites the repository
from the template, and `update-template.yml`, which pulls template changes in.
Both were removed.

They edit the workflow files themselves, which the built-in token cannot do and
should not be able to do — allowing it means anything that can trigger a
workflow can rewrite what the workflows are. Upptime's answer is a personal
access token with the `workflow` scope, stored here as a secret. This repository
is public, so that token would be one misconfigured permission away from being
the most valuable thing in it.

The cost is that template updates are applied by hand. That is the correct
trade: the configuration in `.upptimerc.yml` is ours, and a bot rewriting our
build in order to keep up with an upstream default is not something we want
happening unattended.
