# CLAUDE.md

## Project Overview

**Awesome Text-to-Humanoid** — a curated list of research on **language-conditioned whole-body motion generation and control for physical humanoid robots**, maintained as a single `README.md`.

## Taxonomy

Papers are organized by the **intermediate representation** between language and low-level control (see the Taxonomy table at the top of `README.md`):

1. **Explicit Motion Intermediate** — language conditions a motion generator that outputs explicit kinematic references (poses/trajectories), executed by a whole-body tracker.
2. **Without Explicit Motion** — no explicit kinematic reference at deployment: a single language→action policy, or a latent/intent/token intermediate not decoded into full poses.
3. **Vision-Language-Action (VLA)** — language-conditioned whole-body control that also consumes **visual** observations. VLA systems may internally look like Category 1 or 2, but are **always** listed under Category 3 because they take visual input.

A trailing **Related Methods and Resources** section covers adjacent skill-learning methods, physics-based character animation/generators, and datasets that support this research but are not language controllers for physical humanoid robots (e.g., SMPL-like simulated character control, kinematic motion diffusion without robot deployment).

## Adding a Paper

Each entry is one row in the relevant section's table:

```
| <YYYY‑MM> | **[<Paper Title>](<url>)** | <Venue> | <✅ if tested on a real robot, else blank> | <Resources> |
```

(the `Related Methods and Resources` table replaces the `Real Robot` column with `Type`, describing what kind of related work it is)

- **Date**: use a non-breaking hyphen (U+2011, `‑`) between year and month — e.g. `2026‑03`. Regular `-` will visibly break across two lines.
- **Paper link**: prefer the **official conference/journal proceedings link** (openaccess.thecvf.com for CVPR/ICCV, openreview.net for ICLR, proceedings.mlr.press for CoRL, roboticsproceedings.org for RSS, IEEE Xplore for Humanoids/IROS/ICRA, DOI for journals) over the arXiv abstract page **once the paper is confirmed accepted and published**. Fall back to the arXiv link if not yet accepted, or if a proceedings link can't be found.
  - **Before using any proceedings link, verify it is actually the same paper** — fetch and check the title/author list match. Camera-ready titles sometimes differ from the arXiv title (and unrelated papers can coincidentally share near-identical titles), so title similarity alone is not sufficient confirmation.
- **Venue**: `arXiv` if unpublished, otherwise `<Conference/Journal> <Year>` (e.g. `CVPR 2026`, `RSS 2025`, `IROS 2026`), optionally with `Oral` suffix.
- **Real Robot**: `✅` if the paper demonstrates deployment on physical robot hardware (not just simulation), else leave blank.
- **Resources**: optional links, each prefixed with an emoji, in this order:
  - 🏠 `[Project](<url>)` — project/website page
  - 💻 `[Code](<url>)` — code repository
  - 📊 `[Dataset](<url>)` — dataset page/collection
  - When a row has **more than one** resource link, separate them with `<br>` (one per line inside the cell) rather than a `·`.
  - **How to find them**: start from the paper itself (arXiv page or PDF) — it usually links a project page in the abstract, footnote, or "Project Page" link. Then check that project page for a code repository and/or dataset link, since those are often only listed there and not in the paper text itself.

**Ordering:** within each section's table, entries are sorted by date descending (newest first).

**Section choice:** pick the section matching the paper's intermediate representation, per the taxonomy above. When unsure whether a paper belongs in Category 1/2 vs. the Related section, check whether it controls a real (or physically simulated humanoid) robot via language — if not, it belongs in Related Methods and Resources instead.

## Verifying Paper Metadata

Before adding or editing an entry, fetch the arXiv abstract (or proceedings page) to confirm: title, authors, and whether the paper has since been accepted somewhere (check for "Accepted at ..." notices or version history). Don't guess venue/acceptance status from the paper title alone.

## Commit Style

Keep commits short and descriptive, e.g.:
- `Add <Paper Name> paper`
- `Update <Paper Name> link to <Venue> proceedings`
- `Fix table formatting for Resources column`

Only commit when explicitly asked.
