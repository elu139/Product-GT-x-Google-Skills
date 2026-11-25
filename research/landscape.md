# Landscape: what community already exists around Google Skills

## Google's own surfaces

**Google Cloud Community** is a Google-run discussion forum, separate from
Skills. It exists "to ask questions, collaborate on answers, and connect with
peers and Googlers" ([cloud.google.com/communities](https://cloud.google.com/communities)).
Forum profiles link to Google Developer Program profiles, so earned
credentials and reputation can display there programmatically
([developers.googleblog.com](https://developers.googleblog.com/id/introducing-the-google-developer-program)).

This matters for our argument: brand trust and identity verification do not
by themselves distinguish Skills from a feature Google already runs. Both
carry the same logo and the same credential-linking capability. They only
distinguish Skills from Discord or Reddit.

**Google Cloud Innovators**, a community/credits program adjacent to
learning, stopped onboarding new members in February 2026. Existing members
keep their status; new learners are redirected to Google Developer Groups and
other programs ([discuss.google.dev, Feb 2026 announcement](https://discuss.google.dev/t/google-cloud-innovators-membership-updates-learning-credits-more/330318)).
The platform's stated "community" on-ramp is partly closed.

**One forum post** (a single user, not a survey) proposes an official Discord
for "the Google Cloud and Skills Boost communities," arguing forums are good
for documentation and troubleshooting but not casual mentorship
([discuss.google.dev](https://discuss.google.dev/t/doesnt-anyone-feel-the-need-of-an-official-google-cloud-developers-discord-server-or-slack-for-this/381352)).
This is one data point, not evidence of prevalence. It should not be cited as
"students don't trust forums"; we have not established that claim with any
source. See the open item in `survey.md`.

## Google Chat as a hybrid option

Google Chat has an API for building apps that bring external services into
Chat spaces, including interactive cards ([developers.google.com/chat](https://developers.google.com/chat)).
It has no native knowledge of Skills learning state. Any roadmap-aware
context (what a learner is stuck on, their badge history) would have to be
built and pushed in by us either way, the same work required to build
Launchpad into Skills directly.

Conclusion: the progress-aware matching and context layer is work we do
regardless of where the conversation itself happens. Our wireframes already
treat video/chat as hybrid: every session routes to Google Meet with a
Calendar invite rather than building a native chat surface. The open
question is narrower than "build vs. don't": it's whether we also build a
native conversation surface, which our current design avoids.

## ADPList: the closest existing mentorship model

[ADPList](https://adplist.org) is a free mentorship platform, not run by
Google, useful as a reference for mechanics:

- Mentors set a fixed weekly availability window; mentees book into open
  slots ([ADPList mentor criteria](https://intercom.help/adplist-community/en/articles/8544615-adplist-mentor-criteria)).
- Mentor screening requires meaningful industry experience and some
  leadership/management background (minimums vary by source: one page states
  7+ years and 1+ year of leadership experience; another states 5+ years).
- Mentors describe mentoring as helping demonstrate leadership ability for
  their own career growth: "Exhibiting an interest in mentorship shows your
  manager that you are leadership material. I was promoted recently and I
  credit that partially to my involvement with mentorship." ([Medium, UX
  Design Mentorship](https://medium.com/amazing-together/ux-design-mentorship-the-power-of-giving-back-and-growing-together-4310b2db68c8))
- ADPList gives mentors a portable, public record of impact: a mentor
  dashboard and mentee directory, and public profiles stating session counts
  (e.g., "300+ sessions across 25 countries") ([ADPList blog, Impact by
  Design](https://blog.adplist.org/post/impact-by-design); [ADPList100
  mentor profile](https://adplist.org/adplist100/2026/mentor/rendy-aries-fajrin)).

**Implication for Launchpad:** the individual accounts above establish that
the "mentoring helps my own career" motivation is real for some people. They
do not establish how common it is, or that it will transfer to a
Google-Skills-specific mentor pool. The portable record is the part of the
mechanism that must be replicated deliberately. If mentoring on Skills
produces nothing a mentor can show their own manager, the incentive doesn't
come bundled in for free. Our mentor-dashboard wireframe addresses this with
shareable credentials (Verified Mentor, Interview Coach, Roadmap Mover), but
this is a design choice, not yet a validated one.

## Summary of what's actually established vs. assumed

| Claim | Status |
|---|---|
| Google runs a forum and profiles link credentials | Established, sourced above |
| Innovators program closed to new members Feb 2026 | Established, sourced above |
| Students generally distrust forums | **Not established.** No source found. Treat as an open hypothesis to test in interviews, not a premise. |
| Mentoring motivates mentors via career/leadership signaling | Established as a real motivation (ADPList), prevalence unknown |
| A portable mentor record is necessary for supply | Inferred from ADPList's design choices, not independently tested for Skills |
