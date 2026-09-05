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
  Book = folder of files under `Documents\AuthorPlus\Books`; AI layer is a copy of
  `CIATLE\CIATLE.AICore` and can borrow PreseMaker's saved API keys. **Start with its `CLAUDE.md`.**

The live cross-app tracker (API-36 deadline + extension, per-app versions, privacy URLs, the
production-release protocol, open to-dos) is imported here so it is always in context:

@.claude/PLAYSTORE.md

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
