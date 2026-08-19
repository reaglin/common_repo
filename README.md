# common_repo — shared Claude Code guidance for Ron Eaglin's app portfolio

Clone this into the parent directory that holds the individual app repos
(e.g. `C:\Users\ronal\source\repos\`). Claude Code loads `CLAUDE.md` from the working
directory and every parent directory, so:

- start a session **here** to work across several related projects at once;
- start a session inside an app repo and you get this shared guidance **plus** that app's own
  `CLAUDE.md`.

Contents

| File | Purpose |
|---|---|
| `CLAUDE.md` | Portfolio overview + conventions shared by all the .NET MAUI / Google Play apps; `@`-imports the tracker below |
| `.claude/PLAYSTORE.md` | Live cross-app Play Store tracker: API-36 deadline/extension, per-app versions and keystores, privacy URLs, release protocol, to-dos |
| `maui_publish_to_google_play_guide.html` | Step-by-step MAUI → Google Play publishing guide |

The `.gitignore` is a whitelist: nothing else in the directory (app repos, local settings,
credential notes) is ever tracked.
