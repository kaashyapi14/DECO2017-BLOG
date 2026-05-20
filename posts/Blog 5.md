---
title: From Wireframes to a Real Data Model
date: 2026-05-13
author: Kaashyapi Agarwal
summary: Mapping every page to a data structure and designing the five database tables that power Folio Hub before a single route is written.
tags:
  - database
  - data modelling
  - folio hub
---

# Blog 5 — From Wireframes to a Real Data Model

---

After wireframing, moving to actual code meant figuring out exactly what data each page needs, where it comes from, and how it all connects. Before writing a single route we mapped out the full data structure. Getting this wrong early would mean restructuring tables halfway through the build, which breaks everything already working.

---

## Database Tables

After mapping every page we landed on five tables in our SQLite database — each one has a clear job.

---

### DDD — Users

Each and every page reads from the users table in some way or the other. The nav bar, pitch cards, applicant lists and the badge trigger all depend on it.

---

### DDD — Projects

This is the table central to all — every page reads or writes to it in some form.

> The `status` column does the most work in the entire schema. Every access control check reads it before rendering a page — the feed only shows `open` projects, the checklist only loads for `team_locked` ones, the showcase only displays `shared` ones. Keeping it as one column moving through four states rather than separate boolean flags kept the queries simple and avoided conflicting states.

---

### DDD — Applications

---

### DDD — Checklist Items

Probably the simplest table — one row per task, one boolean to track completion. The progress bar percentage is calculated from a single count query: completed items divided by total items multiplied by 100. No extra columns needed, which was a deliberate choice to keep things manageable.

---

### DDD — Project Ratings

One row per user per project. Before any new rating is inserted the route checks for an existing row so no one can rate twice. After every insert MojoJS calculates the average and if it hits 3 or above, `has_badge` updates to `1` for the owner and every accepted applicant automatically.

---

## What the ERD Reveals

Three important things surfaced from drawing the relationships between the five tables.

**1. Users sit at the centre of all.** It connects to projects, applications and ratings — meaning almost every route touches this table in some way.

**2. The applications table is doing double duty.** It's both the many-to-many link between users and projects and the access control list for the build page. Every team-gated route queries this table first.

**3. There's no separate showcase table.** Shared projects are just projects with `status = shared`. That one decision cut an entire table and keeps the showcase query to a simple `SELECT` with a `WHERE` clause.

---

> **Trade-off worth naming:** we consciously stored `who_needed` as a comma-separated string rather than a separate roles table. It works for our scope of three roles maximum but would break if we ever needed to query by individual role. It's a decision, not an oversight.

---

## What's Next

With the data model mapped and the stack decisions made, the next step is building out the remaining HTML and CSS pages and running user testing on the static interfaces. Once all seven pages are done the focus shifts to accessibility, evaluation and platform responsibility — and what needs to be refined before the backend is connected. That's what the final post covers.
