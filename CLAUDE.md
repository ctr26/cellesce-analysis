# CLAUDE.md

## What this is

Analysis code for a colorectal-cancer organoid drug-screen (CellProfiler feature
CSVs) — phenotypic distance metrics, PCA/tSNE, outlier removal, drug/cell/dose
classification, IC50 dose-response. `master` is a **single 2,372-line
`analysis.py`** script from 2021: flag-driven, hardcoded globals, commented-out
blocks, and it reads gitignored local data
(`./analysed/<folder>/raw/projection_XY/*.csv`) that is **not in the repo** —
so `master` does not run out of the box and is not reproducible.

## Current state: dormant, revival in progress on another branch

`master` itself is dead code (last real commit 2021-12-09). A revival is
**~60% done** on the unmerged branch `modernise/efaar-dino-cp` (checked out as
a worktree elsewhere: `/Users/ctr26/projects/cellesce-modernise-efaar-dino-cp`)
with a proper `src/cellesce/` package, `pyproject.toml` (py3.12, hatchling),
Prefect flows, EFAAR/MoA/DINO modules, and offline smoke tests. Full plan and
rationale: `REVIVAL_PLAN.md` in this repo root (untracked as of 2026-07,
generated 2026-07-02).

**If asked to work on cellesce: read `REVIVAL_PLAN.md` first, then prefer the
`modernise/efaar-dino-cp` branch/worktree over touching `master`'s `analysis.py`.**

## Stack (master branch only)

`environment.yml` — conda env `idr-omero` / `cellesce`, pip + numpy/scipy/
scikit-learn/pandas/matplotlib/seaborn. No test suite, no lint config, no CLI
on `master`. The `modernise` branch is Python 3.12 + uv/hatchling instead —
see that branch's own files, not this one's, for its actual toolchain.

## Gotchas

- `master` has no reproducible entrypoint — `analysis.py` expects local data
  that was never committed.
- Don't add new work to `master`'s `analysis.py`; it's being superseded, not
  extended.
