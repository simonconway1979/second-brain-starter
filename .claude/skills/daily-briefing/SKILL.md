---
name: daily-briefing
description: Shows what was imported into the wiki today. Use for /daily-briefing.
disable-model-invocation: true
allowed-tools: Read Write Glob
---

# Daily briefing

1. Read wiki/log.md and find the ingest lines dated today.
2. If there are none, say "Nothing was imported today." and stop.
3. List each imported file as a link to the file in raw/, with one line on what it is, taken from its source page.
4. Say how many wiki pages were created or changed.
5. Name one thing worth a look, with a link to the wiki page it came from.
6. Keep it under 150 words. Save it as briefs/YYYY-MM-DD.md and show it. Briefs are not sources: never ingest them.
