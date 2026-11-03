# Build your first agent

Your first agent is a daily briefing. Don't ask any questions first. Keep every message short, in plain words. Don't add a recap, a status note or a next-step box.

## Step 1: write it

Create `agents/daily-briefing.md` with exactly this:

```
# Daily briefing

1. Read wiki/log.md and find the ingest lines dated today.
2. If there are none, say "Nothing was imported today." and stop.
3. List each imported file as a link to the file in raw/, with one line on what it is, taken from its source page.
4. Say how many wiki pages were created or changed.
5. Name one thing worth a look, with a link to the wiki page it came from.
6. Keep it under 150 words. Save it as briefs/YYYY-MM-DD.md and show it. Briefs are not sources: never ingest them.
```

If you are Claude Code, also create `.claude/skills/daily-briefing/SKILL.md`:

```
---
name: daily-briefing
description: Shows what was imported into the wiki today. Use for /daily-briefing.
disable-model-invocation: true
allowed-tools: Read Write Glob
---

Read `agents/daily-briefing.md` and follow it.
```

## Step 2: show it

Show the contents of `agents/daily-briefing.md`, with a link to the file. Say: "This is the whole agent: an instructions file plus a trigger."

## Step 3: run it

Follow `agents/daily-briefing.md` now and show the briefing.

## Step 4: finish

Say: "That's all three layers: capture, memory and agents. To run this again, type /daily-briefing, or ask me to run it every morning."
