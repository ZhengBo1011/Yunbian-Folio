# Yuntai Folio (芸台)

A **local-first** personal library management app.

Capture books via camera scanning / manual entry / CSV import, enrich metadata automatically through a three-tier fallback chain (Douban → Open Library → Google Books), organize your collection on a three-pane bookshelf, and close the loop with reading status, lending, notes, and curated lists — all with WebDAV multi-device sync. **Your data always stays in your own hands.**

**Current platform**: native macOS (Swift/SwiftData), **v1.1.0(3)**; a native **Windows edition v1.0.0 is complete and launching soon**.
**Roadmap**: a HarmonyOS edition (ArkTS) is in active development; Android and iOS are planned. All editions will stay in sync over WebDAV.

> 📖 **[中文版 README](README.md)**
> 📦 **Download**: grab the latest DMG / ZIP from [Releases](../../releases)

---

## ✨ Features

### 📚 Library Management

- **Three-pane bookshelf**: sidebar groups (All Books / Tags / Shelf Locations) + list + detail
- **Three capture channels**: camera ISBN scanning, manual entry with auto-completion, CSV bulk import (23-column template with preview and per-row failure report)
- **Three-tier metadata enrichment**: Douban → Open Library → Google Books fallback chain; manual refresh & metadata lock supported
- **Rich bibliographic fields**: title / subtitle / authors / editors / translators / publisher / **second publisher** (co-publishing) / place / year / categories / page count / cover / source
- **Tags = category options**: managed in Settings → Field Options; sidebar click-to-filter; both publishers counted in publisher statistics
- **Copy management**: multiple copies per book with condition, location, digital formats, price, purchase date and custom fields; choosing N locations on capture creates N copies automatically
- **ISBN de-duplication**: against live library and within import batches
- **Wishlist**: separate to-buy view with one-tap "purchased" conversion
- **Unshelved view**: a pinned sidebar entry that surfaces books without any shelf location

### 📊 Statistics

- **Eight chart dimensions** (Swift Charts): overview / categories / publication decades / publishers / ratings / reading status / shelf locations / intake timeline
- **Full entries**: category, publisher and location dimensions list every entry (no Top-10 truncation), with scrolling and search for long lists
- **AI insights slot**: coming soon

### 📑 Curated Lists

- Themed collections with cover art from the earliest-added book
- Batch add from library or wishlist; deleting a list never touches the books themselves

### 📖 Reading Loop

- **Fully custom reading statuses**: name and count them your way (up to 20; the built-in "Reading" cannot be deleted); reorder, edit, and clear back to "not set" anytime
- **Ratings**: 1–5 stars, inline in list rows
- **Notes**: attached to specific copies, 1000-character live counter
- **Toggles**: reading & rating UI can be hidden without losing data

### 📤 Lending Loop

- Lend a copy with a borrower and date, get it back with one tap
- "Lent out" sidebar view with counters

### 🔐 Data Safety

- **Full JSON backup / restore**: all entities **plus app preferences**; automatic pre-restore rollback snapshot; idempotent writes
- **Full data bundle (ZIP)**: library.json + library.csv + notes.json + booklists.json — one-click export/import for archival and migration
- **CSV export/import**: 23-column template (ownership / tags / reading status / second publisher included), fully backward compatible
- **Standalone notes & list backups**: structured JSON re-import with newest-wins + tombstone-priority merge
- **Quick exports**: current-view CSV and Markdown notes from the toolbar
- **Soft delete + sync tombstones**: deletions are traceable and sync-safe

### 🔄 Multi-Device Sync

- **WebDAV sync** with standard services (e.g. Jianguoyun/Nutstore): incremental sync + conflict merge + device identity
- Snapshot-based pipeline (**protocol v1.3**, including custom reading-status options); backup/restore share the same core
- Device preferences (appearance / language) stay local by design

### 🔍 Search & Sorting

- Global search across title / author / ISBN / tags / categories / notes / reading status
- Nine sort orders; quick filter chips; fault-tolerant ISBN matching

### 🎨 Experience

- **UI language**: Follow System / 简体中文 / English, switchable in Settings (restart to apply); system menus follow the OS language
- Appearance: System / Light / Dark, applied instantly
- Resilient cover pipeline (Douban hotlink workaround + two-level cache)
- 28 shelf-location icons; keyboard shortcuts (⌘N capture, ⌘F search, Esc dismiss)
- Adaptive text display: narrow panes degrade gracefully, badges never wrap

### 🚀 Roadmap

| Platform | Status |
|---|---|
| macOS (native) | ✅ v1.1.0(3) |
| Windows (native) | 🔜 v1.0.0 complete, launching soon |
| HarmonyOS (ArkTS/API26) | 🔄 In development |
| Android / iOS | 📋 Planned |

### 🔮 Software Roadmap

- **Windows launch**: the native Windows edition v1.0.0 is complete — first public release coming soon
- **Multi-device sync GA**: HarmonyOS ↔ macOS two-way WebDAV sync graduating to stable, then Android / iOS joining the same protocol, with Windows converging next
- **PDF e-book reading & management**: e-copies become first-class readable assets with a built-in reader and integrated progress & notes
- **AI reading insights**: one-click reading reports based on your library
- **Cloud cover sidecar**: covers synced via a dedicated WebDAV folder
- Ongoing polish: more statistics dimensions, batch tools, full i18n

---

## Requirements

- macOS 14.0+
- Apple Silicon (arm64)

## Install

1. Grab the latest DMG (or ZIP) from [Releases](../../releases)
2. Open the DMG and drag **芸台** into Applications
3. First launch: if macOS asks for Keychain access, click **Always Allow** (only once per signing identity)
4. Upgrading: install over the old version — data migrates automatically (a JSON backup beforehand is recommended)

## Changelog

### v1.1.0(3) (build 18)

- **Reading-status badge restored** in book rows (title-right, single-line capsule)
- **Fixed middle column jumping to top** after editing status/rating/notes in the detail pane
- **Detail pane**: "Reading" section renamed "Reading Status" with a new **Clear Status** button
- **UI language setting**: Follow System / 简体中文 / English; system menus now localized with the OS language
- **Second publisher** field across capture/edit/detail/CSV/sync/statistics
- **Sidebar Tags = category options**, moved below Shelf Locations
- Fixed multiple same-named app copies appearing in the system

### v1.1.1 (build 16)

- Sidebar Tags switched to category options (unified with capture categories)
- Second-publisher field & statistics; CSV template 22→23 columns (backward compatible)

### v1.1.0 (build 15) — Renamed to Yuntai

- **App renamed**: 芸编 → 芸台 (English name Folio unchanged); data and sync identity untouched — install over the old version
- **Reading status rework**: fully custom statuses (up to 20, built-in "Reading" pinned); progress tracking removed
- **Tag system**: persistent sidebar section + tagging in the edit sheet + six default categories on first launch
- **Unshelved** sidebar entry; **28 location icons**; **full statistics lists** (no Top-10 cut); right pane follows sidebar/list selection; multi-location capture creates one copy per location; software info & feedback email in Settings; **sync protocol v1.3**

### v1.0.1 (build 14)

- Fixed CSV bulk import order for wishlist books (no more wrong copies)
- External metadata category sanitization

### v1.0.0 — Stable (build 13)

First stable release: text display system rework, sync reliability upgrades (immediate commit, manual/auto decoupling).

### Earlier versions

- **v0.2.3**: CSV fixes + ownership/tags columns; JSON backup completed; standalone notes/list backups; full data bundle; duplicate-location fix
- **v0.2.2**: 8-dimension charts; curated lists + wishlist + purchase conversion; 18 location icons; Markdown notes export
- **v0.2.1 (public beta)**: Settings center; camera permission rewrite; list & copy fixes
- **v0.2.0**: JSON backup/restore; CSV import; reading & lending loops
- **v0.1.0**: first test build — three-pane shelf, three capture channels, WebDAV sync

## Feedback

Please file issues via [Issues](../../issues) with your macOS version and repro steps, or email anbh1011@163.com.

---
