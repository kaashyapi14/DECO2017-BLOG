---
title: Blog 1 
date: 2026-05-13
author: Kaashyapi Agarwal
summary: Breaking down the BlaBla Corp brief and narrowing down to one concept worth building.
tags:
  - brief
  - ideation
  - process
---

# From Brief to One Idea

---

## Breaking Down the Brief

We're building for **BlaBla Corp**, which is a fictional social media company. It describes itself as a platform built around "community" and not just a place to post things, but somewhere people genuinely want to spend time. The brief talks about "effortless sharing" and "tailor made" experiences, which pushed me to think about what actually makes that happen. What gives a community its identity? What makes someone come back rather than just scroll through once and leave? Those were the questions sitting behind every decision I made when thinking about my idea.

The core of everything according to the brief is **"the right information"** and **"the right experience"**, meaning what people share and how it feels to be part of it.

Something that shapes the design from the start and was honestly a relief to read is that there's no sign-up or login page to build. BlaBla Corp handles authentication centrally, so every person landing on the hub is already a verified user. That removes a whole layer of complexity and keeps the focus on the community itself.

The tech stack is also set: **MojoJS** handles routes and server logic, **SQLite** stores the data, and **HTMX** manages frontend interactions without full page reloads. We can build on it but can't replace any part of it.

On top of these there are some non-negotiables in this project:

![Non-negotiables from the brief](/DECO2017-BLOG/assets/images/Blog-1-non-negotiables-table.png)

*Fig. 1 — The non-negotiables — minimum standards every site must meet*

These aren't just suggestions, they are the minimum standards for all our sites — a great idea that misses any one of them fails the brief.

---

## My Initial Ideas

Reading the brief for the first time, my instinct was to build something for the creative communities I'm personally part of. People in these spaces are looking for a real place to connect and create together. That became the direction for every idea I considered. I explored two different ideas.

---

### Idea 1 — Creative Challenge Hub

A community where weekly creative challenges are posted across different disciplines (design, writing, photography, illustration, music). Everyone submits their take and the community votes on the best execution. A new prompt every week, open to everyone.

**Strength:** Gives creatives across different fields a reason to keep coming back. The challenge format creates a natural content cycle and the voting mechanic builds genuine engagement around shared work.

**Risk:** Voting without clear criteria becomes a popularity contest rather than a quality filter. It also produces no lasting output — submissions live and die within the week and nothing gets built together.

**Accessibility:** Submission uploads and voting interactions need full keyboard support and all images need descriptive alt text.

---

### Idea 2 — Project Builder Hub

A community where people don't just talk about ideas but actually turn them into real projects — pitch an idea, find collaborators, work through it together with a shared structure, and post the result when done.

**Strength:** Solves the gap the first idea reveals — people want to create together, not just attend things. This gives them a way to actually build something and show it to the world.

**Risk:** Trying to do too much at once — essentially Trello, LinkedIn and Reddit built all in one. The core concept was solid but the scope needed serious cutting down.

**Accessibility:** All interactive elements need keyboard support and fields need explicit labels throughout.

---

## Why Project Builder Hub?

Project Builder Hub felt like the stronger pitch to me because it answered something the Creative Challenge Hub couldn't. What happens after the challenge ends? Nothing gets built together, no lasting output, no team. Project Builder Hub closes that gap by giving people a structure to actually finish something collaborative and show it to the world.