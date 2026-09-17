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
verification by Ron → ✅ verified, or returned with a comment/action (stays ⚠️ with the comment
recorded, then back to coding). Claude never marks an item ✅ on its own — passing tests earns ⚠️;
only Ron's confirmation earns ✅. Update the plan in the same commit as the work.

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
