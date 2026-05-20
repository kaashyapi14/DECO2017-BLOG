---
title: Blog 5 - From Wireframes to a Real Data Model
date: 2026-05-13
author: Kaashyapi Agarwal
summary: Mapping every page to a data structure and designing the five database tables that power Folio Hub before a single route is written.
tags:
  - database
  - data modelling
  - folio hub
---

# Blog 6 — Building and Evaluating Folio Hub

---

## Building the Interface

With all seven HTML and CSS pages built, the interface is complete and consistent throughout. The feed, post a pitch, pitch detail, manage applicants, build checklist, showcase and profile pages are all done as static HTML.

<figure>
  <img src="../assets/images/html 1.png" alt="Built HTML pages screenshot 1" width="700">
  <figcaption>The completed static interface — consistent design system across all seven pages</figcaption>
</figure>

<figure>
  <img src="../assets/images/html 2.png" alt="Built HTML pages screenshot 2" width="700">
  <figcaption>DM Serif Display for headings, DM Sans for UI, saffron amber reserved for badges and ratings</figcaption>
</figure>

<figure>
  <img src="../assets/images/html 3.png" alt="Built HTML pages screenshot 3" width="700">
  <figcaption>All seven pages built as static HTML before the backend is connected</figcaption>
</figure>

The design system holds across every page — **DM Serif Display** for headings, **DM Sans** for UI, warm off-white background with saffron amber reserved only for badges and ratings. The next step is connecting MojoJS routes and SQLite to make everything functional.

---

## User Testing

User testing is currently underway. We walked our design peers through the core journey — posting a pitch, applying to one and completing the checklist — and observed where they hesitated or got confused. The focus was on three things: whether the two-state pitch detail page is immediately clear, whether the checklist completion flow feels intuitive, and whether the badge mechanic is understood without explanation. Feedback is being used to refine copy, button placement and information hierarchy before the backend is connected.

---

## Accessibility

Accessibility has been built in from the start rather than added at the end.

- Star ratings and interactive buttons use `aria-labels` so screen readers announce values correctly.
- All form fields have explicit `label` elements — placeholder text alone disappears when typing and isn't reliably read aloud.
- Role slot status uses a text label alongside colour so open and filled states are never communicated by colour alone.

These decisions directly address the AA compliance requirement from the brief.

---

## Privacy and Platform Responsibility

BlaBla Corp handles authentication centrally so Folio Hub doesn't store passwords or login data. However the platform stores user-generated content — pitch descriptions, comments and ratings — which means content moderation needs consideration.

There is no flagging system in the current prototype, which is a known gap. EU cookie policy compliance is required by the brief — session cookies need to be clearly disclosed. Rating integrity is also an open question; nothing currently prevents vote manipulation, which would need addressing before any real deployment.

---

## What to Refine

With all seven pages built, the focus now shifts to connecting the backend.

- **MojoJS routes** need to be written for every page.
- **SQLite** needs to be populated with the right tables.
- **HTMX interactions** need to be wired up.
- The **showcase** needs the rating and badge logic built end to end.
- The **manage applicants page** needs the lock team button to correctly update project status.
- The **profile tabs** need the right queries pulling the correct projects into each view.

The goal is a working end-to-end journey from posting a pitch to earning a badge before the final submission.