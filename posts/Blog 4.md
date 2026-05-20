---
title: Blog 4 — Wireframes and Design Decisions
date: 2026-05-13
author: Kaashyapi Agarwal
summary: Walking through every wireframed page and the design decisions behind each one.
tags:
  - wireframes
  - design decisions
  - folio hub
---

# Blog 4 — Wireframes and Design Decisions

---

Rather than wireframing as a group from the start, we each made our own version of every page independently. The idea was that working separately first would surface different approaches — and then once we had three individual versions we came together, compared them and picked the elements that worked best from each. The wireframes shown here are mine.

---

## Page by Page

---

### Page 1 — Home / Feed

<figure>
  <img src="../assets/images/wireframe 1.png" alt="Wireframe of the home feed page" width="700">
  <figcaption>Home / Feed — the card component is reused across showcase and profile</figcaption>
</figure>

This was the first page we tackled as it was the most important one, where the card component gets reused across the showcase and profile. The card shows the title, description, role tags and interest counter. Description is written in two lines — if everything shows on the card there's no reason to click through. The filter tags at the top let designers narrow by discipline without a full page reload.

---

### Page 2 — Post a Pitch

<figure>
  <img src="../assets/images/wireframe 2.png" alt="Wireframe of the post a pitch form" width="700">
  <figcaption>Post a Pitch — three role fields and a deadline dropdown keep submissions structured</figcaption>
</figure>

The form is very simple: title, description, discipline tags, roles needed and project length. The title is the first thing someone sees on the feed so it needs its own dedicated space rather than being buried in the description. Three separate role fields allows the owner to be very specific about who they actually need. The project length dropdown sets a real deadline upfront because open-ended timelines are exactly how projects stall.

---

### Page 3 — Pitch Detail

<figure>
  <img src="../assets/images/wireframe 3.png" alt="Wireframe of the pitch detail page" width="700">
  <figcaption>Pitch Detail — two states depending on whether you're the owner or a designer</figcaption>
</figure>

This page has two jobs depending on who's viewing it — a designer sees "Want in?" and the owner sees "Manage Applicants." Both states needed wireframing before thinking about the route logic. The deliverables section listing actual outputs was important to include as most platforms list roles but never say what actually gets made. Showing deliverables upfront sets expectations for collaborators.

---

### Page 4 — Manage Applicants

<figure>
  <img src="../assets/images/wireframe 4.png" alt="Wireframe of the manage applicants page" width="700">
  <figcaption>Manage Applicants — spot counter and disabled state prevent accidental over-accepting</figcaption>
</figure>

This is for owners only. I made a simple list showing each applicant's name, role and accept/decline buttons. Wireframing this page surfaced something we hadn't considered — what happens when the team is full? We needed a clear disabled state so the owner couldn't accidentally accept a fourth person, hence the spot counter ("1 of 3 spots filled"). The "Lock team and start project" button sits at the bottom and the badge tags help the owner make quicker decisions about who to accept without needing to dig deeper.

---

### Page 5 — Build Checklist

<figure>
  <img src="../assets/images/wireframe 5.png" alt="Wireframe of the build checklist page" width="700">
  <figcaption>Build Checklist — progress bar and completion confirmation on one page</figcaption>
</figure>

The most complex page to wireframe. The progress bar and completion confirmation live on the same page — splitting them felt unnecessary. Each step has a status tag (**Completed, In Progress, Upcoming**) so the whole team knows where things stand without asking. All members confirming before sharing was important because it stops one person from pushing a project live before everyone's ready.

---

### Page 6 — Showcase

<figure>
  <img src="../assets/images/wireframe 6.png" alt="Wireframe of the showcase page" width="700">
  <figcaption>Showcase — ratings and comments open on the same page, no navigation away</figcaption>
</figure>

The same card component from the feed is reused here deliberately for consistency. The expanded project view opens on the same page showing star ratings, a comment box and a submit review button — because community members shouldn't have to navigate away just to leave a rating.

---

### Page 7 — My Profile

<figure>
  <img src="../assets/images/wireframe 7.png" alt="Wireframe of the profile page" width="700">
  <figcaption>My Profile — badge shown prominently, three tabs pulling from different database queries</figcaption>
</figure>

The profile shows the username and badge prominently at the top — for students and graduates, it is the most meaningful signal on the page. Three tabs (**My Pitches, Projects I Joined, Showcased Works**) below pull from different database queries. The status tags (**Concept, Active, Archived**) give a quick snapshot of where each project sits without clicking in.

---

## What's Next

The best elements were agreed on as a group, shifting the focus to the data. The next post covers identifying how each feature maps to the current stack, defining the database tables, and building the ERD and DDDs before any routes are written.