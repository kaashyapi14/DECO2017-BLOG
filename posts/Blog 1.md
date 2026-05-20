---
title: "Blog 1"
date: 2026-05-03
author: "Kaashyapi Agarwal"
summary: "Breaking down the BlaBla Corp brief and exploring early platform concepts."
tags:
  - ux-design
  - design-process
  - ideation
  - community-platforms
---

# From Brief to One Idea

> Exploring how the initial brief evolved into a collaborative platform concept.

---

## Breaking Down the Brief

We're building for **BlaBla Corp**, a fictional social media company designed around the idea of *community* — not just a place to post content, but somewhere people genuinely want to spend time.

The brief talks about **“effortless sharing”** and **“tailor made experiences”**, which pushed me to think deeper about what actually creates meaningful communities online.

> What gives a community its identity?  
> What makes someone return instead of scrolling once and leaving?

Those questions sat behind every decision I made throughout the ideation process.

---

## Understanding the Core of the Brief

According to the brief, the foundation of the platform is:

- The **right information**
- The **right experience**

Meaning not only *what* people share, but also *how* it feels to participate in the space.

One detail that immediately shaped the direction of the project — and honestly felt like a relief — was that there was **no authentication system to design**.

> [!TIP]
> BlaBla Corp handles authentication centrally, meaning every user entering the platform is already verified.

That removed an entire layer of complexity and allowed the focus to stay entirely on the community experience itself.

---

## Technical Constraints

The technical stack was already defined:

| Technology | Purpose |
|---|---|
| **MojoJS** | Routes and server logic |
| **SQLite** | Database storage |
| **HTMX** | Frontend interactions without full page reloads |

We could build on top of the stack, but we couldn't replace any part of it.

---

## Non-Negotiables

Beyond the technical setup, there were several requirements that every solution had to meet.

| Requirement | Importance |
|---|---|
| Accessibility support | Essential |
| Keyboard navigation | Required |
| Responsive layouts | Required |
| Semantic structure | Required |

> [!IMPORTANT]
> These weren’t suggestions — they were the minimum standard for every project. A strong idea that ignored any one of them failed the brief entirely.

---

# Initial Ideation

`Research`  
`Ideation`  
`Community Thinking`

Reading the brief for the first time, my instinct was to build something for the creative communities I’m personally part of.

People in these spaces are often searching for a place to genuinely connect and create together, not just consume content passively.

That became the direction behind every concept I explored.

I narrowed the possibilities into two main ideas.

---

# Idea 1 — Creative Challenge Hub

A platform where weekly creative challenges are posted across different disciplines such as:

- Design  
- Writing  
- Photography  
- Illustration  
- Music  

Users submit their interpretation of the challenge and the community votes on the strongest execution.

A new prompt appears every week, open to everyone.

---

## Strength

The challenge structure creates a natural content cycle and gives creatives a reason to continually return to the platform.

The voting system also creates engagement around shared work and encourages participation across multiple creative disciplines.

---

## Risk

> [!WARNING]
> Without clear criteria, voting risks becoming a popularity contest rather than a quality filter.

Another major issue was longevity.

Submissions would live and die within a single week, meaning nothing lasting actually gets built collaboratively.

---

## Accessibility Considerations

Accessibility requirements included:

- Full keyboard navigation for uploads and voting
- Descriptive alt text for all image submissions
- Semantic form structures

---

# Idea 2 — Project Builder Hub

A platform where people don’t just discuss ideas but actually turn them into real collaborative projects.

Users could:

- Pitch ideas
- Find collaborators
- Build together through a shared structure
- Publish the final outcome once complete

---

## Strength

This idea solved the major gap left by the Creative Challenge Hub.

> People don’t just want to participate.  
> They want to create something meaningful together.

The platform created a pathway for users to not only collaborate, but also produce tangible work they could publicly showcase.

---

## Risk

> [!WARNING]
> The concept risked becoming too broad — essentially Trello, LinkedIn, and Reddit combined into one platform.

The core direction felt strong, but the scope required serious simplification before it could realistically be built.

---

## Accessibility Considerations

Key accessibility requirements included:

- Keyboard support across all interactions
- Explicit form labels throughout the platform
- Clear navigation hierarchy

---

# Reflection

Project Builder Hub ultimately felt like the stronger concept because it answered something the Creative Challenge Hub couldn’t.

> What happens after the challenge ends?

Nothing gets built together.  
No lasting output exists.  
No team forms.

Project Builder Hub closed that gap by giving people a structure to actually finish something collaboratively and share it with the world.

---

## Next Step

At this stage, the concept still felt broad, but the collaborative direction felt much more aligned with what the brief was truly asking for.

The next challenge became figuring out:

> How could this idea become more focused, achievable, and technically realistic?
```
