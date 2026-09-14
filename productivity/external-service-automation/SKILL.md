---
name: external-service-automation
description: "Route work across third-party services and integrations."
version: 1.0.0
author: Hermes Agent
license: MIT
platforms: [linux, macos, windows]
metadata:
  hermes:
    tags: [productivity, api, cli, oauth, google-workspace, airtable, notion, email, maps, obsidian, hue, twitter, yuanbao]
    related_skills: []
---

# External Service Automation

## Overview

Use this umbrella for operating real services from Hermes through CLIs, REST APIs, OAuth credentials, local files, or messaging gateways. The unifying workflow is: identify the service, confirm credentials/scope, use the least-surprising official or documented interface, verify the side effect, then report exact handles (record IDs, URLs, file paths, message IDs, or API status).

## When to Use

- The user asks to read, write, search, or update data in a SaaS/service account.
- The task involves Google Workspace, Airtable, Notion, email via Himalaya, maps/geocoding/routes, Obsidian vaults, Hue lights, X/Twitter via `xurl`, Yuanbao group interaction, or comparable integrations.
- The task has side effects outside the local filesystem and needs credential/scope checks.

## Universal Rules

1. **Discover credentials before acting.** Check required env vars, config files, or CLI auth state without printing secrets.
2. **Prefer official CLIs when available.** Fall back to REST + `curl` or small Python clients only when the CLI is missing or insufficient.
3. **Verify writes.** Re-read the created/updated object, check API status, or inspect local files before claiming success.
4. **Avoid destructive ambiguity.** For deletes, bulk updates, or public posts, ensure the target is unambiguous.
5. **Return handles.** Final answers should include record IDs, URLs, paths, or command/API evidence.

## Service Playbooks

### Google Workspace

Use `gws` when installed for Gmail, Calendar, Drive, Docs, Sheets, and Contacts. Otherwise fall back to the bundled Python Google API client pattern. Run OAuth setup only when credentials are missing. For Gmail, use Gmail's search operators (`from:`, `to:`, `subject:`, `newer_than:`, `is:unread`) instead of broad local grep.

### Airtable

Use the REST API with a Personal Access Token. Minimum scopes are usually `data.records:read`, `data.records:write`, and `schema.bases:read`. Always URL-encode formulas/filters, paginate records, and use Airtable record IDs for updates/deletes.

### Notion

Use Notion's official `ntn` CLI when installed; fall back to HTTP + `curl`. Confirm integration token access to the target page/database. For page creation/update, respect Notion block-type constraints and re-read the resulting page/database entry.

### Email via Himalaya

Use Himalaya for terminal mailbox operations over IMAP/SMTP/Notmuch/Sendmail. Keep this distinct from Hermes' inbound email gateway. For composition, verify account, recipient, subject, and attachment paths before sending.

### Maps / location intelligence

Use open data sources: Nominatim for geocoding, Overpass for POIs, OSRM for routes, TimeAPI/timezone endpoints when needed. Respect rate limits and cache repeated lookups. For nearby searches, resolve the location first, then query categories.

### Obsidian

Treat the vault as a filesystem. Resolve `OBSIDIAN_VAULT_PATH` or the documented default before file operations. Use file search/read/patch tools rather than shelling out. Preserve wikilinks/frontmatter and avoid writing outside the vault.

### Philips Hue / OpenHue

Use OpenHue CLI on the same local network as the bridge. First pairing requires the physical bridge button; do not claim pairing can be completed remotely. Verify room/light IDs before changing scenes or state.

### X/Twitter via xurl

Use the official `xurl` CLI for posting, search, timelines, DMs, media upload, and raw v2 endpoints. Parse JSON responses and return tweet/message IDs. Confirm intent before public posts, deletes, follows, blocks, or DMs.

### Yuanbao groups

For Yuanbao gateway chats, normal assistant replies are the delivered message. Include `@nickname` in the reply text for gateway-managed mentions. Do not invent a separate send-message step unless a tool explicitly exists for that target.

## Verification Checklist

- [ ] Credentials/auth state checked without exposing secrets.
- [ ] The target account/workspace/vault/device/group is unambiguous.
- [ ] Read/list operations were paginated or scoped appropriately.
- [ ] Write/post/update operations were verified by re-read or API status.
- [ ] Final response includes exact handles and any unresolved permission/setup blocker.
