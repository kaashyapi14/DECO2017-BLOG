---
title: Blog 2
date: 2026-05-13
author: Kaashyapi Agarwal
summary: How our group combined three separate concepts into one unified platform called Spark.
tags:
  - group work
  - concept development
  - spark
---
# Three Ideas, One Direction

---

## Bringing It Together

As a group, we each came in with a separate concept and sat down to figure out which direction made the most sense. The three ideas on the table were my Project Builder Hub, Maia's Music Collaboration Platform, and Aditi's Indie Game Review Community.

---

## Each Idea Breakdown

<figure>
  <img src="../assets/images/blog 2 ideation comparison table.png" alt="Ideation comparison of the three concepts" width="700">
  <figcaption>Comparing the three concepts across feasibility, scope and community depth</figcaption>
</figure>

**Music Collaboration Platform** had the most exciting concept but the problem was the technical reality. Audio engineering in the browser requires the Web Audio API, which is well beyond our skill level and current stack.

**Project Builder Hub** had solid structure and the community spirit but it felt too broad with no clear identity to stand out from existing platforms. Without a specific audience the functional requirements become too vague to build around.

**Indie Game Review Community** was the most technically achievable but too niche for meaningful community depth and user testing. The brief asks for a community that hives, but a narrow audience makes that hard to demonstrate.

None of them felt complete alone, but each had something worth keeping.

---

## SPARK

Rather than picking one and dropping the rest, we borrowed the strongest parts from each and combined them into a hub for creatives — a place where people pitch short-term projects, build a real team, and finish something together. We called it **Spark**.

Spark has four core stages: pitch an idea, get rated, build your team, and create something real. Three mechanics that make it distinct:

---

### Score System

Rather than a simple star average, ideas gather a score based on community ratings, number of nudges received, and recent activity. Ideas crossing a target earn "hot idea" status in the weekly spotlight. This matters because a static feed gives users no reason to return — but this keeps the discovery experience dynamic and rewards quality over popularity.

---

### Role-Based Team Slots

Creator defines exactly who they need — "1 designer, etc." — rather than leaving collaboration open-ended. Each slot shows as open or filled, and applicants specify which role they're applying for, and the creator accepts or declines per role. Once all slots are filled the project locks into build mode automatically. This is a core functional requirement as without defined roles the team assembly has no structure and the build phase can't unlock meaningfully.

---

### Structured Build Phases

Once assembled the team moves through five phases: **Ideate, Plan, Build, Ship, Reflect**. Each phase has a shared checklist and live progress bar. This serves a key user need — accountability — as without visible progress the platform becomes another space where ideas start but nothing gets finished.

---

## Scope

<figure>
  <img src="../assets/images/Scope spark.png" alt="Scope breakdown for Spark" width="700">
  <figcaption>Scope — must-haves versus could-haves for the Spark platform</figcaption>
</figure>

**Must-haves:** idea pitching with tags and role slots, Spark Score, nudge system, discovery feed, build mode phase tracker, outcome card, badge on completion.

**Could-have later:** weekly spotlight feature, advanced feed filtering, emoji reactions on outcomes.

---

## Risks

- The Spark Score tracks ratings, nudges and recency simultaneously — significant backend complexity before a single page loads.
- Role-based nudging adds another layer of relational data on top. Both are the highest technical risks going into build.

---

## Accessibility

- Star ratings and nudge buttons need `aria-labels` so screen readers announce values correctly.
- Role slot status needs a text label alongside colour — open/filled can't be colour only.
- Progress bar needs `aria-valuenow` so the percentage is announced.
- All form fields need explicit labels throughout — placeholder text alone doesn't meet AA standards.

---

## What's Next

For us, Spark felt like the right direction to what the brief was asking for. But putting the full feature list on paper made one thing clear: it was ambitious. Whether all of it was actually buildable with MojoJS, SQLite and HTMX in the time we had was a question we hadn't fully answered yet. That's what the next post gets into.