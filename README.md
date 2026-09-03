# WHAT THE FIZZ!? — System Status

Live status board for all 35 contracted systems, 15 player screens and the 1 admin tool.

**Client status page:** https://rul3ik9.github.io/wtfizz-status/
**Engineering log:** https://rul3ik9.github.io/wtfizz-status/dev.html

## What this is

A single rendered status surface over the Roblox Studio place, measured directly out of the running
place rather than read from documentation. It answers one question: *what is done, what is blocked,
and what is the evidence.*

It is a **summary view**. The detailed records stay in the private project repository under `docs/`
— `PROGRESS.md`, `INSTANCE-MANIFEST.md`, `CONFIG.md`.

## Two audiences, two pages

 is for the client and the agency. It carries the same system verdicts as the
engineering page, in plain language, with no defect log, no module names, and no verification
detail.

 is internal. It carries everything: the module inventory, every open finding, the
review history, the corrections, and the standing caveat that no Play session has been run.

**The client page must never assert that something is tested or verified.** Leaving internal QA
detail out is normal; claiming coverage that does not exist is not. Say what is built, what is in
progress, and what is waiting on a decision — nothing more.

## Update protocol — read before editing

**This page must be republished whenever any system changes state.** A stale status page is worse
than no status page, because it is trusted.

Any of these triggers an update and a push **in the same working session** as the change:

- a system's status moves in either direction
- a blocker opens or closes
- the save schema version bumps
- a catalogue count moves

### Order of operations

1. **Re-measure the live place first.** Never edit a status from memory or from documentation — the
   project docs have drifted twice already. Read it out of Studio.
2. Update the affected row: status pill, notes, and anything the change invalidates elsewhere.
3. Update the summary tiles and the `Measured` date in the header.
4. Commit and push. GitHub Pages redeploys on push, usually within a minute.
5. Mirror the change into the private repo's `docs/PROGRESS.md`.

### Accuracy rules

- **Measured, never assumed.** Every number on the page came out of the running place. If a value
  cannot be measured, say so rather than estimating it.
- **A green row is a claim you can be held to.** "Built but never played" is not DONE without the
  caveat that heads the page.
- **Record deviations, do not quietly absorb them.** Two currently ship knowingly and say so.
- **When documentation and the live place disagree, the live place wins** and the doc gets fixed.

## Scope of this repository

This repo contains **only the status site**. The game design document, its text extraction, the
marketplace fee analysis, and the Luau source are deliberately not here.

## Structure

```
index.html   client-facing status board — system verdicts and what is waiting on the brand owner
dev.html     engineering log — modules, defects, review findings, verification evidence, work log
README.md    this file
```

No build, no package manager, no CI. Edit `index.html`, commit, push.
