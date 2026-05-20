---
title: "Blog 2 — Three Ideas, One Direction"
date: 2026-02-09
author: "Kaashyapi Agarwal"
summary: "How three separate concepts evolved into one collaborative platform idea."
tags:
  - design-process
  - collaboration
  - ux-design
---

# BLOG 2 — Three Ideas, One Direction

## Bringing It Together

As a group, we each came in with a separate concept and sat down to figure out which direction made the most sense. The three ideas on the table were my **Project Builder Hub**, Maia’s **Music Collaboration Platform**, and Aditi’s **Indie Game Review Community**.

---

## Each Idea Breakdown

| Idea | Strength | Risk |
|------|-----------|------|
| Project Builder Hub | Strong collaborative structure and community focus | Too broad with no clear identity |
| Music Collaboration Platform | Exciting and creative concept | Technically unrealistic with our stack |
| Indie Game Review Community | Most achievable technically | Too niche for deep community engagement |

### Music Collaboration Platform

The Music Collaboration Platform had the most exciting concept, but the problem was the technical reality. Audio engineering in the browser requires the Web Audio API, which is well beyond our current skill level and outside what our stack realistically supports.

### Project Builder Hub

Project Builder Hub had solid structure and strong community spirit, but it felt too broad and lacked a specific identity to stand out from existing platforms. Without a clearly defined audience, the functional requirements became too vague to build around effectively.

### Indie Game Review Community

The Indie Game Review Community was the most technically achievable, but it felt too niche for meaningful community depth and user testing. The brief asks for a community that *thrives*, and a narrow audience makes that difficult to demonstrate.

None of the ideas felt complete on their own, but each had something worth keeping.

---

## Spark

Rather than picking one idea and dropping the rest, we borrowed the strongest parts from each and combined them into a hub for creatives — a place where people pitch short-term projects, build a real team, and finish something together.

We called it **Spark**.

---

## Core Concept

Spark has four core stages:

1. Pitch an idea  
2. Get rated  
3. Build your team  
4. Create something real  

What makes Spark distinct are three key mechanics.

---

## Score System

Rather than using a simple star average, ideas gather a score based on:

- Community ratings  
- Number of nudges received  
- Recent activity  

Ideas crossing a target score earn **“Hot Idea”** status in the weekly spotlight.

This matters because a static feed gives users no reason to return. The system keeps discovery dynamic and rewards quality and engagement rather than simple popularity.

---

## Role-Based Team Slots

Creators define exactly who they need, such as:

- 1 Designer  
- 1 Developer  
- 1 Writer  

Each slot displays whether it is open or filled, and applicants specify which role they are applying for. The creator can then accept or decline applicants per role.

Once all roles are filled, the project automatically locks into **Build Mode**.

This became a core functional requirement because without defined roles, the collaboration process lacks structure and the build phase cannot meaningfully progress.

---

## Structured Build Phases

Once assembled, teams move through five structured phases:

1. Ideate  
2. Plan  
3. Build  
4. Ship  
5. Reflect  

Each phase includes:

- A shared checklist  
- A live progress bar  

This addresses a major user need: accountability. Without visible progress, the platform risks becoming another space where ideas begin but never get completed.

---

## Scope

### Must-Haves

- Idea pitching with tags and role slots  
- Spark Score system  
- Nudge system  
- Discovery feed  
- Build mode phase tracker  
- Outcome card  
- Completion badge  

### Could-Have Features

- Weekly spotlight feature  
- Advanced feed filtering  
- Emoji reactions on outcomes  

---

## Risks

The Spark Score tracks ratings, nudges, and recency simultaneously, creating significant backend complexity before a single page even loads.

Role-based nudging adds another layer of relational data on top of that.

Both became the highest technical risks heading into development.

---

## Accessibility Considerations

Accessibility became part of the system design from the beginning.

- Star ratings and nudge buttons require `aria-labels` so screen readers announce values correctly  
- Role slot status needs text labels alongside colour indicators because open/filled states cannot rely on colour alone  
- Progress bars require `aria-valuenow` so percentages are announced properly  
- All form fields require explicit labels throughout, as placeholder text alone does not meet WCAG AA standards  

---

## What’s Next

For us, Spark felt like the strongest response to what the brief was asking for.

But once we mapped the full feature list out on paper, one thing became clear: the idea was ambitious.

Whether all of it was actually buildable with MojoJS, SQLite, and HTMX in the time we had was a question we still hadn’t fully answered.

That’s what the next post explores.
