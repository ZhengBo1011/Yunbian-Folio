# Yunbian Folio (芸编) · English

A **local-first** personal library management app.

Capture books via camera scanning / manual entry / CSV import, enrich metadata automatically through a three-tier fallback chain (Douban → Open Library → Google Books), organize your collection on a three-pane bookshelf, and close the loop with reading status, lending, notes, and curated lists — all with WebDAV multi-device sync. **Your data always stays in your own hands.**

**Current platform**: native macOS (Swift/SwiftData).
**Roadmap**: a HarmonyOS edition (ArkTS) is in active development; Android, iOS, Windows and Linux are planned. All editions will stay in sync over WebDAV.

---

## ✨ Features

### 📚 Library Management

- **Three-pane bookshelf**: sidebar groups (All Books / Tags / Shelf Locations) + list + detail, desktop-grade information density
- **Three capture channels**:
  - Camera ISBN scanning with pre-granted permission flow
  - Manual entry with auto-completion
  - CSV bulk import (24-column template, preview before commit, per-row failure report)
- **Three-tier metadata enrichment**: Douban → Open Library → Google Books fallback chain; manual refresh & metadata lock supported
- **Rich bibliographic fields**: title / subtitle / authors / editors / translators / publisher / place / year / categories / page count / cover / source
- **Categories, tags & locations**: custom pickers with auto-registration; sidebar click-to-filter
- **Copy management**: multiple copies per book with condition, location, digital formats, price, purchase date, PDF notes and custom fields
- **ISBN de-duplication**: against live library and within import batches
- **Wishlist**: separate to-buy view with one-tap "purchased" conversion into the collection

### 📊 Statistics

- **Eight chart dimensions** (Swift Charts): overview / top categories / publication decades / top publishers / rating distribution / reading status share / shelf locations / intake timeline
- **AI insights slot**: coming soon (protocol already reserved)

### 📑 Curated Lists

- Themed collections with cover art from the earliest-added book
- Batch add from library or wishlist; entry timestamps preserved
- Deleting a list never touches the books themselves

### 📖 Reading Loop

- **Reading status**: Wish / Reading / Finished / Paused / Abandoned — all five labels customizable
- **Progress tracking**: page or percentage, automatic start/finish/last-read timestamps
- **Ratings**: 1–5 stars, inline in list rows
- **Notes**: attached to specific copies, 1000-character live counter
- **Toggles**: reading & rating UI can be hidden without losing data

### 📤 Lending Loop

- Lend a copy to someone with a date, get it back with one tap
- "Lent out" smart view with sidebar filter and counters

### 🔐 Data Safety

- **Full JSON backup / restore**: covers all 9 entity types (books / copies / locations / tags / notes / reading records / ratings / options / lists) **plus app preferences**; automatic pre-restore rollback snapshot; idempotent writes
- **Full data bundle (ZIP)**: library.json + library.csv + notes.json + booklists.json + README — one-click export/import, ideal for archival and migration
- **CSV export/import**: 24-column template (including ownership status / tags / reading status / rating / progress), fully backward compatible
- **Standalone notes & list backups**: structured JSON that can be re-imported and merged (newest-wins + tombstone-priority, same semantics as the sync engine); notes with no matching book are skipped and reported — no orphans
- **Quick exports**: current-view CSV and Markdown notes from the toolbar
- **Soft delete + sync tombstones**: deletions are traceable and sync-safe

### 🔄 Multi-Device Sync

- **WebDAV sync** with standard services (e.g. Jianguoyun/Nutstore): incremental sync + conflict merge + device identity
- Snapshot-based pipeline (protocol v1.2); backup/restore and sync share the same core, fully idempotent
- Sync covers all business data; device preferences (e.g. appearance) are intentionally local

### 🔍 Search & Sorting

- Global search across title / author / ISBN / tags / categories / notes / reading status
- Nine sort orders; quick filter chips; fault-tolerant ISBN matching
- Markdown notes export

### 🎨 Experience

- Appearance: System / Light / Dark, applied instantly
- Resilient cover pipeline (Douban hotlink workaround + two-level cache)
- 18 shelf-location icons; compact toolbar; keyboard shortcuts (⌘N capture, ⌘F search, Esc dismiss)

### 🚀 Roadmap

| Platform | Status |
|---|---|
| macOS (native) | ✅ Released — v0.2.3 |
| HarmonyOS (ArkTS/API26) | 🔄 In development |
| Android / iOS | 📋 Planned |
| Windows / Linux | 📋 Planned |

---

## Requirements

- macOS 14.0+
- Apple Silicon (arm64)

## Install

1. Grab the latest DMG (or ZIP) from [Releases](../../releases)
2. Open the DMG and drag **芸编** into Applications
3. First launch: if macOS asks for Keychain access, click **Always Allow** (only once per signing identity)

## Changelog

### v0.2.3 (build 12)

- **Settings CSV fixed**: reading status / rating / progress columns no longer blank; two new columns — Ownership (owned/wishlist) and Tags (22 → 24 columns); fully backward-compatible import
- **JSON backup completed**: book lists now included; snapshot protocol upgraded to v1.2 with a preferences block (appearance / feature toggles / reading labels) so a new device restores exactly as you left it
- **Standalone notes & list backups (new)**: structured JSON export/import with merge semantics identical to the sync engine (union + newest-wins + tombstone priority); unmatched books are reported, never orphaned
- **Full data bundle (new)**: JSON + CSV + notes + lists in one ZIP for archival and migration
- **Duplicate-location fix**: a single resolver now backs location creation across capture, purchase-conversion and copy-edit sheets — no more duplicate entries
- **UX fixes**: list-backup export button enables immediately after creating a list; bundle import failures no longer leave stale UI; unified date encoding across snapshots and backups
- Sync engine and protocol remain backward compatible (HarmonyOS v1.1 clients unaffected)

### v0.2.2 (build 11)

- Statistics (8 chart dimensions), curated lists + wishlist + purchase conversion, 18 location icons, Markdown notes export, enhanced search/sort/filter, soft-delete audit with regression tests, sync protocol v1.1

### v0.2.1 (build 10)

- UI polish, Settings center (appearance / toggles / custom reading labels), camera permission rewrite, list & copy fixes

### v0.2.0 (build 4)

- JSON backup/restore, CSV import/export, reading & lending loops, expanded search

### v0.1.0 (build 3)

- Three-pane shelf, three capture channels, three-tier metadata chain, WebDAV sync

## Feedback

Please file issues via [Issues](../../issues) with your macOS version and repro steps.

> 🇨🇳 [中文版 README](README.md)
