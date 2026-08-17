# assets

Only one file has ever lived here, and it is gone: the theme moved into
`.upptimerc.yml`, which is the copy that actually ships.

The directory stays because `Static Site CI` triggers on pushes that touch
`assets/**` and on nothing else in this repository. Removing it would leave the
page rebuildable only by cron or by hand, which is a poor thing to discover
during an incident.
