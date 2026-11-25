# Product@GT x Google Skills: Launchpad

A community feature proposal for Google Skills: pairing learners with verified
industry mentors and roadmap-matched peer pods, using data Google Skills
already has and no other platform can see.

This repo documents the problem, the evidence for it, the design, and what is
still unproven.

## The problem

Google Skills (and the rest of our team's work) can teach a skill and track
progress toward a career goal. It cannot yet help a learner turn that progress
into something they can say out loud in an interview. In a survey of 70
Georgia Tech students (Oct–Nov 2026), 80% (56 of 70) rated "standing out among
applicants" a significant challenge, and in their own words asked for "a
roadmap based on my current skills and what the employers expect" and "a
concrete outcome I can use on my resume and talk about in an interview."

Full data and quotes: [`research/survey.md`](research/survey.md).

## Why Google Skills, not a forum or Discord

Google already runs a community forum (Google Cloud Community) and ran a
mentorship-adjacent program (Cloud Innovators, closed to new members as of
Feb 2026). Both exist outside Skills. Neither can see what a specific learner
has done.

The argument for building Launchpad into Skills, not next to it: Skills is
building two other capabilities (discovery of a career goal, and a
personalized roadmap toward it) that together produce something a forum
cannot have: a learner's current skill state and exact position on a named
path. A mentor who can see that gives different coaching than a mentor who
sees a username. Hosting the conversation elsewhere strands that context in
both directions: the mentor loses it going in, and the roadmap never learns
whether it led anywhere.

Full landscape review and sourcing: [`research/landscape.md`](research/landscape.md).

## North Star metric

**Weekly Connected Learners**: learners who both advance on their roadmap
and have a human interaction (mentor session or pod activity) tied to that
roadmap in the same week.

The conjunction is deliberate. Booked sessions nobody attends don't count.
Solo progress with no human contact doesn't count. It only moves when
learning and connection happen together, which is the thing that can't exist
off-platform.

**Guardrail:** roadmap completion rate, connected vs. unconnected learners.
If the feature doesn't lift completion, the cost isn't earning its place.

**Lagging, self-reported:** interview and offer outcomes, collected with a
light prompt and always labeled self-reported.

Metric design is unvalidated. See [`decisions/open-questions.md`](decisions/open-questions.md).

## Design

Two canvases, lo-fi then high-fidelity:

- Lo-fi wireframes (Balsamiq style): dashboard entry, join-a-pod flow, pod
  home, mentor booking, community Q&A
- High-fidelity wireframes (Google Skills visual language): mentor directory,
  mentor profile + booking, in-course mentor prompt, mentor dashboard,
  session + feedback, pod space

Screen-by-screen notes and canvas links: [`design/README.md`](design/README.md).

## Status

This is a problem-validation stage, not an approved build. Open questions,
what would falsify the thesis, and what's still missing evidence are tracked
in [`decisions/open-questions.md`](decisions/open-questions.md).
