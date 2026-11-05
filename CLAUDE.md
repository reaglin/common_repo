# CLAUDE.md — Ron Eaglin's app portfolio (shared guidance)

This file is loaded for any session started in `C:\Users\ronal\source\repos\` **or any repo
beneath it** (Claude Code reads CLAUDE.md from every parent directory). Each app repo has its
own `CLAUDE.md` with project specifics; this one carries what is common across them.
Start a session here when the work spans more than one app.

## Android / Google Play apps (.NET MAUI)

| Repo | ApplicationId | Play status | Notes |
|---|---|---|---|
| `Any6_FitnessTracker\` | `com.roneaglin.any6_fitnesstracker` | closed testing done; production access requested 2026-08-19 | csproj is nested: `Any6_FitnessTracker\Any6_FitnessTracker\` |
| `EasyPeasyGPX\` | `com.eaglin.easypeasygpx` | 1.0 (3) API-36 build uploaded to Production 2026-08-22 | its `RELEASE.md` is the template for the others |
| `NaViViewer\` | `com.eaglin.naviviewer` | 1.0 (6) submitted to Production | |
| `PunchMonkey\` | `com.eaglin.punchmonkey` (+ `.designer`) | 1.22 (22) built, upload pending | two apps over one core; server is `PunchMonkeyServer\` |
| `AppOpenerAndTimer\` | `com.eaglin.appopenerandtimer` | in development (net9.0, not yet on Play) | |

Non-Play repos here: `PunchMonkeyServer` (Blazor server + privacy-policy pages for all apps),
`CIATLE*`, `PreseMaker`, `SeaGit`, `ValidationCodeManager`, `WindowsFormManager`, `reaglin`.

## Desktop / Microsoft Store

- **`SMADA10\`** — SMADA (Stormwater Management and Design Aid), a WPF/.NET 10 rebuild of the
  hydrology package that accompanies *Hydrology: Water Quantity and Quality Control*. Free
  software, intended for the Microsoft Store, supporting Ron's paid products. Phases 0-5 of
  `docs/DEVELOPMENT-PLAN.md` are complete as of 2026-09-03. On the Microsoft Store
  (https://apps.microsoft.com/detail/9nntz8389wtk): 1.0.0 live 2026-10-13 (tag `v1.0.0`), **1.1.0 live
  2026-10-15** (tag `v1.1.0`; Weir calculator, Regression rebuilt, Flow/Statistics drop-downs;
  privacy now `https://softwareplus.ai/smada/privacy/`).
  **Start with that repo's `CLAUDE.md` and `docs/DEVELOPMENT-PLAN.md`.** Hand-test build lives
  in `SMADA10\manual-test\SMADA.exe` (see its `docs/MANUAL-TESTING.md`).
  Shares an approach with `reaglin\BMPTrains` — property metadata via an attribute.
- **`AuthorPlus\`** — AI-enhanced book-authoring tool (chapters in a rich-text editor, characters,
  timeline, plotlines in one tree). WPF/.NET 10, paid Microsoft Store app; repo
  `github.com/reaglin/AuthorPlus`. Scaffolded 2026-09-04 (phase 0 of `docs/DEVELOPMENT-PLAN.md`).
  Book = folder of files under `Documents\AuthorPlus\Books`. **Re-planned 2026-09-12:** tree is
  Book → Sections → Chapters → Items (CIATLE Program Assessment style); Ron's own trilogy
  (*The Book of One*, three parts of DOCX chapters) is the live test case
  (`docs/TRILOGY-TEST-CASE.md`); AI goes through the shared `AiManager` package below, replacing
  its copied `AuthorPlus.AI`. **Start with its `CLAUDE.md`.**
- **`Statistle\`** — statistics calculation and learning app following Ron's EGN3443 course
  (`github.com/reaglin/egn3443`): data tables on the left, analyses on the right, every
  parameter explained with its source, and a **Code tab that writes the Python and R** for the
  data and the analysis. WPF/.NET 10, free Microsoft Store app. **Started 2026-09-08** from a copy
  of SMADA's core (`StatistleObject`, `Analysis`, the generic editor with help panel).
  `docs/PLAN.md`, `docs/DEVELOPMENT-PLAN.md`, `docs/METHODS-AND-SOURCES.md` (every statistic
  with its formula, source, Python and R). **Start with its `CLAUDE.md`.**
- **`LMS-2-Website\`** — turns an **IMS Common Cartridge course export** (`.imscc`) into a static
  **website** and publishes it to **GitHub Pages**: three steps in one window, no AI. The features
  exist inside PreseMaker; this is the straight line through them. WPF/.NET 10, free Microsoft
  Store app. **Started and built to phase 4 on 2026-09-14** — the conversion is verified against a
  real 135 MB Brightspace export of EGN3443 (19 sections → 149 pages in ~1.5 s), 61 tests green.
  The GitHub **token** route has not yet run against GitHub (Ron's hand-test 5); Git-only publish
  is tested against a local repository. Phase 5 is the Store. **Start with its `CLAUDE.md`.**
- **`GamifyPlus\`** — **Gamify+** (name reserved on the Microsoft Store): learning games for a
  class, published as ordinary web pages. A teacher with no technical background picks a game type,
  types the questions, and gets one self-contained HTML page per game plus a course website. A game
  **type** is three shareable files (`gametype.json`, `template.html`, `instructions.md`) — data,
  not code — so a new kind of game can be sent to a colleague or written by the AI. Students type
  their name and hand in a signed result line the app verifies (it shows who took part; it is not
  exam security, and the app says so). WPF/.NET 10, free Store app; AI goes through the shared
  `AiManager` package. Started 2026-09-17; "Course" became **Game File** (games in user-made
  groups, five sections, Play and Versions tabs), fourteen game types, AI draft/revise, and
  GitHub Pages publishing are built. On the Microsoft Store at
  https://apps.microsoft.com/detail/9nt6tccndc1v: 1.0.0 (tagged `v1.0.0`), then **1.1.0 live 2026-09-26** (tagged
  `v1.1.0`) — card games (Pyramath, Fractazmic-Rummy, I See Cards, Klondike), 3D games (Robot
  Golf), import a game and grow it by asking (Revise, Make my own version), Professor Ron; 550 tests
  green (identity `DeanEaglin.Gamify`, WACK PASS 23/24; release docs in `docs/release/`, privacy page
  `https://punchmonkeyserver.com/privacy/gamify`, revised for 1.1). **Start with its `CLAUDE.md`.**
- **`EasyPeasyRetirement\`** — **Retirement+** (renamed 2026-10-10): retirement "what if?" planner (when to retire, when to claim;
  Social Security, pensions, accounts, home, expenses; year-by-year projection with taxes and
  RMDs; scenarios compared side by side). All data local. WPF/.NET 10, Microsoft Store; repo
  `github.com/reaglin/EasyPeasyRetirement` (private). **Plan stage as of 2026-09-05** — no code
  yet; `docs/PLAN.md`, `docs/DEVELOPMENT-PLAN.md`, `docs/RULES-AND-SOURCES.md`. Copies SMADA's
  metadata-on-the-property core rather than referencing it. **Start with its `CLAUDE.md`.**

- **`TrafficLabPlus\`** — **TrafficLab+**: turns a real intersection, or a corridor of up to ~10,
  into a **web page with a live traffic simulation** like Ron's LPGA Traffic Lab artifact (kept in
  `reference/`). Roads from **OpenStreetMap** (not Google — its terms forbid deriving geometry);
  volumes typed, from **FDOT AADT**, or estimated by the AI (shared `AiManager`); the program
  previews the page, publishes to **GitHub Pages**, and students **hand in the link**. Classroom
  game + lab (budget, plan, scored test). The engine stays JavaScript because it runs in the page.
  WPF/.NET 10, free Store app; repo `github.com/reaglin/TrafficLabPlus`. Started 2026-10-09;
  **phases 0–7 built the same day** (engine matches LPGA exactly, one-file page; page opens blank as a
  puzzle, Submit plan → printout, name optional; `.trafficlab` study file, start screen, network editor
  with the page rebuilt beside it, New study with its budget, About; built-in examples LPGA and
  Four-Way; the Map section finds a place, loads its roads from OpenStreetMap and makes a study from
  up to ten chosen intersections; FDOT AADT counts fill a Florida study's volumes, AADT × K × D).
  Publishing decided: one GitHub Pages repo, every study unless marked "Don't publish", a summary
  page as the index. Phase 6 (the AI over AiManager 1.4.1: fill in the network, estimate traffic,
  write the challenge, coach — it only proposes), the icon (a traffic signal on a "+") and the privacy
  policy (live at softwareplus.ai/trafficlab/privacy/) done 2026-10-09. Ron plans the Store submission
  for 2026-10-10. Phase 7 (publish every ticked study to one GitHub Pages repository with a summary
  page) and the Store screenshots (tools/store-shots.ps1) done the same day. Ron's real publish worked
  2026-10-10. **Store package 1.0.0 built 2026-10-10** (identity `DeanEaglin.TrafficLab`, Store ID
  9P5NGQF4HRPD; packaging ported from Gamify+; release docs in `docs/release/`). WACK PASS 23/24;
  **1.0.0 live on the Microsoft Store 2026-10-10** (submitted and approved the same day;
  https://apps.microsoft.com/detail/9p5ngqf4hrpd; tagged `v1.0.0`). Its softwareplus.ai page links to
  the Store and plays two examples; the home page has its tile. **Next version (1.1)**, started
  2026-10-10: every page it makes has a footer, "Created with TrafficLab+ · SoftwarePlus.ai", both
  linked (Ron; plan 9.1, ✅ Ron 2026-10-10). **Start with its `CLAUDE.md`.**

- **`VideoStoriesPlus\`** — **VideoStories+** (name reserved by Ron 2026-10-10; StoryBuilder+ was taken):
  turns a person's spoken, phone-recorded story into a short captioned video (60–120 s): their own
  voice and face, photos placed on the words they illustrate, and AI cutaway animations the user makes
  in Google Flow from prompts the program writes. Guided steps (Story ▸ Record ▸ Transcript ▸ Plan ▸
  Pictures ▸ Assemble ▸ Produce ▸ Export), series templates, 16:9 + 9:16 + review copy + .srt; local Whisper with a
  cloud option; ffmpeg renders. WPF/.NET 10, free Store app; AI through the shared `AiManager`; repo
  `github.com/reaglin/VideoStoriesPlus` (private). The pilot, *AR Stories: Deep Hole*
  (`C:\Claude_Shared`, not shipped), is the test case. **Started 2026-10-10; phases 0–2 built the same
  day**: the render engine rebuilds Deep Hole from a story file (109.03 s against the pilot's 109.10 s),
  and the guided seven-step window with Series, Settings and About; Ron's hand-test of Deep Hole worked
  2026-10-10. **Phase 3 (transcription) built 2026-10-10:** Whisper on this computer (Whisper.net, DTW word
  times; Deep Hole within 0.05 s of the pilot's captions) or in the cloud through **AI Manager 1.5.0**
  (new: speech to text), the transcript editor, and the OneDrive question for where stories are kept; 74 tests
  green; ⚠️ Ron's hand-test 3. **Phase 4 (the AI) built 2026-10-10:** help with the telling, name checks, the plan
  proposed from the transcript (real Claude run on Deep Hole matched the pilot's structure and cuts), revision notes,
  photos placed on words, clip prompts with the pilot's rules, and **Cast & sets** — one library of characters (with
  permission, reference photos, every version and prompt), sets/locations and looks for all stories (Ron) — plus a
  guide to Google Flow / Veo; ⚠️ Ron's hand-test 4. **Phase 5 built 2026-10-10:** a beat editor (drag a picture onto
  the word it comes in on), clip review (frames, notes, where the action starts — it finds the pilot's gator wink), and a
  one-beat preview played in the window; ⚠️ Ron's hand-test 5. **Phase 6 built 2026-10-11:** step 7 Export — each finished file checked and marked current or out of date, which file to post where, the post text (AI optional, never gives the ending away), a YouTube thumbnail, copies to another folder; ⚠️ Ron's hand-test 6. **Phase 6b (Ron, 2026-10-12):** eight steps — 6 Assemble (photos and clips put on the beats' words, moved out of Plan), 7 Produce (rough cut + finished videos), 8 Export; every screen opens with its number, name and a "How to use this page" panel; the AI's suggestions at the bottom of every screen; Characters, Locations and Looks as three screens (Cast & sets is gone); step 5's list has thumbnails and PHOTO/CLIP badges; ⚠️ Ron's hand-test 7. **Phase 6c (2026-10-12):** Record and Transcript in numbered parts, help links to softwareplus.ai (pages still to write), the AI breaks the transcript into lines, each line becomes a beat, every kind of beat drawn as a wireframe; ⚠️ hand-test 8. **Phase 7 (the Store):** the sample story "My First VideoStory" ships in the program (Start ▸ Open the sample story); Ron hand-tested the application 2026-10-13; **Store package 1.0.0 built 2026-10-13** (identity `DeanEaglin.VideoStories`, Store ID 9NZWP2LCCPK7, 155 MB with FFmpeg and the sample; release docs in `docs/release/`, nine screenshots); WACK PASS 23/24 (2026-10-13); **submitted by Ron 2026-10-13** (FFmpeg source offer kept); **1.0.0 live on the Microsoft Store 2026-10-14**
  (https://apps.microsoft.com/detail/9nzwp2lccpk7; tagged `v1.0.0`); its softwareplus.ai page says "On the Microsoft Store", with Deep Hole and how it was made, and the home page tile fills the plus. Deep Hole will be the example on softwareplus.ai (Manny agreed). GPL ffmpeg ships beside it; no music (Ron). (The empty `StoryBuilderPlus\` folder can be deleted.)
  **Start with its `CLAUDE.md`.**

- **`MySocialPlus\`** — **MySocial+**: Ron's social media his way instead of the algorithm's — a
  topic tree on the left (roots **My Posts** and **My Friends**, more later), content on the right,
  a badge on every node with something new, everything in time order. Official APIs and RSS only
  (Bluesky, Mastodon, YouTube, RSS, Reddit fully; Facebook/Instagram limited to Ron's own posts —
  comment counts even where Meta hides names, which Ron finds worthwhile). WPF/.NET 10; AI through
  the shared `AiManager`. **Personal use, not a Store program; Bluesky first, then Facebook**
  (Ron, 2026-10-11). **Plan stage, started 2026-10-11** — `docs/PLAN.md`,
  `docs/DEVELOPMENT-PLAN.md`. **Start with its `CLAUDE.md`.**

- **`AccessibilityPlus\`** — **Accessibility+** (name reserved on the Microsoft Store by Ron, 2026-10-29):
  checks a **website** (URL), a **folder or file**, or an **`.imscc`** course export for accessibility,
  writes CourseBuilder+'s full report, then **suggests changes**, shows each as a **diff**, and makes the
  ones the person accepts (a URL's changes go to a downloaded copy). The engine is **copied from
  CourseBuilder+** and grows beyond it (WCAG 2.2, checks on the rendered page, …); later it becomes a
  shared package CourseBuilder+ moves to. WPF/.NET 10, free Store app; AI through the shared `AiManager`;
  repo `github.com/reaglin/AccessibilityPlus` (private). Identity `DeanEaglin.Accessibility`, Store ID
  9P89JG9TR6TB. Pass/fail line WCAG 2.1 AA, 2.2 reported beside it; no logins in 1.0. **Phases 0–1 built
  2026-10-29:** engine copied from PreseMaker `9acc2f3`, identical findings on all 13 real D2L exports, 102
  tests green, a first window that checks a `.imscc`; ⚠️ Ron's hand-tests 1–4. Assessment+ (CIATLE) holds a
  third, rules-only copy of the engine (`docs/ENGINE-SYNC.md`). **The editor built 2026-10-29** (phase 4, Ron hand-testing
  the same day): every fix shown as a change to approve, suggested words, colours, captions, buttons, assignments and
  discussions, list by type of problem, projects, putting the fixes into the course; 138 tests green. **1.0.0 live on the Microsoft Store
  2026-10-30** (https://apps.microsoft.com/detail/9p89jg9tr6tb; tagged `v1.0.0`; submitted 2026-10-29) (identity `DeanEaglin.Accessibility`, Store ID 9P89JG9TR6TB; release docs in
  `docs/release/`); **1.0.1** (Help ▸ About and every feature added 2026-10-30: the new main window, right-click Copy as HTML / paste instructions / Mark as completed with an upload icon, …) **live on the Microsoft Store 2026-10-31** (tagged `v1.0.1`; WACK PASS 23/24; its SoftwarePlus.ai page deployed the same day). **1.0.2** (Check for a new version, the form for every problem, Word/PowerPoint/PDF fixes, colour schemes, the AI check) **submitted for certification 2026-11-03** (WACK PASS 23/24) (Ron: ready to release with the current features; plan 7.15). Privacy policy, program page and
  help live on softwareplus.ai/accessibility/. **Start with its `CLAUDE.md`.**

- **`PLCPlus\`** — **PLC+** (Ron, 2026-11-04; free on the Microsoft Store, name to reserve in Partner Center): learn PLC programming at home, from electrical
  and logic basics to advanced ladder logic, with **simulated machines in place of real hardware**; the self-paced half
  of a PLC course (the lab is the other half), for students, a grant's faculty training cohort, and instructors who
  receive PDF progress reports. WPF/.NET 10, offline, many learners per computer with PIN-locked portable progress files.
  **Started 2026-11-04 from Ron's specification** (`docs/SPECIFICATION.pdf`). Its **`Learning.Core` is the shared
  learning engine** for this and Ron's other learning software: results, submission that works on every platform or
  straight to the instructor (like the Gamify+ games' signed result line), and many learners on one computer (Ron,
  2026-11-04). It becomes a `C:\nuget-local` package once a second program uses it. **Stay with what works** (Ron): MSIX on
  the Store, WPF drawing, .NET's own cryptography. **Phase 0 built 2026-11-04:**
  - the IEC engine on a simulated clock;
  - the grader;
  - the motor start/stop scene and challenge;
  - a first-look window.

  74 tests pass. **Ron answered the plan's 14 questions on 2026-11-04:**
  - JSON progress files; reports signed with the computer's key plus an optional class code;
  - the lab PLC is Allen-Bradley (the engine is compared against it, and Rockwell is the first dialect);
  - prerequisites are recommended, not enforced; the family's window layout;
  - no AI in Phase 1; Ron signs the content when it is published;
  - learners must back up their files; only the name is required on a report.

  ⚠️ Ron: hand-test 0. PLC+ reserved in Partner Center; repo public at https://github.com/reaglin/PLCPlus (2026-11-04). Phase 1 (engine: arrays, breakpoints, traces, reference programs R01–R11, the Allen-Bradley lab guide, which waits for the lab instructor) and **phase 2 (six simulated machines, each with a challenge, a working program and a common mistake) built 2026-11-04**; the window is a preview for the PLC instructors' review (`PLCPlus\docs\INSTRUCTOR-REVIEW.md`; self-contained zip in the gitignored `PLCPlus
eview\`); 130 tests. **Phase 3 (the ladder editor) built 2026-11-04**: "My program (edit it)" for every challenge, running live; 145 tests. **Phase 4 (the learning path) built 2026-11-04**: the family's tree-and-tabs window, 12 modules → items, each item with Learn / Example / Exercise / Reference tabs and the learner's status (Ron); drafts of modules 3 and 5, Markdown content with a validator, progress for one learner; 171 tests. The instructors review at **https://softwareplus.ai/plcplus/review/** (generated by `PLCPlus	ools\make-review-site.py`; Ron, 2026-11-04); examples will be similar machines, not the exercises' answers (Ron, D21). **Phase 5 (assessment) built 2026-11-04**: questions of five kinds on the module checks (find the fault on a faulted machine), Replay the failed test, timing and order in tests, mastery per outcome; 202 tests. ⚠️ Ron: hand-tests 4 and 5; send reviewers the review address ending `?user=yes`.
  **Start with its `CLAUDE.md`.**
- **BMPFast** (`reaglin\BMPTrains`, solution `BMPFast.sln`) — Ron's **commercial** stormwater-permitting
  program (WinForms, .NET 4.8): Best Management Practices to meet the Florida Assessment of
  Stormwater Treatment, from the BMPTrains (FDOT) team. Sold at **https://bmpfast.com** ($500 single-user
  year license with course and certification), not on the Microsoft Store. Its page on SoftwarePlus.ai
  is `site/bmpfast/` (added 2026-10-01).
- **`BMPFast_2\`** — **BMPFast Version 2**: WPF/.NET 10 rebuild of BMPFast with SMADA10's interface
  (tree: General Site Information → Catchments → Treatments, Catchment Routings, Calculators; tabs Entry,
  Plots, Report, Help). Any number of treatments of one type per catchment; several routings compared
  side by side. Engine ported as a copy of v1's (parity tests on v1's projects; later v1 fixes logged in
  `docs/V1-SYNC.md`); opens `.bmpt`, saves `.bmpf`; same bmpfast.com license keys as v1, sold at bmpfast.com and also listed free on the Microsoft Store (users buy licenses, not the software). Users choose the calculation method wherever there is more than one; v1's unfinished features are finished here (phase 11). Repo
  `github.com/reaglin/BMPFast_V2` (private). **Planned 2026-10-17** — `docs/DEVELOPMENT-PLAN.md`,
  phases 0–12. **Release candidate 2.0.2** (tagged `v2.0.2`) sent to the testers 2026-10-21; the reviewers' approval turns a
  candidate into the commercial release, **target mid-November 2026**; significant changes make the next candidate (2.0.3, …).
  **Named BMPFast Plus on the Microsoft Store** (identity `DeanEaglin.BMPFastPlus`, Store ID 9N19ZF13ML3X): **2.0.3 submitted
  for certification 2026-10-29** (WACK PASS 23/24; packaging ported from TrafficLab+; privacy `softwareplus.ai/bmpfast/privacy/`;
  release docs in `docs/release/`). **Start with its `CLAUDE.md`.**

## The website: SoftwarePlus.ai

- **`SoftwarePlus\`** — **https://softwareplus.ai**, the home of the Store programs (domain
  registered by Ron 2026-09-30; repo `github.com/reaglin/SoftwarePlus`, private). Plain static HTML: a home page for the family and **one folder per
  program** (`site/gamify/`, `site/coursebuilder/`, …) that grows into that program's own site.
  Served by Nginx on **its own Bluehost VPS** (self-managed NVMe 4, Ubuntu 26.04 LTS), bought
  2026-09-30: `server1.softwareplus.ai`, `50.6.227.129`, HTTPS by Let's Encrypt; `.\deploy.ps1`
  publishes. **Live since 2026-09-30** (setup guide: `docs/SERVER-SETUP.md`). Has an **Other
  projects** section (Android apps, websites) and BMPFast since 2026-10-01. When a program gets a new version, name, icon or screenshots,
  update its page there too. **Start with its `CLAUDE.md`.**
- **SoftwarePlus.ai is the central home for help and information for every program on its home page**
  (Ron, 2026-10-21: *"I am centralizing help for all the applications on this site."*). Many sessions, for
  many programs, publish to it — so deploys are controlled in one place:
  - **Before every deploy, check:** `.\deploy.ps1 -Status` (in `SoftwarePlus\`) shows the deploy running now and
    the requests waiting. Say so in the session if another one is running.
  - **A program's changes publish only its own folder:** `.\deploy.ps1 -Only <folder> -Reason "…"` (Ron, 2026-10-31: *"The
    deploy for each of the software products should not interfere with the other software subdirectories"*). Every deploy
    sends only the files that changed (checksums against the server), so it takes seconds; `-Check` lists what would go.
  - **Publish only with `SoftwarePlus\deploy.ps1`** (add `-Reason "<program>: what changed"`). It is the controller
    (Ron: *"An agent should control all the deploys and it should manage for all applications that use the site"*):
    every call joins one queue, one deploy runs at a time, the requests waiting are covered together by the next
    run, and each run has its own server folder and a server lock, so no deploy can wipe or overlap another.
    Run it in the background and wait for its result; a queued call can take a while.
  - **Never** copy to the server by hand (scp, rsync, ssh to `/var/www/softwareplus`), never stop, kill or restart
    another session's deploy, and never run the old `/tmp/softwareplus-deploy` steps. If a deploy fails, read its log
    (the path is in the error; all are in `%LOCALAPPDATA%\SoftwarePlus\deploy\runs\`) and tell Ron before trying again.
- **Privacy policies live on SoftwarePlus.ai** (decided 2026-09-30; **all ten copied 2026-10-01**,
  word for word, Windows programs and Android apps alike): `softwareplus.ai/<program>/privacy/` and
  `softwareplus.ai/projects/<app>/privacy/`. **Edit them there.** With each program's next release
  its Store or Play listing's privacy URL moves to the new address, and Ron then removes the page from
  PunchMonkeyServer, preferably as a redirect, since older installs and listings link to it. Until
  then both show the same text. Tracked in `SoftwarePlus\docs\DEVELOPMENT-PLAN.md`, phase 3.
- **Every Store release updates SoftwarePlus.ai** (decided 2026-09-30). Ron: *"Each publish of a
  software will also be accompanied by updates to the softwareplus.ai web site."* A release is
  not finished until the program's page matches it: name, version, price, Store link, features,
  screenshots, privacy if it moves, release notes, then `.\deploy.ps1`. The steps are in
  `SoftwarePlus\CLAUDE.md`, and each release is logged in its plan's phase 5. The Store's own list
  of what is published:
  https://apps.microsoft.com/search/publisher?name=Dean+Eaglin&hl=en-US&gl=US
- **Other Projects on SoftwarePlus.ai** (decided 2026-09-30): the Android apps (PunchMonkey,
  EasyPeasyGPX, Any6, NaViViewer, later AppOpenerAndTimer) and the websites (PunchMonkeyServer,
  Florida Course Repository at floridacourserepo.com) each get a page under `site/projects/`,
  linked from the home page's Other Projects section. A release of any of them updates its page
  too (`SoftwarePlus\docs\DEVELOPMENT-PLAN.md`, phase 6).
- **Classes on SoftwarePlus.ai** (2026-10-01): `softwareplus.ai/classes/` lists Ron's class websites —
  CourseBuilder+ courses on GitHub Pages at `https://reaglin.github.io/<COURSE>/`: EGN3214, EGN3443,
  COP3530, COP4708, COP4813, CEN3722. A new class is one more entry (plan phase 7).
- **Each program's folder covers every feature** (decided 2026-09-30): a summary page, feature
  pages and live examples. Ron's examples: Gamify+ shows all its built-in games, playable;
  CourseBuilder+ shows a course it built, with each type of content. These are added as each
  program is worked on (`SoftwarePlus\docs\DEVELOPMENT-PLAN.md`, phase 4).

## Shared libraries

- **`AiManager\`** — **the one AI layer for every AI-enabled app** (decided 2026-09-12; **1.7.0, 2026-10-16, makes pictures** —
  OpenAI, Gemini or xAI, chosen in AI Settings ▸ Provider for pictures): a
  `Eaglin.AiManager` class library (net10.0, providers Claude/Gemini/OpenAI/Mistral/xAI,
  DPAPI key store in `Documents\AiManager\`, activity log, usage ledger, prompt templates,
  model catalog), WPF and WinForms settings/dashboard packages, and a standalone AI Manager
  exe with a usage dashboard. Distributed as versioned NuGet packages from the local feed
  `C:\nuget-local` (`build\pack.ps1`). Consumers in order: AuthorPlus (first; deletes its
  `AuthorPlus.AI` copy), EasyPeasyRetirement, PreseMaker, CIATLE (`CIATLE.AICore` retired).
  Until an app has migrated, its own AI layer stands. **Start with its `CLAUDE.md` and
  `docs/PLAN.md`.**

The live cross-app tracker (API-36 deadline + extension, per-app versions, privacy URLs, the
production-release protocol, open to-dos) is imported here so it is always in context:

@.claude/PLAYSTORE.md

## Every AI program: the latest AI Manager with every release (decided 2026-10-11)

Ron: *"the new releases will need to update to the latest version and this will be something that
must occur with every version that we release of all the programs that use the AI Manager."*

- **Every release of a program that uses AI Manager first moves it to the latest AI Manager
  version** (the csproj's `Eaglin.AiManager` + its WPF or WinForms package), even when the release
  needs nothing new from it. Every program then shows the same AI Settings, key help and fixes.
  Read AI Manager's `docs/DEVELOPMENT-PLAN.md` for what changed, fix what it changes, tests green.
- **Then a hand-test exe in that repo's `manual-test\`** (gitignored; the command is in its
  `docs/MANUAL-TESTING.md`). Ron tests that exe before anything goes to the Store. All the AI
  programs use this same pattern.
- **The packages are built locally, not kept in git.** On a computer that has just pulled AI Manager,
  run `AiManager\build\pack.ps1` to put the latest version in `C:\nuget-local` before building a program.
- Each program's `CLAUDE.md` says this at the top, and its `docs/DEVELOPMENT-PLAN.md` carries the
  two standing items (R.1 move to the latest AI Manager, R.2 the manual-test build).

| Program (repo) | AI Manager pinned | Hand-test exe |
|---|---|---|
| CourseBuilder+ (`PreseMaker`) | **1.7.0** (latest, 2026-10-16: pictures) | `manual-test\PreseMaker.exe` |
| VideoStories+ (`VideoStoriesPlus`) | **1.7.0** (2026-10-31) | `manual-test\VideoStoriesPlus.exe` |
| Assessment+ (`CIATLE`) | **1.7.0** (2026-10-31) | `manual-test\CIATLE.FCE.exe` |
| TrafficLab+ (`TrafficLabPlus`) | **1.7.0** (2026-10-31, for 1.1) | `manual-test\TrafficLabPlus.exe` |
| Gamify+ (`GamifyPlus`) | **1.7.0** (2026-10-31, for 1.2.0) | `manual-test\GamifyPlus.exe` |
| Author+ (`AuthorPlus`) | 1.2.0 | `manual-test\AuthorPlus.exe` |
| Accessibility+ (`AccessibilityPlus`) | **1.7.0** (2026-10-29) | `manual-test\AccessibilityPlus.exe` |
| Retirement+ (`EasyPeasyRetirement`) | none yet — the rule applies once it has an AI feature | `manual-test\EasyPeasyRetirement.exe` |

Update the "pinned" column when a program moves.

## Every project: `docs/DEVELOPMENT-PLAN.md` (decided 2026-09-16)

Every program Ron and Claude work on keeps its plan in **`{repo}\docs\DEVELOPMENT-PLAN.md`** —
always that name, always that place, so Ron knows where to look in any repo.
**`LMS-2-Website\docs\DEVELOPMENT-PLAN.md` is the model to copy.** Repos without one are **not**
retrofitted now: when Ron returns to an app for updates or new development, that work starts by
creating its plan (fold in any existing `*PLAN*.md` content, or reference it). Each repo's
`CLAUDE.md` carries a short pointer back to this section.

**Why:** Ron tracks many projects at once and reads this file to see, at a glance, what is
done, what needs him, and what is left.

**Shape:**
- Phases (`## Phase N — name`, with a mark on the heading once the whole phase is settled), each a
  table of numbered tasks: `| # | Task | Done when |`.
- A short "How an item is marked" legend near the top.
- An **"Open questions for Ron"** section: numbered, dated when asked and when answered; an
  answer turns into (or updates) a task.
- A **References** section **at the end** listing every other document a task depends on
  (`docs/PLAN.md`, `docs/MANUAL-TESTING.md`, `RELEASE.md`, a source/methods doc, …) — relative
  path plus one line on what it is for. List only documents that exist.

**Marks — three states, nothing more elaborate:**

| Mark | Means |
|---|---|
| *(no icon)* or ⬜ | to do — not started or still being built (either is fine) |
| ⚠️ | **action needed** — built and tested, waiting for Ron to verify; *or* Ron returned it with a comment; *or* blocked on an answer from Ron. Say what the action is in the row |
| ✅ | done — built, tested, **and verified by Ron** |

Dropped items may be struck through with ❌ and the reason (as LMS-2-Website does).

**The flow each item moves through:** specification → questions → coding → testing →
UI/UX review → human testing (Ron or others) → ✅ verified, or returned with a comment/action
(stays ⚠️ with the comment recorded, then back to coding). Claude never marks an item ✅ on its
own — passing tests and a clean UX review earn ⚠️; only Ron's confirmation earns ✅. Update the
plan in the same commit as the work.

## Every program: the "+" names (decided 2026-09-26)

Ron likes the **Gamify+ / Author+** naming and is moving the Store programs to it. A rename is an
ordinary Store **update**, not a new app: the Store listing, its link and Store ID, the installs,
ratings and reviews all stay; the **package identity never changes** (Gamify+ is
`DeanEaglin.Gamify` and shows "Gamify+"). **Each rename is done with that program's next version,
as Ron works on it** — not all at once.

**Names reserved in Partner Center by Ron (2026-09-26):**

| Program (repo) | Store name now | New name — reserved | Status |
|---|---|---|---|
| PreseMaker (`PreseMaker\`) | PreseMaker | **CourseBuilder+** | **2.0.0.0 live 2026-09-29** (tagged `v2.0.0`; name moved onto the existing PreseMaker product); **2.0.1.0 live 2026-10-05** (tagged `v2.0.1`); privacy now `https://softwareplus.ai/coursebuilder/privacy/` (the old PunchMonkeyServer addresses redirect there) |
| CIATLE (`CIATLE\`, the CIATLE.FCE app) | CIATLE-FCE | **Assessment+** (changed from ProgramAssessment+ by Ron, 2026-09-29; reserved — on the existing CIATLE-FCE product via Manage app names, not a new product) | **2.0.0.0 live as Assessment+ 2026-10-01** (tagged `v2.0.0`; .NET 10, AI Manager; privacy `https://softwareplus.ai/assessment/privacy/index.html`) |

Others Ron has floated (not reserved yet): SMADA → **Hydrology+**.
**VideoStories+** (`VideoStoriesPlus`, Ron, 2026-10-10; **reserved in Partner Center**): new, so it ships
as VideoStories+ at 1.0; its icon carries the "+" (plan 7.1).
**EasyPeasyRetirement → Retirement+** (Ron, 2026-10-10; **reserved in Partner Center** the same day):
not yet on the Store, so it ships as Retirement+ at 1.0. Done 2026-10-10: the icon (the shaded nest
egg with a blue "+" on #1F4E8C, `EasyPeasyRetirement\packaging\make-icon.py`), SoftwarePlus.ai, and
the in-app name (manifest DisplayName, window title, About with its softwareplus.ai link, dialogs);
⚠️ Ron to look.

**What a rename changes** (in the program's next version):
- The package manifest's **DisplayName** (and the VisualElements display name) — it must match the
  reserved name exactly, or Partner Center refuses the upload.
- What a person reads: window titles, Help ▸ About, help text, dialogs, generated documents that
  name the program, the Store listing text, and any logo or screenshot that shows the name.
- The privacy page: a new page under the new name on PunchMonkeyServer, **with the old address
  kept working** (Gamify+'s page answers on three routes).
- Partner Center, when it is submitted: the listing's **Product name** set to the new name; after
  it is live, the old name may be deleted (an app always keeps at least one).

**What a rename does not change:** code names, namespaces, assembly and repo names, the package
identity, and the folders people's files are saved in (Gamify+ still saves to
`Documents\GamifyPlus`) — renaming those would lose people's work or break installs. "The program
is called X+ in front of a person, and keeps its code name in the code" — Gamify+'s rule.

**The "+" is in the icon too — it is the suite's theme** (Ron, 2026-09-29: *"The + is in the icon
for Gamify+, CourseBuilder+, and now in Assessment+ so it is the theme"*). Every "+" program's icon
is one simple white mark on the program's own colour, with a **"+"** as part of the mark: Gamify+,
CourseBuilder+ (the open book and plus), Assessment+ (the Plan → Implement → Assess → Revise loop
round a plus, `CIATLE\msix\make-store-assets.py`). **Author+ is next** — Ron: *"for Author+ we will
want to stick to the theme with the + in the icon"* (a task in `AuthorPlus\docs\DEVELOPMENT-PLAN.md`).
Hydrology+ follows if SMADA is renamed.

## Every program: "Created by Dr. Ron Eaglin" in About (decided 2026-09-25)

Ron: "it is time to start the marketing." Every program's **Help ▸ About** (or its About page)
shows **"Created by Dr. Ron Eaglin"** with his picture. **Not retrofitted now**: add it the next
time each program is updated, as a task in its `docs/DEVELOPMENT-PLAN.md`, and tick it off here.

- **The picture:** `C:\Users\ronal\OneDrive - Daytona State College\Pictures\Ron Eaglin (self)\Dr_Ron_Icon.jpg`
  (1024 × 1024; a copy is in `GamifyPlus\resources\images\dr-ron-eaglin-1024.jpg`). Ship a 256 px
  copy with the app (`magick … -resize 256x256 -quality 88`), shown at about 96 px with rounded corners.
- **The words:** "Created by Dr. Ron Eaglin" as a heading beside the picture, and a line under it
  suited to the program. **GamifyPlus** is the model (MainWindow.xaml, About: an `ImageBrush` on a
  rounded `Border`, the jpg as a WPF `Resource`).
- **MAUI apps:** the same card on the About/Settings page. Store listings keep the developer name
  each store has (Dean Eaglin on Play).
- **Games** made with a program credit the designer where Ron designed the game: GamifyPlus writes
  "Original game design by Dr. Ron Eaglin" on Pyramath, Fractazmic and I See Cards, and "Made with
  Gamify+" on every game.

| Program | Created-by in About |
|---|---|
| GamifyPlus | ✅ done 2026-09-25 |
| AuthorPlus, CIATLE (CIATLE-FCE), EasyPeasyRetirement, LMS-2-Website, PreseMaker, SeaGit (SEAGit), SMADA10, Statistle | built 2026-09-26 (Ron asked for all the Store programs at once) — committed and pushed; ⚠️ each waits for Ron to look, and ships with that program's next Store update |
| AiManager (its exe) | on next update |
| TrafficLabPlus | ✅ shipped in 1.0 (live 2026-10-10); Ron looked 2026-10-10 |
| AccessibilityPlus | built 2026-10-29; ships in 1.0.1 (the 1.0.0 package has no About); ⚠️ waits for Ron to look |
| VideoStoriesPlus | ✅ shipped in 1.0 (live 2026-10-14) |
| EasyPeasyGPX, Any6_FitnessTracker, NaViViewer, PunchMonkey, AppOpenerAndTimer | on next update |

## Every program: Help ▸ About links to its SoftwarePlus.ai page (decided 2026-09-30)

Each Store program's **Help ▸ About** (or About page) gets a link to **its own page on
https://softwareplus.ai**. The link goes beside the "Created by Dr. Ron Eaglin" card, with the
words "More about {program}, with help and examples: softwareplus.ai/{folder}". **Not
retrofitted now**: add it the next time each program is worked on, as a task in its
`docs/DEVELOPMENT-PLAN.md`. It **ships with that program's next Store release**, and the site is
updated in the same release (above). Tick it off here.

| Program | Its page | About link |
|---|---|---|
| Gamify+ (`GamifyPlus`) | https://softwareplus.ai/gamify/ | on next update |
| CourseBuilder+ (`PreseMaker`) | https://softwareplus.ai/coursebuilder/ | ✅ in 2.0.1 (live 2026-10-05): About links to the CourseBuilder+ page and its privacy policy |
| Assessment+ (`CIATLE`) | https://softwareplus.ai/assessment/ | ✅ in 2.0.0.0 (live 2026-10-01): About links to softwareplus.ai, the Assessment+ page and its privacy policy |
| Author+ (`AuthorPlus`) | https://softwareplus.ai/author/ | on next update (before 1.0 ships, if possible) |
| Statistle | https://softwareplus.ai/statistle/ | on next update |
| SMADA (`SMADA10`) | https://softwareplus.ai/smada/ | shipped in 1.1.0 (live 2026-10-15): About links to the SMADA page and its privacy policy; ⚠️ waits for Ron to look |
| SEAGit (`SeaGit`) | https://softwareplus.ai/seagit/ | on next update |
| LMS-2-Website | https://softwareplus.ai/lms-2-website/ | before 1.0 ships |
| Retirement+ (`EasyPeasyRetirement`) | https://softwareplus.ai/retirement/ | built 2026-10-10 (About links to softwareplus.ai/retirement); ships in 1.0; ⚠️ waits for Ron to look |
| TrafficLab+ (`TrafficLabPlus`) | https://softwareplus.ai/trafficlab/ | shipped in 1.0 (live 2026-10-10): About links to the TrafficLab+ page; ✅ Ron looked 2026-10-10 |
| VideoStories+ (`VideoStoriesPlus`) | https://softwareplus.ai/videostories/ | shipped in 1.0 (live 2026-10-14): About links to the VideoStories+ page |
| Accessibility+ (`AccessibilityPlus`) | https://softwareplus.ai/accessibility/ | built 2026-10-29 (About links to the page and its privacy policy); ships in 1.0.1 |

## Every program: Help ▸ About links to its Store page, its page and all programs (decided 2026-10-30)

Ron: *"The Help->About on all the apps should have a link to the location of the app on the Windows App Store. They
should also have a link to their subdirectory on SoftwarePlus.ai and a link to all programs."* So each program's
**Help ▸ About** has three links, beside the "Created by Dr. Ron Eaglin" card (and the privacy link where it has one):

- "More about {program}, with help and examples: softwareplus.ai/{folder}" (the rule above)
- "{program} on the Microsoft Store (updates, ratings and reviews): apps.microsoft.com/detail/{Store ID}"
- "All of Dr. Ron Eaglin's programs: softwareplus.ai" → `https://softwareplus.ai/#programs`

**Accessibility+ is the model** (`AccessibilityPlus\src\AccessibilityPlus.App\AboutWindow.xaml`). **Ron asked for every
program at once (2026-10-30: "Update all the other apps' About now")** — all built, tested and pushed the same day, each with
a ⚠️ plan item; each ships with that program's next Store release. A program not yet on the Store adds the Store link once
Partner Center gives its Store ID. A **new** program has all three from its first version.

| Program | Store page | About links (built 2026-10-30, commit; ⚠️ Ron to look, ships with the next release) |
|---|---|---|
| Accessibility+ (`AccessibilityPlus`) | https://apps.microsoft.com/detail/9P89JG9TR6TB | `173e8b4`, shipped in 1.0.1 (live 2026-10-31) |
| Gamify+ (`GamifyPlus`) | https://apps.microsoft.com/detail/9NT6TCCNDC1V | `cbcddb9` (plan 9.25) |
| CourseBuilder+ (`PreseMaker`) | https://apps.microsoft.com/detail/9MT854NV3FGF | `5b0dc0f` (plan 20.16) |
| Assessment+ (`CIATLE`) | https://apps.microsoft.com/detail/9PFNSN40RBZ4 | `73de8bd` (plan 45.7) |
| Statistle | https://apps.microsoft.com/detail/9MV608S7M9X6 | `dfa8a63` (plan 5.6) |
| SEAGit (`SeaGit\SEAGit`) | https://apps.microsoft.com/detail/9P7Z72K774JN | `ef748b1` (no plan file in that repo) |
| SMADA (`SMADA10`) | https://apps.microsoft.com/detail/9NNTZ8389WTK | `c0f5681` (plan 7.9); the About's Close button (worked only with Esc) fixed in `0066dad` (plan 7.10) |
| TrafficLab+ (`TrafficLabPlus`) | https://apps.microsoft.com/detail/9P5NGQF4HRPD | `01a1065` (plan 9.2) |
| VideoStories+ (`VideoStoriesPlus`) | https://apps.microsoft.com/detail/9NZWP2LCCPK7 | `48180b1` (plan 7.8) |
| BMPFast Plus (`BMPFast_2`) | https://apps.microsoft.com/detail/9N19ZF13ML3X | `a3b45b6` (plan 10.44); its missing privacy link added too |
| Author+ (`AuthorPlus`) | not on the Store yet | `b07b674` page + all programs (plan 4.10); Store link when there is an ID (4.11) |
| LMS-2-Website | not on the Store yet | `12685de` page + all programs (plan 6.13); Store link when there is an ID (5.6) |
| Retirement+ (`EasyPeasyRetirement`) | not on the Store yet | `92350c9` all programs added (plan 4.6); Store link when there is an ID (5.6). Its build failed the NuGet audit (NU1902/NU1903, `System.Security.Cryptography.Pkcs` 8.0.1 via PDFsharp): fixed in `2aac223` with a direct Pkcs 10.0.13 reference (plan 4.7) |

## Every program: Help ▸ Check for a new version (decided 2026-10-30)

Ron: *"Is it possible on the Help menu to add a 'check for new version?'"* … *"Add this to all the Windows Store Apps."*
Each Store program's **Help** menu has **Check for a new version…**: it asks the Microsoft Store (`Windows.Services.Store`,
so the App project targets `net10.0-windows10.0.19041.0`) whether a newer version is out — "You have the latest version
(x.y.z)", or it offers to download and install it (the Store shows its progress). A copy not installed from the Store (a
hand-test exe) says it cannot check and offers the Store page. **Accessibility+ is the model**
(`AccessibilityPlus\src\AccessibilityPlus.App\StoreUpdates.cs`). Built for every Store program at once; each ships with that
program's next Store release, and its Store path can only be tried in the Store-installed copy after that (⚠️ in each plan).
A **new** Store program has it from its first version (Author+, LMS-2-Website and Retirement+ when they reach the Store).

| Program | Built (commit, plan item) |
|---|---|
| Accessibility+ (`AccessibilityPlus`) | `60134f0` (plan 7.9), ships in 1.0.2 |
| Gamify+ (`GamifyPlus`) | `4da1205` (plan 9.26); a button in its About section (it has no Help menu) |
| CourseBuilder+ (`PreseMaker`) | `922c259` (plan 20.17); a button in its About window (no menu bar); in the 2.0.2 notes |
| Assessment+ (`CIATLE`) | `8eacb68` (plan 45.8); in both Help menus (main window and course editor). One test fails on the new EGN3214 FA26 export in Downloads (27 items, the test expects more than 40) — not this change |
| Statistle | `29fb5ee` (plan 5.7; 5.8 Pkcs audit fix). ⚠️ Its privacy policy says it "makes no network connections … checks for updates": Ron to decide the wording before the release that ships it |
| SEAGit (`SeaGit\SEAGit`) | `1d33aee` (no plan file, no tests). ⚠️ The next Store build must be 1.0.6 (the 1.0.5.0 .msixupload in `AppPackages` was rebuilt with this change); the untracked Inno Setup script still points at `bin\Release\net8.0-windows`; its privacy page and About say it makes no connection |
| SMADA (`SMADA10`) | `3ea38d7` (plan 7.11); its Store listing says "no network use" — soften at the next release (the check goes online only when asked) |
| TrafficLab+ (`TrafficLabPlus`) | `2e251e9` (plan 9.3) |
| VideoStories+ (`VideoStoriesPlus`) | `8107226` (plan 7.9) |
| BMPFast Plus (`BMPFast_2`) | `9800e38` (plan 10.45); a copy from a setup file is pointed to the Store. `tools/review_outstanding.py` not run yet (it writes SoftwarePlus and the BMPTrains spreadsheet, then needs a deploy) |

## Every Store program: the usability checklist (decided 2026-10-31)

Ron: *"The most important items for this round is to ensure that every application has a high level of usability …
localized help, tooltips, descriptive labels"* and *"we are looking for some consistency in the applications."*
**`USABILITY-CHECKLIST.md`** (in this folder) is the one list every program meets the same way: each screen says what it
is for with local help, every control has a label and a tooltip (disabled ones say why), inputs say what to type, feedback
and errors in plain words, no surprise loss of work, the same Help menu, About and Check-for-a-new-version wording. Its end
holds the **manual-test template**: each program's `docs/MANUAL-TESTING.md` has a "Round 2026-11 — usability" part in that
shape, and a current hand-test exe in `manual-test\`. UX reviews check against the list. The 2026-10-31 round's reviews are
in each repo's `docs/ux-reviews/2026-10-31-pre-release.md`; the fixes are ⚠️ plan rows tagged "UX review 2026-10-31".
`https://softwareplus.ai/status.html` (not linked) shows every program's version, release status, changes and site state.

## Every project: the development cycle (decided 2026-09-17)

Applies to all development, in every repo, in this order:

1. **Operational first.** The code runs and does the task that was asked — including building
   or extending its test suite as part of the work, not after. Nothing moves on until this holds.
2. **UI/UX second.** Every interface that is added or changed must pass a **cognitive
   walkthrough** and a **heuristic evaluation** (Nielsen's heuristics) before it goes to Ron.
   Use the `ux-reviewer` agent on the screens/pages touched; fix what it finds, or record why
   not. Record the review in the plan item (e.g. "UX: walkthrough + heuristics passed, 2 fixes").
   - **Err on the side of better instructions. Never assume the user knows how to use the
     software** — say what a screen is for, what to do next, what a setting means, and what
     went wrong in words a first-time user can act on.
   - A review read from source cannot judge rendered visuals (contrast, spacing, layout at
     scale); look at the running app for those (see memory on WPF window capture).
3. **Human testing.** Ron or other testers use it (hand-tests in `docs/MANUAL-TESTING.md`
   where the repo has one). The item sits at ⚠️ until then.
4. **Full circle.** What human testing returns — comments, confusion, bugs — becomes new plan
   items or ⚠️ comments and feeds the next round of code generation, back through steps 1–3.

## Conventions shared by all the MAUI apps

- **Toolchain:** Visual Studio 2022 17.14 + `dotnet` CLI. Repos are targeted to
  **.NET 10 / `net10.0-android` (API 36)**; the .NET 10 SDK (10.0.400), `maui-android`
  workload, and Android SDK platform 36 were installed 2026-08-22. net10.0-android builds
  need **JDK 17**: pass `-p:JavaSdkDirectory="C:\Program Files (x86)\Android\openjdk\jdk-17.0.14"`
  (the PATH default is jdk-11, which is too old). Always build with `-f <tfm>-android`;
  iOS/MacCatalyst targets are not built on Windows.
- **Upload keys:** all in `C:\keystores\` (Play App Signing is on, so these are *upload* keys).
  `C:\keystores\aliases.txt` maps keystore → alias. Passwords are **never** committed: the
  sibling apps read them from a gitignored `Directory.Build.props` at the repo root
  (`Directory.Build.props.template` shows the shape); Any6 currently uses env vars via
  `publish-release.ps1` — align it to `Directory.Build.props` when convenient.
  Before signing, verify the cert with `keytool -printcert -jarfile <aab>` against the
  fingerprint recorded in that app's `RELEASE.md` — two apps (Any6, PunchMonkey) have
  look-alike keystores that are *not* the registered upload key.
- **Release shape per repo:** `RELEASE.md` (checklist, key fingerprints, Play steps),
  `store/` or `store-assets/` (listing art + `release-notes-<ver>.txt`), and a signed-AAB
  publish step (`dotnet publish … -c Release -p:AndroidPackageFormat=aab`, output in
  `bin\Release\<tfm>-android\publish\*-Signed.aab`). Every Play upload needs a higher
  `ApplicationVersion` (versionCode).
- **Device smoke test before upload:** install the Release *APK* from the same publish folder
  (`adb install -r`), uninstalling any Play-installed copy first (Google re-signs, so
  signatures mismatch), exercise the core flow, check `adb logcat` for FATAL/exceptions.
  Test phone: Samsung Galaxy S24 Ultra (SM-S928U, Android 16); adb is at
  `%LOCALAPPDATA%\Android\Sdk\platform-tools\adb.exe`. The phone must be unlocked — adb
  cannot get past the PIN prompt.
- **Privacy policy URLs** are per-app pages on PunchMonkeyServer
  (`https://punchmonkeyserver.com/privacy/<app>`); see the tracker for the exact URLs.
- **Code style:** CommunityToolkit.Mvvm (`[ObservableProperty]`, `[RelayCommand]`), pages
  resolved from DI, `x:DataType` compiled bindings, `AppThemeBinding` for light/dark.
  MAUI 10: use `DisplayAlertAsync` (not `DisplayAlert`).
- **Policy deadlines apply to every app.** When a Play-policy or tooling fix lands in one repo,
  say whether the others need it and update `.claude\PLAYSTORE.md`.

## Useful references in this directory

- `maui_publish_to_google_play_guide.html` — step-by-step MAUI → Play publishing guide.
- `.claude\PLAYSTORE.md` — the tracker imported above (edit it, not this file, for status).
- `.claude\settings.local.json` — permission allow-list for this directory.
