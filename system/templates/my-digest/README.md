# My Digest

Your quick "what's going on in my Google" catch-up. It looks at your recently changed Google Drive
files (and today's calendar, if connected), then writes you a short, friendly summary.

## How to run it

Just say **"catch me up"** (or run the `catch-me-up` skill). The assistant follows `routine.md`.

## What it does

1. Reads your ~8–10 most recently changed Google Drive files (read-only).
2. If Google Calendar is connected, adds today's events.
3. Writes the summary to `digest-<YYYY-MM-DD>.md` in this folder.
4. Shows it to you and offers to open or summarize anything.

It only **reads** your Google and writes a **local** note here — nothing in Google is changed.

## Make it yours

This is *your* project — tweak `routine.md` however helps. Want it to also skim your recent email, or
draft a to-do list from what it finds? Say **"level up"** and we'll grow it. Want to actually **edit**
Google Sheets & Docs from here (not just read)? Say **"level up google"**.
