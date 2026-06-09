---
title: A3 Reflection
date: 2026-06-09
author: Kaashyapi Agarwal
summary: Looking back at what we built, how it performs, where it falls short and what building Folio Hub actually taught me.
tags:
  - reflection
  - performance
  - accessibility
  - folio hub
---

# Reflecting on Folio Hub

Building Folio Hub pushed me to think about web development differently, not just whether something works but why it works the way it does, where it breaks and what I can do better next time.

---

## Evaluation of Performance and Technical Behaviour

To evaluate how Folio Hub actually performs, we ran Lighthouse audits across all the six pages. The performance scores ranged from 96 to 99 across every page, and Best Practices hit a perfect 100 everywhere, which reflects that the app is built on solid technical foundations with no deprecated APIs or security issues.

![Lighthouse Inspections Table](/DECO2017-BLOG/assets/images/lighthouse-inspection.png)

The fastest page was Post a Pitch, scoring 99 with both FCP and LCP at 0.7s. This makes complete sense as it's a static form with no images and no database queries on load. There's almost nothing for the browser to do before the page is ready to use. 

![Post A Pitch Inspection](/DECO2017-BLOG/assets/images/PostAPitch_Lighthouse.jpeg)

My Projects was the slowest at LCP 1.0s, which directly reflects what that page is doing. It runs multiple database queries simultaneously to build the project picker, the applied projects list, and the checklist state. The extra load time is expected given the complexity, but it's the clearest page to optimise if development continues.

![My Projects Inspection](/DECO2017-BLOG/assets/images/MyProjects_Lighthouse.jpeg)

The most consistent weakness across every single page was render-blocking requests sitting between 490 and 530ms. What made this interesting to diagnose was that it appeared on Post a Pitch too a completely static page with no data at all. That ruled out database queries as the cause immediately and pointed straight to the CSS file. The stylesheet grew significantly during development as components were added, reworked, and sometimes cut, leaving dead code the browser still has to fetch on every load. The fix is straightforward to audit and trim the stylesheet. It's the one change that would have the biggest performance impact across the whole app.

The HTMX interactions felt noticeably snappier than anything else like toggling a checklist item and watching the progress bar update live without a page reload is exactly what that technology is there for.


---

## Evaluation of User Experience and Accessibility

Accessibility was something we thought about from the start rather than working on at the end, and the Lighthouse scores reflect that — most pages scored between 94 and 96.

The most specific finding was on the Profile page, which scored 90 the lowest of all pages. As It is the only page in the app that uses JavaScript-driven tab switching and after looking into it, the issue is mostly the `aria-selected` and `aria-controls` aren't being updated dynamically when clicking on a tab. So while the tabs work visually, a screen reader wouldn't reliably announce the active panel. A small update to the `switchTab()` function to update those attributes on every click but it's a good example of how dynamic JavaScript interactions need extra care to stay accessible.


![Profile Inspection](/DECO2017-BLOG/assets/images/Profile_Lighthouse.jpeg)

The other finding was a contrast failure flagged on the Feed and Showcase pages. The muted secondary text colour we used (`#9b9189` against `#f5f2ed`) falls just below the WCAG AA 4.5:1 ratio. This was a deliberate design decision as the muted tone is intentional for things like usernames and interest counts, to keep the visual hierarchy clean but we could fix by just darkening that colour by around 10% and it would pass AA without visibly breaking the palette.

![Feed Inspection](/DECO2017-BLOG/assets/images/Feed_Lighthouse.jpeg)

![Showcase Inspection](/DECO2017-BLOG/assets/images/Showcase_Lighthouse.jpeg)


The foundational stuff worked well like every form input across the app has a matching `<label for="">`, all images have descriptive alt text, the checklist progress bar uses `role="progressbar"` with `aria-valuenow`, `aria-valuemin` and `aria-valuemax`, and the interest counter on the pitch details page uses `aria-live="polite"` so changes are announced without interrupting the user. These decisions were taken together during the development and they paid off.

![Applicants Inspection](/DECO2017-BLOG/assets/images/Applicants_Lighthouse.jpeg)

---

## Critical Reflection and Improvement Planning

We definitely underestimated the complexity in this project that came from supporting multiple users with different roles at the same time. The original plan was a simple flow where one person posts a pitch, others apply, the owner manages it. Once we started building it out, it became clear that collaborators needed their own view of the checklist, their own project picker, and their own restrictions on who could publish to showcase. All of it wasn’t in the initial scope but each addition was the right call but it made the My Projects page go through several complete rewrites before it felt right.

The most frustrating bug we hit was the image upload. Spent a significant amount of time on it before figuring out the root cause in MojoJS, `saveFile()` has to be called before `ctx.params()` in the request lifecycle. Calling them in the wrong order silently dropped the file data before it could be saved. Once we understood why it was happening, the fix was literally one line, but getting there took hours. If I were doing this again I'd write a small test for the file upload flow right at the start.

The schema setup gap was another one that caused real friction, fresh installs broke consistently because `schema.sql` wasn't being run automatically, and the error shown was a raw SQLite stack trace rather than anything helpful. We fixed it by updating the README with explicit setup steps, but the better solution would have been the app running its own migrations on startup.

With more time, the three things I'd prioritise are image compression since images are currently served at full resolution which would be a real problem at scale, a notification system so accepted applicants don't have to manually check their status and properly designing the badge feature before attempting to build it.


---

## Retrospective Assessment of Functional Requirements

Looking back at what we originally planned versus what actually shipped, the core feature loop came through intact. Pitch posting, applying to projects, accepting and declining applicants, checklist progress tracking, image uploads, showcase with star ratings, and session-based authentication all of it worked well in the end. For a prototype built under time pressure that's a reasonable outcome and I'm glad the fundamentals held.

What the original requirements genuinely didn't account for was the depth of the multi-user flow. The planning assumed a fairly simple owner-centric view but in practice that turned out to be a significant underestimate. Almost every page needed to behave differently depending on whether you were the owner, an accepted collaborator, a pending applicant, or just browsing. The applicants page, the checklist, and the showcase all required branching logic that wasn't in the original plan. Each addition was the right decision, but looking back the requirements should have mapped out the full user matrix from the start rather than discovering it mid-build.

The badge feature was the clearest example of a requirement that wasn't ready to be a requirement. It appeared in the planning because it sounded like a good community mechanic, awarding designers recognition based on project completions and ratings but the logic for how badges would actually be calculated, awarded, and displayed was never properly designed. It got cut not because we ran out of time to build it, but because we didn't know what we were building. Retrospectively it should have been marked as a stretch goal from day one, which would have freed up time and mental energy for things that were actually defined. 

Folio Hub isn't perfect but it works, and building it taught me more about scoping, debugging and just making decisions under pressure than any brief ever could.

