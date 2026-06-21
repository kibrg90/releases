# AceLink — Releases

**AceLink** is a very lightweight **Android TV / Fire TV** app for browsing and playing
**AceStream** live channels. Point it at a source — a web page, an M3U playlist, a URL that
returns a playlist, or a direct `acestream://` link — and it scrapes the channel IDs, enriches
them via the on-device AceStream engine, and gives you a clean, D-pad-navigable channel grid you
can play with one click.

> This repository hosts **public release downloads only**. The source code lives in a separate
> private repository.

## 📥 Download

Grab the latest APK from the [**Releases**](https://github.com/kibrg90/acelink-releases/releases/latest) page.

Direct link to the current build:
**[acelink-v0.1.0.apk](https://github.com/kibrg90/acelink-releases/releases/download/v0.1.0/acelink-v0.1.0.apk)**

## 💿 Install (sideload)

AceLink is distributed as a sideloadable APK (it is **not** on the Google Play Store).

```bash
adb install -r acelink-v0.1.0.apk
```

- **Application id:** `com.acelink.app`
- **Min Android:** 7.1 (API 25 — Fire TV gen 1) · **Target:** Android 14 (API 35)
- Requires an on-device **AceStream engine** reachable at `127.0.0.1:6878`
  (install the AceStream app on the same device).

## ✨ Features

- **Add a source** — web-page URL, playlist URL, a bare host (`pimpletv.ru`), an M3U file, or a
  direct `acestream://` link; the right driver is auto-detected.
- **Channel index → picker** — index sites open a searchable, multi-select picker; only the
  channels you pick are crawled and imported.
- **Channel grid** — live status, logos (iptv-org), search, categories, A–Z fast-scroll,
  bookmarks, and a Recently-played row.
- **Backup mirrors + failover** — channels keep mirror IDs; the player warms a mirror, waits for
  the swarm, and (opt-in) fails over to the next-best by peer count.
- **Embedded playback** — Media3/ExoPlayer over the engine's raw MPEG-TS, or hand off to the
  AceStream app.
- **Manage** — rename / delete channels, re-scrape / delete sources, prune dead mirrors.

## 🔗 Possible sources

Paste any of these into **Add source** — the driver type is auto-detected:

- **acestreamid.com** — `https://acestreamid.com/`
  A large **channel index**: the page has no ids itself, but lists channels whose AceStream ids
  live on per-channel sub-pages. AceLink detects the index and opens the **channel picker**, then
  crawls only the channels you select.
- A **web page** containing `acestream://` links or 40-char content ids.
- A **playlist URL** or a local **`.m3u` / `.m3u8`** file.
- A single **direct link** — `acestream://<id>` or a bare 40-char content id.

---

_Personal / hobby project. No content is hosted — AceLink only browses and plays sources you add._
