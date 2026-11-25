# Open questions and what would change our mind

This feature is at the problem-validation stage. The items below are
unresolved, in rough order of how much they could break the thesis.

## 1. Do surveyed students (or Skills' actual target learners) use Google Skills?

Not confirmed. If the n=70 sample isn't on Skills, the "current skills and
roadmap position" context that is the core of the argument doesn't exist for
them yet, and the whole case shifts from "Skills already has this, don't
waste it" to "Skills would need to build this from zero, same as anyone
else."

**Needed:** screen for Skills account / usage in the next research pass.

## 2. Was the mentor-access survey question platform-specific?

The 47% (33/70) figure and its quote ("they could connect me with industry
professionals") answer a need, not a platform preference. If the original
survey prompt didn't name Google Skills, we don't have evidence students want
this *here* specifically, only that they want it *somewhere*.

**Needed:** the exact question wording; re-ask with the platform named if it
wasn't.

## 3. No evidence for forum distrust

We've been treating "students don't trust forums" as a premise. It isn't
sourced. One forum post wanting a Discord is not evidence of prevalence. See
`research/landscape.md`.

**Needed:** read discuss.google.dev directly: are students asking
career/interview questions there, do they get answered, by whom, how fast?
That's a cheaper and more relevant check than searching for generic forum-
trust literature, which wouldn't even answer the right question (this
population, this specific forum).

## 4. Mentor supply and incentive

We're borrowing ADPList's "mentoring helps my own career" incentive model.
ADPList pairs that incentive with a portable, shareable record of impact
(session counts, mentee outcomes). Our mentor-dashboard wireframe mirrors
this with shareable credentials tied to measured roadmap movement
("Roadmap Mover": learners who advance a level after meeting you).

**Unresolved:** whether this incentive is strong enough on its own to
produce a working mentor pool at launch, before the credential has any
external recognition value. Needs to be tested directly with prospective
mentors, not inferred from ADPList's public mentor testimonials.

## 5. The falsifier

Stated falsifier: if students who say they want human connection decline to
book a session when one is one click away, or say they'd rather get it from
someone at their own school, the thesis is wrong and the feature should not
be built as scoped.

**Needed:** test this directly in the 5–8 learner interviews, not as a side
effect of testing the booking flow's usability.

## 6. Hybrid vs. full build

Our current design is already partially hybrid: sessions route to Google
Meet via Calendar invite rather than a native in-Skills chat surface. The
open question is narrower than "build vs. don't"; it's whether the
matching, context, and feedback-loop layer (which only Skills can build) is
sufficient on its own, or whether a native community surface (Q&A, pod chat)
is also needed. Current recommendation (see `design/README.md`) is to defer
or cut the generic Community Q&A screen, since it duplicates Google Cloud
Community with no roadmap-data advantage.

## Next steps, in order

1. Screen the existing survey sample for Skills usage (item 1).
2. Run 5–8 learner interviews testing the falsifier (item 5) before testing
   UI usability.
3. Spend one hour reading discuss.google.dev for career-related threads
   (item 3) instead of searching for generic forum-trust research.
4. Talk to 2–3 prospective mentors about what they'd need to participate
   (item 4), separate from the learner interviews.
