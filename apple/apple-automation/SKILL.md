---
name: apple-automation
description: "Operate Apple apps and services through macOS automation."
version: 1.0.0
author: Hermes Agent
license: MIT
platforms: [macos]
metadata:
  hermes:
    tags: [apple, macos, notes, reminders, messages, findmy, automation]
    related_skills: [macos-computer-use, obsidian]
---

# Apple Automation

## Overview

Use this umbrella for Apple ecosystem tasks on macOS. Prefer purpose-built CLIs when available (`memo`, `remindctl`, `imsg`, FindMy tooling) and fall back to `computer_use` only when the CLI cannot express the task. Apple apps often require Privacy & Security permissions; stop and ask before clicking permission dialogs or typing secrets.

## When to Use

- Creating, searching, editing, exporting, or organizing Apple Notes.
- Adding, listing, or completing Apple Reminders.
- Sending or checking iMessage/SMS via the local Messages database/CLI.
- Locating Apple devices or AirTags through Find My.
- Cross-device Apple workflows where iCloud sync matters.

## Apple Notes (`memo`)

Prerequisites: macOS Notes.app and `brew tap antoniorodr/memo && brew install antoniorodr/memo/memo`.

```bash
memo notes                         # list notes
memo notes -f "Folder Name"        # filter by folder
memo notes -s "query"              # fuzzy search
memo notes -a "Title"              # quick-create note
memo notes -a                       # interactive editor
memo notes -e                       # select and edit
memo notes -m                       # move note to folder
memo notes -ex                      # export notes
```

Use Obsidian instead for Markdown-native vault work. Use the `memory` tool for agent-only facts that do not need iCloud sync.

## Apple Reminders (`remindctl`)

Use reminders for actionable user-facing tasks, not agent-internal TODOs.

Common pattern:

```bash
remindctl add "Buy milk" --list "Reminders"
remindctl list
remindctl complete <id>
```

If a due date, list name, or recurrence is ambiguous and materially changes the reminder, ask; otherwise choose the default Reminders list.

## Messages / iMessage (`imsg`)

Use the Messages CLI only for contacts/chats the user explicitly asks you to message. Do not send sensitive content without the user's exact wording.

Typical flow:

```bash
imsg search "Alice"
imsg send "+15551234567" "Message text"
imsg chats
```

Verify the resolved recipient before sending when multiple contacts match.

## Find My

Use Find My only for the user's own devices/AirTags or explicitly authorized family/shared items. Location can be sensitive; summarize at an appropriate precision unless the user needs exact coordinates.

Expected flow: list devices/items, select the matching label, then report status, last-seen time, battery, and location confidence.

## GUI Fallbacks

When the CLI fails or the operation is inherently visual, load `macos-computer-use` and drive the native app with `computer_use`:

1. Capture with `mode="som"` scoped to the app.
2. Click by element index, not raw coordinates.
3. Verify after every state-changing action.
4. Never click permission, password, 2FA, or payment dialogs without explicit user direction.

## Common Pitfalls

1. **Using Apple Notes for private agent memory.** If the note is only for future agent behavior, use `memory`; if the user wants a synced note, use Notes.
2. **Assuming permissions are already granted.** Apple Automation, Contacts, Messages, Location, and Screen Recording permissions may block commands.
3. **Recipient ambiguity.** Messages can resolve multiple phone numbers/emails; verify before sending.
4. **Over-reporting location.** Find My output is sensitive; avoid exact coordinates unless necessary.

## Verification Checklist

- [ ] Confirm the relevant CLI is installed or choose a GUI fallback.
- [ ] Verify target app/list/contact/device before writing or sending.
- [ ] Re-read/list after changes when possible.
- [ ] Respect macOS permission and secret-handling safety rules.
