# Design

Visual system: [`design-system.md`](design-system.md) documents the exact
color tokens, spacing, radii, typography, and components used to build the
high-fidelity screens below, so another team can match the look when
building a different Skills feature.

Two canvases. Neither has been opened/rendered by Claude after generation,
check for clipped text or crowded layouts before presenting.

## Lo-fi wireframes (Balsamiq style)

https://claude.ai/artifact/EAhkcdZRHdrnDpCsbw1gdi

Matches the Google Skills shell (top bar, left nav) in a hand-drawn wireframe
style. Five screens:

1. Dashboard with Launchpad entry
2. Join a pod (role, year, availability form)
3. My pod home (featured screen: weekly mock interview, goals, shared
   resources, "how I got my offer" stories, session rating)
4. Mentor sessions (browse + book)
5. Community Q&A

## High-fidelity wireframes (Google Skills visual language)

https://claude.ai/artifact/8zHpJmCc4bAYo5Vr3QvDi3

Full Material-style treatment matching the actual Google Skills UI
(screenshots provided separately). Six screens, linked so Play walks the
learner flow:

1. **Mentor directory**: verified mentors with ratings, review counts,
   topic tags, next availability. Sorted by relevance to the viewer's
   roadmap; each card shows how many learners on the same roadmap the mentor
   has already coached.
2. **Mentor profile + booking**: rating breakdown, reviews, slot picker. A
   panel above the confirm button shows exactly what the mentor will see
   (goal, roadmap %, badges, the module the learner is stuck on), with an
   explicit, togglable consent control.
3. **In-course mentor prompt**: a learner stalled inside a specific course
   module sees mentors who finished that exact path, with roadmap context
   pre-attached to the booking request. This is the platform-unique moment:
   no forum or external chat can offer help at this instant with this
   context. Was not in the original feature list; added because it's the
   highest-leverage screen for testing the exigence.
4. **Mentor dashboard**: mentee list with roadmap progress and recent
   change, not just session count. Shareable mentor credentials (Verified
   Mentor, Interview Coach, 50 Sessions, Roadmap Mover) tied to measured
   learner movement rather than self-reported activity.
5. **Session + feedback**: what the mentor sees going in (roadmap state,
   recent activity, what the learner explicitly asked for) and structured
   feedback going out, which updates the learner's roadmap and flags skill
   areas. This is the other missing piece: it closes the loop back to the
   discovery and personalized-roadmap sub-teams. Was not in the original
   feature list.
6. **Pod space**: peers matched by roadmap position (not just role/year),
   weekly Meet session, rotating mock-interview pairing, shared activity
   feed, escalation path to a mentor when the pod stalls as a group.

## What's platform-unique vs. generic

Ranked by how much each depends on data only Google Skills has:

| Feature | Depends on Skills data? | Status |
|---|---|---|
| Mentor session with roadmap context (screens 2-3, 5) | Fully; cannot exist on a forum or generic chat | Candidate for MVP |
| Peer pod matched on roadmap position (screen 6) | Fully; requires knowing where every learner is, this week | Candidate for MVP or R2 |
| Community Q&A (lo-fi screen 5) | Barely; duplicates Google Cloud Community's existing forum | Candidate to defer or cut |

If a screen would work identically with the learning data stripped out, it's
not an argument for building inside Skills specifically.
