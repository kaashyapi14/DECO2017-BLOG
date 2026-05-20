---
title: Blog 3 
date: 2026-05-13
author: Kaashyapi Agarwal
summary: Stripping Spark back, narrowing the audience to designers, and mapping the sitemap and user flow for Folio Hub.
tags:
  - folio hub
  - sitemap
  - user flow
---
# Finalising the Idea and Structure

---

## Limitations of the Previous Idea

As our group discussions began going into more details on the project it felt like Spark was the right direction but the more we mapped it out the more problems surfaced. Two things became clear quickly.

The first was **complexity**. The Spark Score required tracking community ratings, nudge counts and recency weighting across multiple database tables simultaneously. As beginners working with MojoJS and SQLite for the first time, we hadn't written a single route yet and already the data model was becoming unmanageable. The feature that made Spark feel unique was also the feature most likely to sink the project.

The second was the **audience**. Spark was open to every creative discipline (design, tech, music, writing, film). That sounds inclusive but in practice it made every decision harder. What does a pitch card look like when it needs to work for a musician and a graphic designer equally? The broader the audience the vaguer the requirements become, and vague requirements are impossible to build around.

---

## Narrowing the Concept

The brief essentially asks for something "tailor made" — a hub that tries to serve everyone risks becoming something that already exists. Therefore, as a group we made two decisions together.

**1. Strip Spark back to its core journey:** pitch, apply, build, share. Everything that was too complex beyond that got cut. The Spark Score was replaced by a simple star rating on completed projects. The original system required three simultaneous events which would have introduced bugs and would have been difficult to implement in time. The completion vote system was also cut as it needed a separate database table and multi-user coordination that could stall if one member went inactive. The owner marking the project complete is enough.

**2. Narrow the audience entirely to designers building portfolio work.** Not all creatives — only design students and graduates who need real collaborative projects to show employers. Due to this, the tags became design disciplines: Brand, UI/UX, Product, Editorial, Motion. The roles became design-specific and the language shifted accordingly. Deliverables on each pitch became concrete design outputs: logo suite, brand guidelines, type system.

<figure>
  <img src="../assets/images/blog-3-folio-hub.png" alt="Folio Hub concept overview" width="700">
  <figcaption>Folio Hub — the narrowed concept built around designers and portfolio work</figcaption>
</figure>

> We named the platform **Folio Hub** — where folio abbreviates portfolio and hub reflects the community.

---

## Redesigning the Checklist Feature

The previous tracker was replaced with an owner-defined checklist where the owner of the project could add up to five tasks, and the team ticked them off — this updates the progress bar. This looked like a cleaner structure with the same accountability purpose.

---

## Sitemapping
<figure>
  <img src="../assets/images/sitemap-1.png" alt="Sitemap for Folio Hub" width="700">
  <figcaption>Sitemap — every page mapped with access control before a line of code was written</figcaption>
</figure>

<figure>
  <img src="../assets/images/sitemap-2.png" alt="Sitemap for Folio Hub" width="700">
  <figcaption>Sitemap — every page mapped with access control before a line of code was written</figcaption>
</figure>

> Mapping screens before writing any code forces a concrete question: what does the platform actually need versus what would be convenient to have?

<figure>
  <img src="../assets/images/sitemap-table.png" alt="Sitemap for Folio Hub" width="700">
  <figcaption>Sitemap — every page mapped with access control before a line of code was written</figcaption>
</figure>

The completion vote and share pages were merged into one — confirming done and sharing to the showcase is one moment, not two screens. The access control column matters as much as the page list because it shows conditional logic that needs to be planned into every route before a line of code is written.

---

## User Flow

<figure>
  <img src="../assets/images/user-flow.png" alt="User flow diagram for Folio Hub" width="700">
  <figcaption>User flow — the owner and designer journeys mapped before any routes were written</figcaption>
</figure>

Mapping the flow made something visible that the sitemap doesn't show — Folio Hub has two parallel journeys. The owner creates and manages. The designer browses and applies. Both paths converge at the build phase and finish together at the showcase. Mapping this before building meant we could identify where conditional logic needed to live before writing a single route.

---

## What's Next

With the sitemap and user flow mapped, the next step is turning each page into wireframes — getting the layout and information hierarchy figured out before any code is written.