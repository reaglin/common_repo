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
  `docs/DEVELOPMENT-PLAN.md` are complete as of 2026-09-03; phase 6 is Store submission.
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
- **`EasyPeasyRetirement\`** — retirement "what if?" planner (when to retire, when to claim;
  Social Security, pensions, accounts, home, expenses; year-by-year projection with taxes and
  RMDs; scenarios compared side by side). All data local. WPF/.NET 10, Microsoft Store; repo
  `github.com/reaglin/EasyPeasyRetirement` (private). **Plan stage as of 2026-09-05** — no code
  yet; `docs/PLAN.md`, `docs/DEVELOPMENT-PLAN.md`, `docs/RULES-AND-SOURCES.md`. Copies SMADA's
  metadata-on-the-property core rather than referencing it. **Start with its `CLAUDE.md`.**

## Shared libraries

- **`AiManager\`** — **the one AI layer for every AI-enabled app** (decided 2026-09-12): a
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
| EasyPeasyGPX, Any6_FitnessTracker, NaViViewer, PunchMonkey, AppOpenerAndTimer | on next update |

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
