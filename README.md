# CPSC 100 — Course Development

Internal course-development repository for CPSC 100 (Computational Thinking), UBC.

This repo holds the material used to **build** the course: templates, the authoring
guide, canonical learning outcomes, shared terminology, and lecture planning artifacts.

The **public course website** lives in a separate repo:
[Parsa-Rajabi/CPSC-100](https://github.com/Parsa-Rajabi/CPSC-100), published from
`main:/docs` to <https://parsa-rajabi.github.io/CPSC-100/>.

## Why two repos

Everything under `docs/` in the public repo is served by GitHub Pages, whether or not
the sidebar links to it. There is no way to keep a page in that folder and off the live
site. Splitting the repos means planning artifacts, draft material, and internal notes
are never one guessed URL away from students.

| | Public repo | This repo |
|---|---|---|
| Audience | Students | Instructor, TAs, course designers |
| Contents | Syllabus, policies, assignment pages, rubrics students read | Templates, authoring guide, outcomes, lecture outlines |
| Published | Yes, via GitHub Pages | No |

> [!IMPORTANT]
> This repository is currently **public**. Anything committed here is world-readable.
> Do not commit unreleased exam questions, solutions, grading keys, or student
> information until the visibility has been reviewed.

## Layout

```text
_templates/                     Artifact shapes. Copy these when starting something new.
  lecture-outline.md            Internal lecture planning artifact
  activity.md                   Student-facing lab or project page
  rubric.md                     Criterion-referenced rubric

_authoring/
  teaching-material-guidelines.md   Read this before creating or reviewing material

_shared/
  learning-outcomes.md          Canonical outcomes. Copy from here; do not invent.
  terminology.md                Consistent naming across all material

lectures/
  outlines/                     Planning artifacts, one per lecture
  notes/                        Developed notes, derived from outlines

labs/                           Lab drafts, before publishing to the public repo
projects/                       Project drafts
rubrics/                        Rubric drafts
```

## How to use this

**Starting a lecture:** copy `_templates/lecture-outline.md` into `lectures/outlines/`,
pick outcomes from `_shared/learning-outcomes.md`, then write the Big Idea before
anything else.

**Starting a lab or project:** copy `_templates/activity.md` into `labs/` or `projects/`.
Write the rubric from the assignment page, not the other way around.

**Publishing:** student-facing pages move to the public repo's `docs/` when they are
ready. Planning artifacts stay here.

## Rules that matter most

1. Read `_authoring/teaching-material-guidelines.md` first.
2. Use only outcomes from `_shared/learning-outcomes.md`. Do not invent outcomes to
   justify content you want to teach.
3. Link to canonical policy in the public repo's syllabus rather than restating it.
4. Mark unresolved curriculum decisions as `TODO: instructor decision required` so they
   can be found with `grep -rn "instructor decision required" .`
5. AI-generated material is a draft for human review, never a finished artifact.

## Source

The design behind this system is documented in
`course-material-template-agent-handoff.md` in the public repo.
