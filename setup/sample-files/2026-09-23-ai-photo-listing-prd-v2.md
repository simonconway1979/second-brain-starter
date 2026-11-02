Rehanga Confluence · Product · Seller Experience · PRDs

# PRD: AI photo listing (Sell an item) · v2

| Property | Value |
|---|---|
| Owner | Maya Lindqvist (Senior PM, Seller Experience) |
| Squad | Seller Experience |
| Designers | Inês Carvalho, Pedro Almeida |
| Engineering lead | Daniel Okoro |
| Approver | Tomás Reis (pending) |
| Status | Draft v2 · for comment until Fri 25 Sep |
| Last updated | 23 September 2026 |

**Version history**

| Version | Date | What changed |
|---|---|---|
| v1 | 21 Sep | First draft, squad only. Mostly copied from the one-pager. |
| v2 | 23 Sep | Spike results added, solution updated after the 16 Sep product review, metrics, timeline. Shared with Tomás. |

---

## Problem

**Too many new sellers never get their first item live.**

**38% of first-time sellers give up before their first listing goes live** (Q1 2026 seller dashboard). That's more than one in three people who opened "Sell an item", wanted to sell something, and left. Sellers who don't finish the first one almost never come back for a second.

The slowest part is writing. Sellers stare at an empty description box, write two words, delete them, and give up. In the March seller survey (n=1,840), **47% named the description as the most annoying step** of listing, more than any other step.

We already proved the flow moves when we remove boring work: the photo upload redesign took drop-off at the photo step from 19% to 12% (live since 3 March).

## Evidence

- **Funnel (Amplitude, first-time sellers, 1–27 Aug 2026):** of the sellers who drop out, **41% go at the description step**, 27% at price. Median time to publish a first listing is **8m10s**; the description step alone is 3m40s. [link: amplitude/rehanga/funnels/first-listing-aug26]
- **Seller survey (Typeform, March 2026):** description is the most annoying step for 47%; 58% "don't know what to charge".
- **Competitor A** launched "list from a photo" in May. About 90 seconds per item according to their own numbers (trade-press piece, 1 Sep, clipped in Notion). Board asked in May where ours is.
- **Spike (Daniel, 16 Sep):** a vision model can draft most of the fields from the photos we already get. See Engineering check below.
- Seller interviews (Dovetail, 2024): sellers want speed above everything, "I'd let it write everything". Buyer study (Lena, June 2026): buyers look at the seller's own words and the flaw photos. *TODO: Lena to check I've summarised her study right.*

## Users

- **First-time sellers** (main target). First item, usually from their phone, often in the evening, usually a clothing item they've worn.
- **Repeat sellers.** Will get it too, but not who we're measuring.
- Not in scope: professional sellers using bulk upload.

## Goals and success metrics

**Goal:** more first-time sellers get their first item live, faster.

| Metric | Baseline | Target | Source |
|---|---|---|---|
| First-listing completion (Q4 KR1) | 66% | **+15%** relative | Amplitude, first-listing funnel |
| Median time to publish, first listing | 8m10s | Under 3 min | Amplitude |
| Description step drop-off | 41% of drop-offs | Halve it | Amplitude |
| "Not as described" claims on AI-drafted listings | tbc (Sofia's dashboard) | Monitor | Zendesk / Looker |

Guardrail: we watch claims on AI-drafted listings weekly from launch. No target set; to be agreed with Sofia once the Q4 OKRs are final.

## Scope

**In v1**
- AI draft of title, description, category, colour and condition from the seller's photos
- Brand shown as a suggestion the seller can accept or ignore (never filled in silently)
- Dark-photo warning before the draft is made
- Draft posts straight away; seller can edit after it's live
- Works in all four markets, all four languages

**Out of scope for v1**
- Price suggestion (58% "don't know what to charge" is real, but it's its own project. Talk to Rui now he's on pricing.)
- Multi-item photos (a pile of clothes in one shot)
- Accessories and jewellery categories (spike didn't test them)
- Bulk upload

## Solution outline

So basically the "Sell an item" flow stays the same shape, it just isn't empty when you get to it.

1. **Photos.** Seller adds photos as today (grid, reorder, cover photo, the Flaws slot from DS 4.2 stays as it is). As soon as the first photo is in, we send the set to the model in the background, so the seller doesn't wait.
2. **Dark-photo warning.** If the photos are too dark, we show a short warning before we draft: "Your photos look a bit dark. Retake for a better listing?" Seller can retake or continue.
3. **Draft.** Title, description, category, colour and condition are filled in. Brand appears as a suggestion chip ("Looks like: [brand]? Add it"), not in the field.
4. **Post.** Seller adds a price and taps "List item". The draft goes live as it is. As agreed in the product review on 16 Sep, we don't add a separate review screen: under the Trust & Safety policy the seller is responsible for their listing's accuracy, and an extra step costs us the completion we're trying to win.
5. **Edit after posting.** After posting, the seller lands on the listing with a clear "Edit" entry point (Pedro's post-publish edit screen, in progress).

Design: Inês and Pedro. Screens in Figma, flow spec to follow. *Inês is also sketching a review-before-posting screen as an option; not in this version.*

### Requirements

| # | Requirement | Priority | Notes |
|---|---|---|---|
| R1 | Model call starts when the first photo is added, runs in background | Must | 2.5–4 s per photo set in the spike |
| R2 | Title, description, category, colour drafted | Must | Description tone: plainer than the spike's ("too salesy", Daniel) |
| R3 | Condition drafted from photos | Must | Spike: OK in good light, weaker in poor light; see R5 |
| R4 | Brand as suggestion only, never auto-filled | Must | Spike: brand unreliable with no label visible |
| R5 | Dark-photo warning | Must | Threshold tbc with Daniel |
| R6 | Draft posts without a separate review step | Must | Product review 16 Sep |
| R7 | Post-publish edit screen | Should | Pedro |
| R8 | Label that AI helped write the listing | tbc | Legal to confirm whether needed (see Open questions) |
| R9 | Fallback: if the model fails or times out, seller gets today's empty form | Must | |
| R10 | Event tracking for every drafted field: accepted / edited | Must | For the claims guardrail |

## Risks

- **Condition in poor light.** The spike rated items better than they are on dim photos. The dark-photo warning should catch most of it. *TBD with Inês: what else?*
- **Brand.** Covered by R4.
- **Capacity.** Hugo and Ana are on checkout hardening until next week. Every week they're out comes off the end of the timeline.
- **Claims.** TBD
- **Translation quality** in FR and IT: not tested in the spike.

## Open questions

1. If the model has already guessed a condition, what does the selector show? (Open since the design brief, 2 Sep.) Pre-selected, or a hint next to it?
2. Do we need to label AI-drafted text? Legal note from July says something about this. *Maya to ask Catarina.*
3. Dark-photo threshold: who decides, and from what data? (Hugo has evening photo numbers.)
4. Do we show the brand chip in all categories or only where the spike was good?
5. ~~Which vendor?~~ Done, passed AI review on 3 Sep.

## Engineering check

From Daniel's spike write-up (16 Sep, [Confluence](../confluence/2026-09-eng-note-vision-model.md)):

| | Spike result |
|---|---|
| Sample | 600 recent listings, 150 reviewed by two support agents |
| Cost | ~€0.004 per listing at current pricing |
| Latency | 2.5–4 s per photo set |
| Category, colour, title | Good |
| Description | Good but generic, a bit salesy |
| Brand | Unreliable, confident wrong answers |
| Condition | Reasonable in good light, weak in poor light |
| Effort to productionise | ~2 sprints |

At around a million orders a month, the cost is small either way. Daniel to confirm the vendor's volume pricing before launch.

## Timeline

| Step | When | Owner |
|---|---|---|
| PRD v2 comments | by Fri 25 Sep | everyone |
| Hugo and Ana back on Seller | Mon 28 Sep (tbc) | Daniel / Tomás |
| Sizing | week of 28 Sep | Daniel |
| Build (2 sprints) | October | Seller squad |
| Live, all four markets | **before the code freeze, Mon 9 Nov** | Maya |

If the engineers come back later than the 28th, it gets very tight. We need about two weeks after build for QA and the language checks.

## Decision log

| Date | Decision | Who |
|---|---|---|
| 3 Sep | Vision vendor passed AI review | Marco's review, via Daniel |
| 16 Sep | AI draft posts without a separate review step; seller can edit after | Tomás, product review |
| 16 Sep | Brand stays a suggestion | Product review |

---

**Comments**

**Inês Carvalho** · 23 September 2026
R3 + R6 together mean the seller can post a condition they haven't looked at. Is that what we want? Not saying no. Asking.

**Daniel Okoro** · 23 September 2026
Timeline assumes I get both of them back on the 28th and nobody borrows them again before November. Putting that on record.

**Maya Lindqvist** · 23 September 2026
@Inês let's talk tomorrow at lunch? 🙂 @Daniel noted, it's in Risks.
