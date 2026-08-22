# Play Store releases — protocol + requirements tracker

Covers the four production apps: **EasyPeasyGPX, Any6_FitnessTracker, NaViViewer, PunchMonkey**.
All release work happens on this machine (Ron's primary development machine). Per-app details live in
each repo's `RELEASE.md` (EasyPeasyGPX's is the template); this file tracks the cross-app items.

## Hard requirement: target API 36 by Nov 1, 2026

Google Play requires targetSdk **36** (Android 16) for updates from Aug 31, 2026.
**Ron obtained an extension to Nov 1, 2026.** Plan:

1. Get the current releases operational (API 35-or-lower builds are acceptable under the extension).
2. **September 2026:** retarget every code base to **.NET 10 / API 36**.
3. Upload an updated AAB for each app **before Nov 1, 2026**.

EasyPeasyGPX's retarget commit (`a75f9b7` in that repo) is the template: TFM `net9.0-*` → `net10.0-*`,
`DisplayAlert` → `DisplayAlertAsync` (MAUI 10 deprecation), then fix whatever API-level analyzers flag
(e.g. its `Notification.Builder(Context, channelId)` crash below API 26).

## App status (updated 2026-08-22)

**Toolchain (2026-08-22):** .NET 10 SDK **10.0.400** installed alongside 9.0.312; `maui-android` 10.0.20
workload + Android SDK **platform 36** installed; net10.0-android builds need **JDK 17** at
`C:\Program Files (x86)\Android\openjdk\jdk-17.0.14` (pass `-p:JavaSdkDirectory=...`; the PATH jdk-11 is
too old). API-36 store builds are unblocked for all apps.

| App | ApplicationId | Version / code | TFM | minSdk | Upload keystore | Status |
|---|---|---|---|---|---|---|
| EasyPeasyGPX | `com.eaglin.easypeasygpx` | 1.0 / 3 | **net10.0 / API 36** | 24 | `C:\keystores\easypeasygpx.keystore` (alias `easypeasygpx`) | 1.0 (3) **API-36 AAB built, signature verified, device smoke test PASSED 2026-08-22** (first net10.0-android store build; commit `e753b5d`); Ron uploading to Production 2026-08-22 (replaces the 1.0 (2) API-35 AAB in review since 2026-08-17); tag `v1.0` once live; next build = versionCode 4 |
| Any6_FitnessTracker | `com.roneaglin.any6_fitnesstracker` | 1.0 / 3 | **net10.0** (repo, `d6271ee` 2026-07-28, +maccatalyst) — built vc3 AAB is net9/API 35 | 21 | `C:\keystores\any6alias.playupload.keystore` (alias `any6alias`, SHA-256 `18:6D:6E:22…`) — **not** `eaglin.any6_fitness.keystore` / repo `key.keystore` (different key; Play rejects it) | 1.0 (3) signed AAB built + signature verified + device smoke test PASSED 2026-08-19 (`release\…-v1.0-vc3.aab`, built from the .NET 9 tree); production-access request **still in review as of 2026-08-22** — when granted, rebuild on .NET 10 / API 36 (toolchain now installed) as versionCode 4 and upload that instead of the API-35 vc3 |
| NaViViewer | `com.eaglin.naviviewer` | 1.0 / 6 | **net10.0** (repo, `1e78f97`) — shipped AAB was net9/API 35 | 24 | `C:\keystores\naviviewer.keystore` (alias `naviviewer`) | 1.0 (6) signed AAB built + signature verified 2026-08-17 (`RELEASE.md`, `store/release-notes-1.0.txt` added); 1.0 (6) submitted to Production 2026-08-17, **approved — rollout in progress, not yet complete, as of 2026-08-22**; tagged `v1.0`; **Ron has app changes planned** → next build = versionCode 7 on .NET 10 / API 36 (toolchain ready) |
| PunchMonkey | `com.eaglin.punchmonkey` | 1.22 / 22 | **net10.0** (repo, `91ac48d` merged 2026-08-18) — shipped AAB was net9/API 35 | 26 | `C:\keystores\mycompany.myapp.keystore` (alias `myapp`) — legacy name, **do not rename**: it is the registered upload key | 1.22 (22) signed AAB built + signature verified 2026-08-18 (`RELEASE.md`, `store/release-notes-1.22.txt`); device smoke test PASSED 2026-08-18 (one non-reproducible ANR noted in RELEASE.md); **Play Console shows app status Production, last updated Aug 18 (2026-08-22 screenshot)** — confirm 1.22 rollout, then tag `v1.22` + bump server `LatestAppVersion` to 1.22 + deploy |

Keystore passwords come from each repo's gitignored `Directory.Build.props`. All apps use Play App
Signing — the local keystores are **upload** keys only (a lost upload key is resettable in Play Console).

## Privacy policy URLs (deployed 2026-08-17)

Google rejected the shared `https://punchmonkeyserver.com/privacy` URL (did not name the app / developer
entity). Each app now has its own page on PunchMonkeyServer (`Components/Pages/Privacy/*.razor`, commit
`c801155`), naming the app, package id, and developer (Ron Eaglin). **Set the Play Console → App content →
Privacy policy URL for each app to its own page:**

| App | Privacy policy URL |
|---|---|
| PunchMonkey | `https://punchmonkeyserver.com/privacy/punchmonkey` |
| NaViViewer | `https://punchmonkeyserver.com/privacy/naviviewer` (old `/apps/naviviewer/privacy` still resolves) |
| EasyPeasyGPX | `https://punchmonkeyserver.com/privacy/easypeasygpx` |
| Any6_FitnessTracker | `https://punchmonkeyserver.com/privacy/any6fitness` |

`/privacy` is now an index of the four. All pages name the developer as **Dean Eaglin** (matching the
Play Console account name), updated + deployed 2026-08-22 (PunchMonkeyServer commit `0d8eeec`); the
contact email remains ron.eaglin@gmail.com.

## Production-release protocol (per app)

Proven on EasyPeasyGPX 2026-08-16; repeat for each app:

1. **Version bump** — new `ApplicationVersion` (versionCode; Play rejects reuse), and
   `ApplicationDisplayVersion` to the production number (e.g. 1.0).
2. **Build** — `dotnet publish <proj>.csproj -f <tfm>-android -c Release` → upload the
   `*-Signed.aab` from `bin/Release/<tfm>-android/publish/`.
3. **Verify the signature** — `keytool -printcert -jarfile <aab>` must match the upload-key
   fingerprints recorded in the app's RELEASE.md.
4. **Device smoke test** — install the Release **APK** from the same publish folder on a physical
   device and exercise the core flow. The Play closed-testing install must be uninstalled first
   (Google re-signs with the app key, so signatures mismatch).
5. **Release notes** — write `store/release-notes-<ver>.txt` (`<en-US>` block, paste-ready).
6. **Play Console** — Production → Create new release → upload AAB → keep pre-filled release name →
   paste notes → review → staged rollout (e.g. 20%) → 100% after a few crash-free days.
7. **Git** — commit the version bump + notes + RELEASE.md updates, push, and tag (e.g. `v1.0`)
   once the release is live.

## Per-app to-dos before their production release

- **Any6_FitnessTracker**
  - ~~Create `CLAUDE.md`~~ ~~add `RELEASE.md` + Release-signing block~~ done 2026-08-19
    (`CLAUDE.md`, `RELEASE.md`, `publish-release.ps1`, `store-assets/`; pushed as `f1a1957`/`783875e`).
  - Signing differs from the siblings: csproj signs only when `ANDROID_STORE_PASS` env var is set
    (driven by `publish-release.ps1`). Align to `Directory.Build.props` when convenient.
  - The registered upload key is the VS-generated `Any6Alias` keystore (copied to
    `C:\keystores\any6alias.playupload.keystore`); the repo's `key.keystore` is a different key —
    remove or clearly label it.
  - Set Play Console → App content → Privacy policy URL to `https://punchmonkeyserver.com/privacy/any6fitness`.
  - Trim `net10.0-maccatalyst` (+ windows/tizen leftovers) if out of scope.
  - Production-access request pending (submitted 2026-08-19); then upload vc3 (or an API-36 rebuild) and tag `v1.0`.
- **NaViViewer** — ~~add a `RELEASE.md`~~ done 2026-08-17 (1.0 / 6). Submitted to Production + tagged `v1.0` 2026-08-17.
- **PunchMonkey** — ~~add a `RELEASE.md`~~ done 2026-08-18 (1.22 / 22). Smoke test passed 2026-08-18. Remaining: upload to Production, tag `v1.22`, then bump server `LatestAppVersion` to 1.22 + deploy.

## September .NET 10 / API 36 migration checklist (all four apps)

- [x] EasyPeasyGPX — retargeted (`a75f9b7`); **API-36 versionCode-3 build DONE + smoke tested 2026-08-22; uploaded to Production by Ron 2026-08-22**.
- [x] Any6_FitnessTracker — retargeted (`d6271ee`, 2026-07-28); still needs the API-36 store build (versionCode 4, since vc3 was built from the .NET 9 tree) + upload before Nov 1 — waiting on production access.
- [x] NaViViewer — retargeted (`1e78f97`); still needs the versionCode-7 store build + upload before Nov 1 (bundle with Ron's planned app changes).
- [x] PunchMonkey — retargeted (`91ac48d`); still needs the versionCode-23 store build + upload before Nov 1.

Toolchain prerequisite (.NET 10 SDK + maui-android + Android platform 36 + JDK 17) installed and
verified 2026-08-22 — see the note above the app-status table for the exact build flags.
