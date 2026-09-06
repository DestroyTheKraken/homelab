# Ops UI / ticket-delivery — system scan (2026-09-05)

**Purpose:** Inventory of apps already on um690 that could support a future daily-ops / ticket UI.  
**Not a design.** Homelab start/stop/review methodology remains undesigned.

## Already installed (strong hits)

| App | Path / version | Ticket-ish role |
|-----|----------------|-----------------|
| **Kontact** | `/usr/bin/kontact` · KDE PIM 25.12.3 | Shell that hosts Mail + Calendar + Contacts |
| **KMail** | `/usr/bin/kmail` | **Delivery channel** — assignments as mail (labels/folders = queues) |
| **KOrganizer** | `/usr/bin/korganizer` | **Schedule + to-dos** — due dates, recurrence, progress |
| **KAddressBook** | `/usr/bin/kaddressbook` | People / family contacts |
| **Akonadi** | server + IMAP + ical resources | Backend for the above |
| **KWrite / Kate** | `/usr/bin/kwrite`, `kate` | Draft ticket text / phase notes (not a tracker) |
| **Google Chrome** | stable | Gmail / Calendar / Grok Web PWAs |
| **gh** | `/usr/bin/gh` | GitHub Issues as tickets — **auth token currently invalid** |
| **Dolphin** | installed | File evidence attachments |
| **kaccounts-*** | installed | KDE Online Accounts plumbing |

### Already wired

- Akonadi IMAP resource: **`Gmail (destroythekraken)`** · `UserName=destroythekraken@gmail.com`  
  So KMail ↔ that mailbox is not theoretical — it is configured.

## Missing / weak on this machine

| Wanted | Status |
|--------|--------|
| KNotes / KAlarm / Zanshin | Not on PATH / not installed |
| Nextcloud desktop client | Not installed |
| Taskwarrior / vit | Not installed |
| Flatpak/Snap kanban (Plane, Focalboard, Vikunja, …) | None found |
| Dedicated ticket product (Kanboard, Redmine, …) | Not installed |
| Plasma task/todo plasmoids | None beyond icon tasks |
| `gh` usable for Issues | Needs `gh auth login` |

## Apt candidates (not installed; low-friction adds)

| Package | Why consider |
|---------|----------------|
| `zanshin` | KDE to-do manager on Akonadi (pairs with Kontact) |
| `merkuro` | Newer KDE mail/calendar/tasks suite (alternative UI on same stack) |
| `taskwarrior` | CLI tickets — good for LFCS lane, not a family GUI |

## Thought check: KWrite + KMail + Grok Web + Google + KOrganizer

| Piece | Verdict |
|-------|---------|
| **KMail + Gmail (destroythekraken)** | **Yes — best delivery pipe you already have** |
| **KOrganizer to-dos/calendar** | **Yes — best progress/due-date UI you already have** |
| **Kontact** | Use as the single window instead of juggling separate apps |
| **KWrite/Kate** | Fine for composing ticket bodies; do not treat as the tracker |
| **Google connection** | Already present via Akonadi IMAP; Calendar sync may still need a CalDAV/Google resource if to-dos should live in Google Calendar |
| **Grok Web automation** | **Highest complexity / fragility.** Defer until mail+todos alone prove useful. Prefer: human pastes a ticket template into KMail, or later a simple script that opens a draft — not browser automation. |

### Minimal pattern that matches “ticket delivery” without new products

1. Folder/label in KMail: e.g. `Ops/Inbox`, `Ops/Doing`, `Ops/Done` (or tags).  
2. Each ticket = email to self (or from Grok draft) with subject `PHASE-0: …` / `OPS: …`.  
3. KOrganizer to-do linked to due date for that subject.  
4. Evidence = reply thread + optional files in Dolphin.  

That is a **PIM-based ticket system**, not Jira — appropriate until you design a real ops methodology.

## Explicit non-recommendations (for now)

- Building a custom Plasma UI or automating Grok Web as the ticket bus  
- Standing up Vikunja/Kanboard/Plane on LabNet before Phase 0–1 platform work  
- Using GitHub Issues as the only ops UI while `gh` auth is broken (fixable later for code tasks only)

## Next design questions (when you are ready — not answered here)

1. Is a “ticket” an **email**, a **calendar to-do**, a **git issue**, or all three?  
2. Who receives tickets — only you, or family?  
3. Must progress sync to Google Calendar, or is local Akonadi enough?

## Related AIDE research (ticket delivery / daily guides)

BraveResearch + NetworkAIDE synthesis (Zammad, inbox levels, AIDE_OS UX):

`~/Projects/AIDE/aideTutor/Refs/ticket-delivery-from-brave-research.md`

Primary BraveResearch source: `~/Documents/BraveResearch/sysadmin-helpdesk-aideTutor.md`