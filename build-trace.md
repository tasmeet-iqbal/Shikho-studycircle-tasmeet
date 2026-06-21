# StudyCircle: build trace

## How I built it
I built the v1 prototype with an AI coding partner, iterating in plain single-file HTML and CSS so the whole thing runs from one file with no build step. I grounded it in the real Shikho app: I reproduced the actual home screen (top bar, trial banner, routine, stories, program, mentors, Shikho AI, support) from the screens I saw during the week, then added the StudyCircle layer on top, so it feels native and not like a generic wireframe. State is saved in the browser with localStorage, so a connection and progress survive a reload.

This document is the decision log. The GitHub repo history at deploy time is the version trail, and a short Loom walkthrough can sit on top of it.

## The decisions I made, and why
- Go after activation. The biggest headroom is students who register and never start a first lesson. Everything in v1 points at getting a new student into one real lesson.
- Class is the social unit. Classes 9 to 12 are most of the paid base, and a class is small enough to feel personal and big enough to never look empty. The team had already filed "class is the obvious social unit" and "presence beats a vanity leaderboard."
- Cooperative, never a leaderboard. Every count is collective or about your own progress. No ranks, no "you are last." Ranking pushes down exactly the weaker students and girls you most want to keep.
- Value before payment. The free chapter is a real lesson you reach in one tap, and the trial and enrol prompts sit after the value, never in front of it.
- Anonymous, and this is my call, not a brief requirement. The brief never mentions minors or safety. I chose anonymous (counts, not names) because these are minors and it lets us ship without a moderation system. I flag it as a judgment call, not a stated rule.
- No open group chat, in any version. An open chat among minors is the highest-risk, highest-moderation-cost surface, and it drives hanging out, not studying. The community feeling comes from belonging (your class is here, you got counted), not conversation.
- First lesson over join-first. My early v1 made the student join a circle before studying, which puts a step in front of the win. After looking at how strong onboarding flows work (Canva, Notion, Loom, Brilliant: kill the blank page, one tap to the first real win, value first), I flipped it. The home now opens on a "your first class is ready, 5 minutes, start" card that goes straight into the lesson, with the social proof ("10+ classmates studied today") riding on it. The trial banner moved below.
- Notifications belong in v1. The disengaged student is not in the app, so the notification is the first touchpoint, the door. The real Shikho notification today is generic (time and class) and gets ignored. The StudyCircle version is social and personal, so it actually pulls.
- Defined failure and empty states. The week's biggest design lesson was that an undefined "failed to load, retry" state is what shipped a white screen, and that defining states is the PM's job. So the lesson has a defined loading state and a calm broken-load recovery (auto-retry, a retry button, never blank, never "log out"), and the profile has a real empty state before any progress.
- One solid persistent loop, not a pile. v1 is join-by-doing, first lesson, get counted, come back. The richer social mechanics (rooms, buddy, quiz, streaks) are sequenced into v2 and v3, behind proving v1 first.
- Head-to-Head Quiz stays separate. The roadmap pairs it with StudyCircle, but it is its own competitive product, so I did not absorb it.

## How it evolved
- Started with a class-presence layer added onto the real home (counts, a pulse strip).
- Built v2 and v3 concept prototypes (notifications, trial bridge, study rooms, buddy, quiz, AI helper).
- Cut a separate AI study buddy, since Shikho already has Shikho AI, and dropped a guardian consent gate (too much friction, low guardian uptake), keeping the social layer fully anonymous.
- Held streaks for proper later design so they never shame anyone.
- Tightened all copy to be plain and human, removed any fake "live" framing, and used SVG icons with no emoji.
- Did the white-screen incident work during the week (root cause and a retry-state spec), then reused that spec to define the prototype's failure states.
- Reframed v1 from "join a circle first" to "first lesson first" after the onboarding research, and moved the first notification into v1.
- Audited the whole build against the simulation's stated must-haves and closed the gaps (defined states, brand exactness, this trace).

## What is in the submission
- The working v1 prototype: `prototype/studycircle-v1.html` (clickable, persistent, off-script safe, grounded in the real Shikho UI).
- The v1, v2, v3 plan: `deliverables/studycircle-plan.md`.
- This build trace, plus the repo history at deploy.
