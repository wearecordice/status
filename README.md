# Cordice status

Uptime monitoring for [Cordice](https://cordice.org), published at
**[status.cordice.org](https://status.cordice.org)**.

Nothing here runs on Cordice's own infrastructure, and that is the whole point.
The checks run on GitHub's machines every five minutes and the page is served by
GitHub Pages, so if our servers stop answering, this page keeps working and says
so. A status page hosted next to the thing it watches goes quiet exactly when
somebody needs it.

Built with [Upptime](https://upptime.js.org) (MIT). Configuration lives in
[`.upptimerc.yml`](.upptimerc.yml); everything else in this repository is
generated.

## Incidents

An outage opens an issue here and a recovery closes it, so the incident history
is the issue history — public, and written by the thing that noticed rather than
by somebody remembering to.

That covers "it stopped answering". It does not cover why, what is being done,
or anything a monitor cannot see: a fault that returns 200 while doing the wrong
thing, a problem only some people have, or the hour after the fix when we are
watching whether it holds. Those are written by hand.

**Open an issue from the Incident template.** The issue is the incident: its
title and body appear on the status page, so they are written for the person
whose call just dropped rather than for whoever will fix it. Add one severity
label — `major outage`, `partial outage`, `degraded` or `maintenance` — and then
post each new fact as a comment, each beginning with its state:

| State             | Means                                      |
| ----------------- | ------------------------------------------ |
| **Investigating** | We know, and we do not yet know why        |
| **Identified**    | We know why, and we are working on it      |
| **Monitoring**    | The fix is out and we are watching it hold |
| **Resolved**      | It is over                                 |

Close the issue when you post Resolved. Upptime closes the ones it opened
itself; a hand-written one is yours to close.

**Planned work** goes through the Scheduled maintenance template, which carries
a machine-read block of start and end times and the services expected to go
down. Upptime uses it to announce the window in advance and to keep the downtime
inside it from counting against our uptime.

## What is watched

Ten monitors, listed in [`.upptimerc.yml`](.upptimerc.yml) with the reasoning
for each. Two things are worth knowing about how they are written:

Where a service returns something only it would say, the check asserts on that
text rather than on the status code alone — a 200 proves something answered, not
that the right thing answered. The events server is the clearest case: a
WebSocket handshake cannot be made over the HTTP/2 these monitors speak, so it
answers a plain health path with a body no other part of the stack produces.

Every monitor sets `maxResponseTime`. Upptime's default is sixty seconds, which
is not a threshold so much as the absence of one — nothing here takes a minute,
so "degraded" could never be reached and the page drew three states while only
ever showing two.

## Working on this

Two things about the build are not obvious and cost an afternoon each:

**Editing the theme does not rebuild the page.** `Static Site CI` triggers only
on pushes that touch `assets/**`, plus a daily cron and manual dispatch. A change
to `.upptimerc.yml` alone will sit there looking applied and change nothing until
the workflow is run by hand.

**Service icons come from `history/summary.json`**, which is written by
`Summary CI` — a different workflow from `Uptime CI`. Change an icon in the
configuration and nothing moves until that one runs.

The page also calls the GitHub API from the reader's browser, which is limited
to 60 requests an hour per address. Reloading it while working will exhaust that
and replace the status with a rate-limit notice; it clears on its own.

## Licence

MIT, as inherited from the Upptime template. The software it monitors is
AGPL-3.0.
