---
title: "Blog 3 — Finalising the Idea and Structure"
date: 2026-02-28
author: "Kaashyapi Agarwal"
summary: "How Spark evolved into Folio Hub through simplifying features, narrowing the audience, and structuring the platform."
tags:
  - ux-design
  - design-process
  - information-architecture
---

# BLOG 3 — Finalising the Idea and Structure

## Limitations of Spark

As our group discussions started going into more detail, Spark still felt like the right direction, but the more we mapped it out, the more problems surfaced.

Two things became clear quickly.

### Complexity

The first was complexity.

The Spark Score required tracking:

- Community ratings  
- Nudge counts  
- Recency weighting  

across multiple database tables simultaneously.

As beginners working with MojoJS and SQLite for the first time, we hadn’t written a single route yet and already the data model was becoming unmanageable.

The feature that made Spark feel unique was also the feature most likely to sink the project.

### Audience Problems

The second issue was the audience.

Spark was open to every creative discipline:

- Design  
- Tech  
- Music  
- Writing  
- Film  

That sounded inclusive, but in practice it made every design decision harder.

What does a pitch card look like when it needs to work equally well for a musician and a graphic designer?

The broader the audience became, the vaguer the requirements became. And vague requirements are impossible to build around effectively.

The database structure also became too heavy for us to realistically handle because every field needed to support completely different types of creative work.

---

## Narrowing the Concept

As a group, we made two major decisions together.

### 1. Simplify the Core Journey

We stripped Spark back to its essential flow:

1. Pitch  
2. Apply  
3. Build  
4. Share  

Everything beyond that which added too much complexity got removed.

That meant:

- No Spark Score  
- No nudge weighting  
- No weekly spotlight system  

We decided that a simple star rating system was enough for the prototype.

### 2. Focus the Audience

Instead of designing for *all creatives*, we focused entirely on **designers building portfolio work**.

The platform became targeted toward early-career designers who need real collaborative projects to showcase to employers and clients.

That single decision changed almost every part of the platform.

---

## How the Focus Changed the System

### Tags Became Design-Specific

Instead of broad creative categories, tags became:

- Brand  
- UI/UX  
- Product  
- Editorial  
- Motion  

### Roles Became More Concrete

Roles shifted into specific design positions such as:

- UX Researcher  
- Illustrator  
- Layout Designer  

### Language Became More Focused

The tone of the platform also changed:

- “5 designers have shown interest”  
- “Want in on this project?”  

### Deliverables Became Clearer

Pitch outcomes became tangible design outputs:

- Logo suite  
- Brand guidelines  
- Type system  

At this point, we officially renamed the platform:

# Folio Hub

---

## Sitemap — Seven Pages, Every Cut Justified

*MAP*

Mapping screens before writing any code forced a concrete question:

> What does the platform actually need versus what would simply be convenient to have?

Every page had to justify its existence.

The completion vote and showcase pages were eventually merged into one because confirming a project is finished and sharing it publicly are really part of the same moment, not two separate screens.

The access control column became just as important as the page list itself because it revealed conditional logic that needed to be planned into every route before development even started.

---

## User Flow

*MAP*

Mapping the user flow exposed something the sitemap alone couldn’t show:

Folio Hub contains **two parallel journeys**.

### The Owner Journey

The owner:

- Creates the pitch  
- Manages applications  
- Approves collaborators  
- Oversees the project  

### The Designer Journey

The designer:

- Browses projects  
- Applies for roles  
- Joins a team  
- Collaborates during the build phase  

Both journeys eventually converge during the build process and finish together at the showcase.

Mapping this before development meant we could identify where conditional logic needed to exist before writing a single route.

---

## What’s Next

The flow also made the database requirements visible.

At minimum, the system needs tables for:

- Users  
- Pitches  
- Roles  
- Applications  
- Checklist items  
- Ratings  
- Badges  

The relationships between these tables — especially:

- Applications linking users to pitches  
- Ratings triggering badge logic  

— are where most of the complexity lives.

The next step is mapping all of this properly through:

- ERDs (Entity Relationship Diagrams)  
- DDDs (Data Definition Diagrams)  

before any code gets written.