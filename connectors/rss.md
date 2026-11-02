# RSS connector

Any blog or newsletter with a feed. No login.

## Connect

Ask for a feed link. If they have none, offer `https://simonwillison.net/atom/everything/`. Fetch it with `curl -sL "<link>"`, using GET only. Don't use a tool that summarises the page. Save the link as `feed` in the state file.

What the tool can do: read a public web page. Nothing else is needed.

## Fields

| Standard field | From the feed |
|---|---|
| `source` | `rss` |
| `date` | `published`, or `pubDate`, or `updated` |
| `from` | The author, or the feed's title |
| `permalink` | The item's link |
| `title` | The item's title |

For `<id>`, use the last part of the item's link, or of its `id` or `guid`, as a short slug. Add `feed: "<feed title>"` below the seven fields.

## Quirks

- The body is the item's `content`, or else its `description` or `summary`. Convert HTML to plain Markdown, and change no words.
- Many feeds only carry an excerpt. Keep what the feed gives you, and don't fetch the full page.
