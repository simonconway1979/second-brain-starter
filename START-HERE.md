# Your second brain

Three parts. Raw files you never edit. A wiki the AI writes and keeps current. One instructions file that tells it how. You add files. The AI does the filing.

The method is Andrej Karpathy's LLM Wiki: https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f

**You need:** Claude Code or Codex, installed and logged in.

## 1. Open this folder

Open Claude Code or Codex in this folder.

## 2. Set it up

Paste this:

```
Read setup/set-up.md and follow it.
```

It asks what you want the wiki for, and whether to use your own files or the sample files. Then it writes the instructions file. Read it when it's done: that's your rulebook.

## 3. Ingest one file

```
Ingest raw/[file name]. Tell me which wiki pages you created or changed, and why.
```

Open a page it wrote. Does it link back to your raw file? If not, tell it to.

## 4. Ingest the rest, and make it yours

```
Ingest the other files in raw/, one at a time. Follow the rules in the instructions file. Update the index and the log after each one.
```

While it runs, open the instructions file and change one rule so it fits what you want.

## 5. Ask it

```
[Your question]. Answer from the wiki, and name the raw file behind each point.
```

Ask something you'd normally dig for. Then ask: where did that come from? It should name a real file.

## 6. Keep it going

Pick one source that comes in every week, like your meeting notes. Put 10 minutes in your calendar each Friday. Add the week's files, ingest them, then run this:

```
Lint the wiki. Look for contradictions, stale claims, pages with no links, and claims with no source. Fix what you can, and list what needs me.
```
