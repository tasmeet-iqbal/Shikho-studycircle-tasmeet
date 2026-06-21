# StudyCircle: Product Plan

StudyCircle is a social and study layer inside the Shikho app, for classes 9 to 12.

## The problem

Our biggest gap is activation. Many students register but never start a real lesson. The free trial path (a free chapter as the way in) converts to paid several times better than buying directly, but the honest conversion rate is about 7.5 to 8.6 percent once we remove students who were already paying, not the 14.5 percent headline. The paid base is strongest in classes 9 to 12, so that is where we focus.

## The idea

A class-based social layer that gets students learning together and keeps them coming back. It is cooperative, never a leaderboard. It is anonymous, because students are minors, so no names and no photos. It lives inside the existing Shikho app. It is not a new app or a new surface.

## v1 (ships now)

The core is one loop: open the app, see your lesson, do it, come back tomorrow.

- The home screen opens on a single card: the exact course the student was enrolled in, a "5 minutes, start" label, and an honest social line ("10+ classmates studied today"). No catalog, no browse screen.
- One tap goes straight into the free trial lesson. No separate join step before the lesson. This removes the browse maze, which is where new students drop off. The pattern is the same one strong onboarding flows use: one tap to the first real value.
- Joining is implicit. The student becomes part of their class by completing the lesson, not by a separate tap. After the lesson, their progress (days active, lessons done) is saved. The next visit picks up where they left off. That saved state is the persistence the brief asks for.
- The trial lesson and any enrolment prompt come after the student has felt the lesson work, never before. Value first, ask later.
- The first social touchpoint is a notification, a welcome message and a before-class reminder. This reaches students who have not opened the app yet, before the home screen is even relevant.

Why this cut: it puts the first real win one tap away. Saved progress means the second visit is not starting from zero, which is the activation problem in plain terms.

v1 pieces, briefly:
- The lesson-first home card with the honest "studied today" count.
- One-tap entry into the free trial lesson, no intermediate join screen.
- Implicit class membership saved on lesson completion, with progress state persisted.
- Welcome and before-class notifications as the first touchpoint for new students.
- The two events that make activation measurable: lesson_start and lesson_complete.

## v2 (next)

- Notifications as the front door: a welcome, a before-class reminder, and a catch-up nudge for students who miss a lesson. Each one opens straight into the lesson, not the home screen. Why it waits: v2 needs the lesson events from v1 working and trusted before any nudge can be timed or measured.
- An anonymous study buddy. Why it waits: pairing students is a bigger step, and it needs the core loop to prove itself first.
- The trial-to-lesson bridge: show classmates in the free chapter and route every tap into a real lesson before any payment screen. Why it waits: it should ride on real counts and the proven first-lesson loop.

## v3 (later)

- Study rooms with a shared focus timer. Why it waits: more surface, and presence work that has to stay anonymous and never fake.
- A class quiz. Why it waits: more surface, plus real-time reliability and an anti-ranking design.
- A per-chapter AI helper. Why it waits: it deepens study past the first lesson, so it sits behind proving the first lesson first.
- Gentle cooperative streaks. Why it waits: streaks need care so they never shame weaker students, which is safety and design work.

The bigger reason these wait: anything that lets minors see or talk to each other needs consent, safety, and moderation work that v1 deliberately skips.

One scope note on the roadmap. The 2026 roadmap line pairs StudyCircle with a Head-to-Head Quiz. I am keeping them separate on purpose. StudyCircle stays a cooperative class layer, and Head-to-Head Quiz is its own competitive product. The class quiz in v3 above is a together-quiz, not the head-to-head one, so StudyCircle does not absorb a second feature mid-build.

## The calls I made

- Class is the unit. A class is small enough to feel like "your people" and big enough, across the country, to never read as empty.
- Cooperative, not a leaderboard. Rankings push down exactly the students we want to keep: weaker ones and girls. A shared count lifts everyone.
- Anonymous. Students are minors. Counts, never names or photos. This also lets us ship without a consent and moderation system on day one.
- Value before any payment. The student should reach a real lesson and feel it work before we ever mention money. This is the honest way to lift the trial path.
- One solid persistent loop, not many features. A single loop that sticks is something we can actually measure and trust. Features layer on after it proves out.

## How we measure it

First, build the two events: lesson_start and lesson_complete. Activation cannot be measured until these exist.

- Primary metric: first-lesson activation rate for newly registered class 9 to 12 students. Run it as an A/B test, the class-circle version against a plain control.
- Secondary metrics: return rate, and repeat-trial leading to paid, measured at the honest 7.5 to 8.6 percent base, never the inflated 14.5 percent.
- Guard metrics: no fake "online now" counts (counts are past tense and real), no drop for girls or weaker students, and no rise in students turning notifications off.
