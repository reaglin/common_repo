# Releases — every product, every version

One table per store. **Submitted** = sent for certification (Microsoft) or uploaded to a track (Google Play).
**Approved** = live on the store. **Status** = has the product changed since that submission?

| Status | Means |
|---|---|
| Superseded | an older version; a later one was submitted |
| In certification | submitted, not live yet |
| Live — no changes | the newest live version; nothing committed since it was submitted |
| Live — changed since | the newest live version; work committed since (commits, last date) — the next version has material |
| Prepared, not submitted | a package or version is built and waits for Ron |

— means the date was not recorded. Status checked **2026-11-20** (commits since each submission, `git log`).
Sessions keep this file current (rule in `CLAUDE.md`, "Every Store submission: RELEASES.md").

## Microsoft Store

| Product (repo) | Version | Submitted | Approved | Status |
|---|---|---|---|---|
| **CourseBuilder+** (`PreseMaker`) | 1.x as PreseMaker | — | — | Superseded |
| | 2.0.0 | — | 2026-09-29 | Superseded |
| | 2.0.1 | — | 2026-10-05 | Superseded |
| | 2.0.2 | 2026-10-14 | ~2026-10-15 | Superseded |
| | 2.0.3 | 2026-11-16 | 2026-11-18 | Superseded |
| | 2.0.4 | 2026-11-20 | 2026-11-21 | Live — changed since (to 2026-11-22: 2.1.0 submitted) |
| | 2.1.0 | 2026-11-22 | | In certification (the course family, Send feedback) |
| **Assessment+** (`CIATLE`) | 1.4.0 (CIATLE-FCE) | 2026-09-21 | — | Superseded |
| | 1.5.0 | 2026-09-22 | — | Superseded |
| | 1.6.0 | 2026-09-23 | — | Superseded |
| | 2.0.0 | 2026-10-01 | 2026-10-01 | Live — changed since (11 commits, to 2026-10-31) |
| **Gamify+** (`GamifyPlus`) | 1.0.0 | 2026-09-24 | — | Superseded |
| | 1.1.0 | 2026-09-25 | 2026-09-26 | Live — changed since (20 commits, to 2026-11-02) |
| | 1.2.0 | | | Prepared, not submitted |
| **Author+** (`AuthorPlus`) | 1.0.0 | 2026-11-05 | 2026-11-06 | Superseded |
| | 1.1.0 | — | 2026-11-06 | Superseded |
| | 1.2.0 | — | 2026-11-09 | Live — no changes |
| **Statistle → Statistics+** (`Statistle`) | 1.x | — | — | Superseded |
| | 2.0.0 | | | ❌ uploaded to draft Submission 2 (2026-11-12), never submitted; superseded by 2.1.0 |
| | 2.1.0 | 2026-11-23 | 2026-11-24 | Live — no changes (the first Statistics+ release: the PlusBooks' window, Parts I and III written, Part II in development, Send feedback; WACK PASS 23/24) |
| **SEAGit** (`SeaGit\SEAGit`) | 1.0.5 | — | — | Live — changed since (to 2026-10-31) |
| | 1.0.6 | | | Prepared, not submitted |
| **SMADA** (`SMADA10`) | 1.0.0 | 2026-09-09 | 2026-10-13 | Superseded |
| | 1.1.0 | 2026-10-14 | 2026-10-15 | Live — changed since (63 commits, to 2026-10-31) |
| **TrafficLab+** (`TrafficLabPlus`) | 1.0.0 | 2026-10-10 | 2026-10-10 | Live — changed since (7 commits, to 2026-10-31); 1.1 in development |
| **VideoStories+** (`VideoStoriesPlus`) | 1.0.0 | 2026-10-13 | 2026-10-14 | Live — changed since (5 commits, to 2026-10-31) |
| **Accessibility+** (`AccessibilityPlus`) | 1.0.0 | 2026-10-29 | 2026-10-30 | Superseded |
| | 1.0.1 | — | 2026-10-31 | Superseded |
| | 1.0.2 | — | 2026-11-05 | Superseded |
| | 1.1.0 | 2026-11-22 | 2026-11-22 | Live — no changes |
| **Alignment+** (`AlignmentPlus`) | 1.0.0 | 2026-11-21 | 2026-11-22 | Superseded |
| | 1.1.0 | 2026-11-22 | 2026-11-22 | Live — no changes |
| **BMPFast Plus** (`BMPFast_2`) | 2.0.3 | 2026-10-29 | — | Superseded |
| | 2.0.4 | 2026-11-02 | by 2026-11-12 | Superseded |
| | 2.0.5 | 2026-11-12 | 2026-11-20 | Superseded |
| | 2.0.6 | 2026-11-20 | | In certification |
| **AppliedDatabase+** (`AppliedDatabasePlus`) | 1.0.0 | — | 2026-11-19 | Superseded |
| | 1.1.0 | — | 2026-11-19 | Live — changed since (Part II, the window, Send feedback) |
| | 1.2.0 | 2026-11-24 | | In certification (Part II, the Python and Document labs) |
| **DataStructures+** (`DataStructuresPlus`) | 1.0.0 | 2026-11-19 | | In certification (direct link only) |
| **PLC+** (`PLCPlus`) | 1.0.0 | — | by 2026-11-17 (hidden; public since 2026-11-18) | Live — superseded on approval of 1.1.0 |
| | 1.0.1 | | | ❌ never submitted; superseded by 1.1.0 |
| | 1.1.0 | 2026-11-23 | | In certification (the PlusBooks' window, Send feedback, 1.0.1's features; WACK PASS 23/24) |
| **Tinnitus+** (`TinnitusPlus`) | 1.0.0 | | | Prepared, not submitted |
| **PythonProgramming+** (`PythonPlus`), a new product, 9NNW39ZSGGGN (reserved 2026-11-23 at the PSF's request; plan phase 13) | 1.0.0 |  2026-11-23 | | In certification (public, discoverable, free) |
| Python+ (`PythonPlus`), 9PGZ83LZ3HD1: replaced by PythonProgramming+ | 1.0.0 | 2026-11-22 | | Withdrawn from certification 2026-11-23 (never published); the product deleted by Ron 2026-11-23 |
| **LMS-2-Website** | 1.0.0 | | | In development (phase 5 is the Store) |
| **Retirement+** (`EasyPeasyRetirement`) | 1.0.0 | | | In development |
| **WebDevelopment+** (`WebDevelopmentPlus`), 9NSV6R442B0M | 1.0.0 |  2026-11-23 | | In certification (public, discoverable, free; the whole book) |

## Google Play

As recorded in `.claude\PLAYSTORE.md` (last updated there 2026-08-29); confirm in Play Console.

| Product (repo) | Version (code) | Submitted | Approved | Status |
|---|---|---|---|---|
| **EasyPeasyGPX** | 1.0 (2) | 2026-08-17 | — | Superseded |
| | 1.0 (3) | 2026-08-22 | — | Live? — no changes since 2026-09-17 |
| **NaViViewer** | 1.0 (6) | 2026-08-17 | rollout in progress 2026-08-22 | Live — changed since (5 commits, to 2026-09-17) |
| **PunchMonkey** | 1.22 (22) | — | in Production 2026-08-18 | Live — changed since (to 2026-09-17) |
| | 1.22 (23) / (24) | | | Prepared, not submitted |
| **Any6 Fitness Tracker** (`Any6_FitnessTracker`) | 1.1 (5) | | | Prepared, waiting for production access |
