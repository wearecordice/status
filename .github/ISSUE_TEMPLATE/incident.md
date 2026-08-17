---
name: Incident
about: Something is wrong with a Cordice service, and readers should be told
title: "Short sentence naming what is broken"
labels: incident
assignees: schadomia
---

<!--
This issue IS the incident. Everything written here appears on
status.cordice.org, so write it for the person whose call just dropped, not for
the person who will fix it.

The title is what most people read. Name the thing that is broken and what it
means for them — "Voice channels disconnect after a few seconds" rather than
"LiveKit SFU failure".

Add one severity label:

  major outage     nobody can use it
  partial outage   some people, or some of it
  degraded         it works, badly — slow, flaky, some requests failing
  maintenance      planned, and we chose the time

Then leave the issue open and post each new fact as a comment, newest last,
each one starting with its state:

  **Investigating** — we know, and we do not yet know why
  **Identified**    — we know why, and we are working on it
  **Monitoring**    — the fix is out and we are watching it hold
  **Resolved**      — it is over

Close the issue when you post Resolved. Upptime closes the ones it opened by
itself; this one is yours to close.
-->

**Investigating** — what a reader can see, when it started, and what still
works. If there is a way around it, say so here rather than further down.
