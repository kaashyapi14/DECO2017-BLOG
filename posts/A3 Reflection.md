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

## Performance and Technical Behaviour

To evaluate how Folio Hub actually performs, we ran Lighthouse audits across all six pages. Scores ranged from 96 to 99 and Best Practices hit a perfect 100 everywhere, reflecting that the app is built on solid technical foundations with no deprecated APIs or security issues.

![Lighthouse Inspections Table](/DECO2017-BLOG/assets/images/Lighthouse.png)

The variation between pages made sense once I thought about what each one is actually doing. Post a Pitch was the fastest, scoring 99 with both FCP and LCP at 0.7s as it's a static form with no images and no database queries on load. 

![Post A Pitch Inspection](/DECO2017-BLOG/assets/images/PostAPitch_Lighthouse.jpeg)

My Projects was the slowest at LCP 1.0s, which directly reflects the multiple database queries it runs simultaneously to build the project picker, applied projects list, and checklist state. The extra load time is expected given the complexity, but it's the clearest page to optimise if development continues.

![My Projects Inspection](/DECO2017-BLOG/assets/images/MyProjects_Lighthouse.jpeg)

The most consistent weakness across every page was render-blocking requests sitting between 490 and 530ms. What made this worth investigating was that it appeared on Post a Pitch too which is a completely static page. That ruled out database queries immediately and pointed to the CSS file. The stylesheet grew significantly during development as components were added, reworked, and sometimes cut, leaving dead code the browser still fetches on every load. Auditing and trimming the stylesheet would be the single highest-impact fix across the whole app.

The HTMX interactions felt noticeably responsive like toggling a checklist item and watching the progress bar update live without a page reload is exactly what that technology is there for.


---

## User Experience and Accessibility (LightHouse and WAVE)

![WAVE](/DECO2017-BLOG/assets/images/WAVE.png)

Accessibility was something we approached from the start rather than working on at the end, and the Lighthouse scores reflect that most pages scored between 94 and 96. The foundational work held up well, every form input has a matching `<label for="">`, all images have descriptive alt text, the progress bar uses `role="progressbar"` with the correct ARIA attributes, and the interest counter uses `aria-live="polite"`.

![Profile Inspection](/DECO2017-BLOG/assets/images/Profile_Lighthouse.jpeg)

The lowest score was the Profile page at 90, the only page using JavaScript-driven tab switching. After looking into it, `aria-selected`and `aria-controls` aren't being updated dynamically when a tab is clicked therefore a small update to `switchTab()` would fix it. It's a good reminder that dynamic interactions need extra care to stay accessible.

![Feed Inspection](/DECO2017-BLOG/assets/images/Feed_Lighthouse.jpeg)

![Showcase Inspection](/DECO2017-BLOG/assets/images/Showcase_Lighthouse.jpeg)

The contrast failure on the Feed and Showcase pages was a deliberate trade-off. The muted secondary colour (`#9b9189` against `#f5f2ed`) falls just below the WCAG AA 4.5:1 ratio, which was intentional for keeping the visual hierarchy clean. Darkening it by around 10% would pass AA without visibly breaking the palette.

The bigger gaps only became visible through testing with multiple accounts. The collaborator experience was completely unaccounted for a collaborator would see the exact same controls as the owner, including the publish button. Threading an `isOwner` flag through the relevant controllers and templates wasn't in the original plan but was the right call. 

![Applicants Inspection](/DECO2017-BLOG/assets/images/Applicants_Lighthouse.jpeg)

The apply button also had no feedback after clicking, so a teammate assumed it hadn't worked. We fixed that with an HTMX state change swapping it for an "Interest sent" confirmation. The My Projects page was rethought entirely it originally just listed projects you owned, duplicating the profile page. Changing it to show everything you own, collaborate on, and have applied to made it actually worth using.

Full keyboard navigation is the one gap that didn't get addressed and would be the first thing I'd prioritise if development continued.



---

## Critical Reflection and Improvement Planning

We definitely underestimated how complex supporting multiple user roles would get. The original plan was one simple flow: one posts a pitch, others apply, the owner manages it. Once we started building, it became clear that collaborators needed their own checklist view, project picker, and publishing restrictions, and the My Projects page went through several rewrites before it felt right.


The most frustrating bug was the image upload. The root cause was a MojoJS constraint `saveFile()`and `ctx.params()`both consume the HTTP request body, so calling them in the wrong order silently dropped either the file or the form data with no error shown, just the form infinitely loading. Our tutor pointed us toward the demo controller where `saveFile()` is called first and after understandingnwhy the ordering mattered, the fix was a single line. Getting there still took hours, and if I were doing this again I'd write a test for the file upload flow right at the start.


The schema setup was source of friction, fresh installs broke consistently because `schema.sql` wasn't being run automatically and the app would crash because the user table was auto-created but everything else wasn't. We fixed it by updating the README with explicit setup steps, but the better solution would have been the app running its own migrations on startup.

With more time, the three things I'd prioritise are image compression since images are currently served at full resolution which would be a real problem at scale, a notification system so accepted applicants don't have to manually check their status, and properly designing the badge feature before attempting to build it. This project also gave me a hands-on understanding of things I'd only read about before session management, encrypted cookies in MojoJS, how user data flows and is protected server-side. That kind of practical experience is something no amount of reading could have given me.


---

## Retrospective Assessment of Functional Requirements

Looking back at what we planned versus what shipped, the core loop came through: pitch posting, applying to projects, accepting and declining applicants, checklist progress tracking, image uploads, showcase with star ratings and session-based authentication. For a prototype built under time pressure, I'm glad all the fundamentals were held.

What the original requirements didn't account for was the depth of the multi-user flow. The planning assumed a fairly simple owner-centric view, but almost every page ended up needing to behave differently depending on whether you were the owner, a collaborator, a pending applicant or if you're just browsing. The branching logic across the checklist, applicants page, and showcase was not in the original plan but i feel like each addition was the right call although the requirements should have mapped out the full user matrix from the start rather than discovering it mid-build.

The badge feature is the clearest example of a requirement that wasn't ready to be one. The idea was to award designers recognition based on showcase ratings `has_badge`  even appears in our DDD table but the schema was never updated to support it. Adding a badge table and a `user_achievement`  table mid-development would have meant redesigning the ERD entirely with no time left to test. It got cut not just because we ran out of time, but because we hadn't properly designed what we were building. It should have been a stretch goal from day one also keepig in mind that the features driven by derived logic need to be planned from the start, not added later.

