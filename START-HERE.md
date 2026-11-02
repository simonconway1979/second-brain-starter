# Your second brain

Three parts. Raw files you never edit. A wiki the AI writes and keeps current. One instructions file that tells it how. You add files. The AI does the filing.

The method is Andrej Karpathy's LLM Wiki: https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f

**You need:** Claude Code or Codex, installed and logged in.

## Set it up

Open Claude Code in this folder and type:

```
/setup
```

On Codex, paste this instead:

```
Read setup/set-up.md and follow it.
```

It takes you through the rest, one step at a time. It asks what the wiki is for, helps you add 5 files, then ingests them with you. Check its work after the first two. That's your memory layer.

## Connect a source

```
/connector
```

Pick a source and it walks you through collecting and testing. RSS needs no login. That's your capture layer. On Codex, paste `Read setup/connector.md and follow it.`

## Build an agent

```
/build-agent
```

It makes a first agent, `/brief`, which tells you what changed in your wiki and why it matters. That's your agent layer. On Codex, paste `Read setup/build-agent.md and follow it.`

## Keep it going

Pick one source that comes in every week, like your meeting notes. Put 10 minutes in your calendar each Friday. Add the week's files to `raw/`, then type:

```
/capture
```

It finds anything new and adds it to your wiki. Your files stay in `raw/` for good, because the wiki links to them. You can also paste text after `/capture`. On Codex, paste `Read setup/capture.md and follow it.`

Then run `/brief`. Now and then, run this:

```
Lint the wiki. Look for contradictions, stale claims, pages with no links, and claims with no source. Fix what you can, and list what needs me.
```

To ask it something:

```
[Your question]. Answer from the wiki, and name the raw file behind each point.
```
