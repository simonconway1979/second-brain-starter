# Build your first agent

An agent is an instructions file plus a trigger. Walk them through this in short, plain messages. Where a stage says **Stop**, end your message and wait.

## Stage 1: pick the job

Say: "Your first agent is a brief. It reads what changed in your wiki and tells you what matters. Who is it for, and what should it look out for? One line is fine, or say 'just me'."

**Stop.**

## Stage 2: write it

Create `agents/brief.md` with these instructions, adding their answer as the audience and focus:

```
# Brief agent

For: [their answer]

1. Read wiki/log.md and find the entries from the last 7 days.
2. Read the wiki pages those entries touched, and the index.
3. Write a brief of under 150 words: what changed, why it matters, and one thing to do next.
4. Name the wiki page behind each point. If the wiki doesn't support a point, leave it out.
5. Save it as briefs/YYYY-MM-DD.md and show it. Briefs are not sources: never ingest them.
```

If you are Claude Code, also create `.claude/skills/brief/SKILL.md`:

```
---
name: brief
description: Writes a short brief on what changed in the wiki. Use for /brief.
disable-model-invocation: true
allowed-tools: Read Write Glob
---

Read `agents/brief.md` and follow it.
```

## Stage 3: run it

Follow `agents/brief.md` now and show the brief.

Then say: "That's your third layer. An agent is an instructions file plus a trigger: open agents/brief.md and you can read all of it. To run it again, type /brief, or ask me to schedule it every Friday."

## Stage 4: keep it going

Say: "Pick one source that comes in every week. Put 10 minutes in your calendar each Friday: add the files to raw/, type /capture, then /brief."
