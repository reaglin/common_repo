# Usability checklist — every Store program (Ron, 2026-10-31)

Ron: *"The most important items for this round is to ensure that every application has a high level of usability
based on the principles of the cognitive walkthrough and heuristic evaluation. This can be achieved through localized
help, tooltips, descriptive labels, and all of the items that dictate good user design for usability."* and *"we are
looking for some consistency in the applications."*

Every program meets each item below, in the same way, so a person who knows one program finds their way in the next.
A program's UX review checks against this list; its `docs/MANUAL-TESTING.md` has a part that walks it (template at the end).
**Never assume the user knows the software.**

## 1. Every screen says what it is for (local help)

| # | Rule |
|---|---|
| 1.1 | Each window, page, tab or step opens with one or two plain sentences: what it is for and what to do first. |
| 1.2 | Each screen has local help: a "How to use this page" panel, a help pane, or **Help ▸ Help for this screen (F1)** that opens help about *that* screen, not a general index. |
| 1.3 | The local help links to the matching page of the program's help on SoftwarePlus.ai (`https://softwareplus.ai/<folder>/help/…`) for more. |
| 1.4 | An empty screen (no project, no data, nothing selected) says what to do to fill it, with a button for it where possible — never a blank area. |
| 1.5 | First start points to the sample/example and to the first step. |

## 2. Every control is labelled and explained

| # | Rule |
|---|---|
| 2.1 | Button and menu labels say what happens: verb + object ("Publish to GitHub", not "Go"). An ellipsis (…) when a window or question follows. |
| 2.2 | **Every** button, menu item, icon, toggle and field has a tooltip: what it does, and any consequence ("replaces the values now in the table; Undo brings them back"). |
| 2.3 | A disabled control's tooltip says **why** it is disabled and what enables it (WPF: `ToolTipService.ShowOnDisabled="True"`; WinForms: say it in the status line or a label beside it). |
| 2.4 | Icon-only buttons have a visible label or a tooltip **and** an accessible name (AutomationProperties.Name / AccessibleName). |
| 2.5 | Access keys are unique within a window; Enter = the default action and Esc = Cancel/Close in every dialog. |

## 3. Every input says what to type

| # | Rule |
|---|---|
| 3.1 | A label, the units, and an example or the allowed range ("Area (acres, e.g. 12.5)"). |
| 3.2 | Required vs optional is shown the same way throughout the program. |
| 3.3 | A rejected value says why, next to the field, and what is used meanwhile ("'12,5' is not a number; still using 12"). |
| 3.4 | What is typed is kept when the user saves, closes or switches without leaving the field. |

## 4. Every action gives feedback

| # | Rule |
|---|---|
| 4.1 | Success: a short confirmation of what happened and where ("Saved to Documents\…"). |
| 4.2 | Failure of something the user asked for: a dialog with what went wrong in plain words, the likely cause, and the next step. Technical text only after "Details for support:", never raw exceptions, HRESULTs or enum names. |
| 4.3 | Long work (more than about a second): a busy cursor or progress, the starting control disabled so it cannot run twice, Stop where it can stop. |
| 4.4 | Progress and routine notes go in the status line; failures do not go *only* there. |

## 5. Work is never lost by surprise

| # | Rule |
|---|---|
| 5.1 | Close, New, Open, and **Check for a new version → install** ask "Save changes to {file}?" Yes / No / Cancel when there are unsaved changes. |
| 5.2 | Delete, replace and overwrite name what will be lost and say whether Undo brings it back. |
| 5.3 | Undo history belongs to one document (cleared on New/Open). |
| 5.4 | A crash or damaged file gives a message and keeps the work (recovery copy offered, never deleted without asking). |

## 6. The same words and the same places in every program

| # | Rule |
|---|---|
| 6.1 | The program's "+" name everywhere a person reads it; no code names, plan numbers or "coming in a later build". |
| 6.2 | One word for one thing in the whole program (e.g. "folder" vs "repository", "Program Outcomes" vs "SLOs"). |
| 6.3 | **Help menu, in this order and with these words:** *Help for this screen (F1)* · *Help on the web (softwareplus.ai/<folder>)* · *Check for a new version…* · *About {program}…*. A program without a menu bar puts the same items in its About/Help area. |
| 6.4 | **About:** "Created by Dr. Ron Eaglin" card, the version, links to the program's page, its Microsoft Store page, all programs, and its privacy policy. |
| 6.5 | **Check for a new version:** "Asking the Microsoft Store…" while it runs; "You have the latest version of {program} ({version})"; before installing: save question (5.1), then "Windows closes {program} to install it; open it again from the Start menu."; a copy not from the Store says it cannot check and offers the Store page. |
| 6.6 | Message box titles are "{program}" or "{program} — {subject}". |

## 7. Visual checks a person must make (cannot be judged from source)

Text contrast (at least 4.5:1), nothing cut off at 125–200 % scaling and at the minimum window size, focus visible
when tabbing, colour never the only signal (an error also has words or an icon), high-contrast theme readable.

---

## Template: the manual-test part for this round

Each program's `docs/MANUAL-TESTING.md` gets a part, at the top, in this shape (copy it, fill in the program's own tasks):

```markdown
## Round 2026-11 — usability (Ron, 2026-10-31)

Build: `manual-test\<Program>.exe` (made <date>, version <x.y.z>). Close any copy that is open first.
Record each step as ✅ / ❌ with a note; ❌ and notes go back into docs/DEVELOPMENT-PLAN.md.

### A. First start, as a new user
A1. Start it. Does the first screen say what the program is for and what to do first? Is the sample/example offered?
A2–A5. <the program's 3–5 core tasks, each "Do … — expected: …"> — at each step, could you tell what to do next
     without knowing the program?

### B. This round's fixes
B1… one step per ⚠️ plan row marked "UX review 2026-10-31": what to do, what you should see.

### C. Every screen (USABILITY-CHECKLIST.md 1–4)
For each window/step: <list them>. Hover every control: tooltip? Disabled ones say why? Help for this screen opens
help about this screen? Empty state says what to do? A wrong value says why?

### D. Same as every program (checklist 5–6)
D1. Change something, then Close / New / Open: asked to save?  D2. Help menu items and order as in 6.3.
D3. About: version, four links work.  D4. Check for a new version (hand-test copy: says it cannot check, offers the Store page).

### E. Look (checklist 7)
At 150 % scaling and the smallest window size: anything cut off, hard to read, or colour-only?
```
