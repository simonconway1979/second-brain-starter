Rehanga Confluence · Product · Seller Experience · PRDs

# PRD: AI photo listing (Sell an item) · v3 final FINAL

| Property | Value |
|---|---|
| Owner | Maya Lindqvist (Senior PM, Seller Experience) |
| Squad | Seller Experience |
| Designers | Pedro Almeida (confirmation step, Flaws prompt), Inês Carvalho (review, DS) |
| Engineering lead | Daniel Okoro |
| Research | Lena Brandt |
| Legal | Catarina Moura (label wording) |
| Approver | Tomás Reis (pending) |
| Status | **For sign-off** · comments by Thu 29 Oct, end of day |
| Last updated | 29 October 2026 |

> Yes, the title is a joke. No, there will not be a v4. (Please.)

**Version history**

| Version | Date | What changed |
|---|---|---|
| v1 | 21 Sep | First draft, squad only. Mostly copied from the one-pager. |
| v2 | 23 Sep | Spike results, solution after the 16 Sep product review, metrics, timeline. |
| v3 | 28 Oct | Rewritten after Tomás's call on 19 Oct (no auto-post). Confirmation step, Flaws prompt, price suggestion, label wording from Legal, usability notes from 22 Oct, cost from Finance. Shared with Inês on 27 Oct evening first. |

---

## Background

**Too many new sellers never get their first item live.**

**38% of first-time sellers give up before their first listing goes live** (Q1 2026 seller dashboard). That's more than one in three people who opened "Sell an item", wanted to sell something, and left. Sellers who don't finish the first one almost never come back for a second.

The slowest part is writing. Sellers stare at an empty description box, write two words, delete them, and give up. In the March seller survey (n=1,840), **47% named the description as the most annoying step** of listing, more than any other step.

We already proved the flow moves when we remove boring work: the photo upload redesign took drop-off at the photo step from 19% to 12% (live since 3 March).

## Evidence

- **First-listing funnel (Amplitude, 1–27 Aug, first-timers only):** **41%** of the people who drop out do it on the description, 27% on price. A first listing takes **8m10s** (median), and 3m40s of that is the description box.
- **Pricing (Looker, first-time sellers, Mar–Aug listings):** first listings are priced a **median 19% under** the category median. Underpriced items go in 2 days instead of 9, and the sellers behind them list 40% fewer items over the next 90 days. Only about 31% of first-timers land within 10% of median.
- **Seller survey (Typeform, March):** 58% "don't know what to charge".
- **Spike round 2 (Daniel, 14 Oct):** 400 drafts at 2,048 px, all reviewed by support. Condition overstated in **124 of 400 (31%)**. Brand wrong in about 1 in 8.
- **Usability sessions (Lena, 22 Oct):** 8 sellers on Pedro's prototype. **5 of 8 confirmed a condition one level too high without changing it.** The three who changed it saw the Flaws slot light up; two of them added a flaw photo.
- **Buyer study (Lena, June, 12 buyers):** what buyers trust is how the seller themselves describes the condition, plus pictures of the flaws. **9 of 12** said knowing AI had written a listing would make them trust it less, unless the seller had confirmed it.
- **Competitor A:** "list from a photo" since May, about 90 seconds an item, with a "Created with AI assist" line on AI-written listings.

## Users

- **First-time sellers** (who we measure). First item, usually on the phone, often in the evening.
- **Repeat sellers** get it too.
- Not in scope: professional sellers on bulk upload.

## What changed since v2

So, basically: in v2 the draft went live as soon as the seller tapped "List item", and they could fix it afterwards. **That's gone.** On 19 Oct Tomás changed the call after round 2 (his post in #product-leads is the source, not this page). Nothing an AI drafted goes live until the seller has confirmed the condition themselves.

## Solution

**1. Photos, as today.** Grid, reorder, cover photo, the Flaws slot from DS 4.2. The draft call starts in the background as soon as the first photo is in.

**2. Dark photos.** We measure brightness on the device before the call. Below the line on SELL-1873, the draft still fills title, description, category and colour, but **we don't show a condition from the model at all.** The selector stays empty and the seller picks. Copy: "Your photos are a bit dark. Choose the condition yourself, or retake in daylight."

**3. The draft.** Title, description, category and colour filled in. Description tone plainer than the spike (Daniel: "less shop window"). No "authentic", "genuine" or similar words in anything the model writes, in any of the four languages.

**4. Condition: the seller confirms.** One tap, on the condition step, before "List item" is active. The seller can confirm the level or pick another. **No confirmation, no listing.** A pre-ticked box doesn't count and neither does editing after posting (Legal, 30 Sep and 21 Oct).
→ *How the selector looks before that tap is still open. See Open questions #1.*

**5. Flaws prompt (new in v3).** When the level the seller lands on is Good or Satisfactory, or we skipped the condition because of dark photos, we ask for a close-up of any wear in the Flaws slot: "Show buyers any marks or wear. A close-up helps." The seller can skip it with "Nothing to show". In Lena's sessions only the sellers who changed the level ended up adding a flaw photo, so the prompt has to come with the level, not after it.

**6. Price suggestion.** On the price step the seller sees what similar items go for (median price, matched on category, brand tier and condition) as a place to start: "Similar items sell for around €X". The field is pre-filled with it and the seller can change it. If we don't have enough sold items for that combination, no suggestion, field empty as today. *Tomás said this in September at product leads: for first-timers the price might matter more than the text.*

**7. Brand.** A suggestion chip only ("Looks like [brand]? Add it"). Never filled into the field, never written into the title or description, never stated as fact. Brand detection itself (SELL-1858) stays in Later.

**8. Label for buyers.** On the listing page, next to description and condition, Legal's wording exactly: **"Description drafted with AI, confirmed by the seller."** Catarina asked us not to shorten it and to see final screens before launch. The listing page is Buyer Experience code, so Nuno reviews SELL-1872.

**9. Fallback.** If the model fails or times out, the seller gets today's empty form. No label then.

### Requirements

| # | Requirement | Priority | Card | Notes |
|---|---|---|---|---|
| R1 | Background draft call from first photo | Must | — | 2.5–4 s per set in round 1 |
| R2 | Title, description, category, colour drafted | Must | 1854/55/56/69 | Plainer tone |
| R3 | Condition drafted, passed into the confirmation step | Must | SELL-1857 | |
| R4 | Seller confirms condition before publish | Must | SELL-1870 | Merged behind flag 29 Oct |
| R5 | Auto-post path removed from code | Must | SELL-1874 | Daniel |
| R6 | Dark-photo state: no model condition | Must | SELL-1873 | Brightness line is Hugo's guess from round 2 evening rows |
| R7 | Flaws prompt on Good / Satisfactory / dark | Must | SELL-1875 | Pedro, Hugo |
| R8 | Price suggestion from category median | Should | SELL-1876 | Median source tbc |
| R9 | Brand as chip only | Must | — | Already the case in the draft fields |
| R10 | Buyer-facing AI label, Legal's wording | Must | SELL-1872 | Buyer Exp review (Nuno) |
| R11 | Fallback to empty form | Must | — | |
| R12 | Events: drafted / confirmed unchanged / changed, per field | Must | — | For the claims guardrail |

## Success measures

| Measure | Baseline | Target | Source |
|---|---|---|---|
| First-listing completion (KR1) | 66% (Aug) | **+15%** | Amplitude |
| "Not as described" claims on AI-assisted listings | Same rate on listings made without the AI draft, same weeks | **No higher than baseline** | Zendesk → new BI tool |
| First-time sellers priced within 10% of category median (KR3) | ~31% | **Within 10% of median** | Looker / new BI tool |
| Condition changed at the confirmation step | — | Watch only | Events (R12) |

The claims measure is a guardrail and sits next to KR2. If AI-assisted listings come in above baseline for two weeks running, we stop and look before going wider. *Sofia to confirm the baseline definition.*

## Cost

**€0.011 per listing** at our volume tier and 2,048 px photo sets (Finance, vendor quote via procurement, 16 Oct). v2 had €0.004, but that came from the spike: list price, smaller photos (1,024 px), a small run. Not the same thing. Monthly volume for procurement: Daniel and Ana Ribeiro.

## Risks

- **Sellers tap through.** Lena's 5 of 8. The Flaws prompt and the selector question (#1) are our answer so far. We'll know more from the events after launch.
- **Dark-photo line is a guess.** Hugo's own words. Revisit after two weeks of data.
- **Buyer Experience review** for the label lands in their cut-over week.
- **Translation** of the label and the Flaws prompt: TBD.
- Claims: covered by the guardrail above.

## Open questions

1. **Selector before the tap:** AI level pre-selected (what we tested), shown as a hint next to an empty selector, or empty? Pedro has drawn the empty and hint variants. Possibly a second round with Lena (she needs a week to recruit).
2. Label wording in PT, ES, FR, IT: who signs off each language? *Maya to ask Catarina.*
3. Price suggestion: where does the median come from once Looker is read-only (30 Nov)? Who owns that number?
4. Launch order by market: TBD.

## Timeline

| Step | When | Owner |
|---|---|---|
| Confirmation step (SELL-1870) | Thu 29 Oct ✅ merged behind flag | Ana, Pedro |
| Auto-post removal, dark-photo, label | before 6 Nov | Daniel, Hugo, Maya |
| Flaws prompt | before 6 Nov | Pedro, Hugo |
| Everything behind the flag | **before the freeze, Mon 9 Nov** | Daniel |
| Sign-off | Fri 30 Oct | Tomás |
| Rollout comms | TBD | |

## Decision log

| Date | Decision | Who |
|---|---|---|
| 3 Sep | Vision vendor passed AI review | Marco's review, via Daniel |
| ~~16 Sep~~ | ~~AI draft posts without a separate review step; seller can edit after~~ | ~~Tomás, product review~~ (replaced 19 Oct) |
| 16 Sep | Brand stays a suggestion | Product review |
| 19 Oct | No auto-post. Seller confirms condition in one tap; AI text labelled | Tomás, product leads + #product-leads |
| 21 Oct | Label wording | Catarina Moura, email |

---

**Comments**

**Inês Carvalho** · 28 October 2026
+1. Small one on the Flaws prompt: "marks or wear" reads fine in English, please check it doesn't become "damage" in PT. Sellers hate that word.

**Joana Pires** · 28 October 2026
How is the baseline for the claims measure picked? Same categories, same weeks? When the title test was paused on 2 October 2025, the weeks after went on arguing about which listings it had been compared with. Please write it down before launch, not after.

**Lena Brandt** · 28 October 2026
Thank you for citing the sessions. Small correction to keep with the number, if possible: 8 participants, all with items they rated Good, and the draft was always one level too high. In our sample 5 of 8 confirmed it unchanged. It is not a rate for the real flow.

**Maya Lindqvist** · 28 October 2026
@Lena added to Risks, thank you! @Joana I'll write it with Sofia this week.

**Daniel Okoro** · 29 October 2026
Cost section is right. Still the cheapest line on this page.

**Rui Almeida** · 29 October 2026
Section 6 / R8 (price suggestion): Pricing has this from today, card moved to me. For my dependency list I need: (1) the data source for the category median after 30 Nov, (2) who owns that number in the new BI tool, (3) who answers sellers who think the suggestion is wrong (support macro?), (4) its own flag, separate from the AI draft (agreed in the sync this morning). I'll set up a short slot.

**Maya Lindqvist** · 29 October 2026
Thanks Rui! I'll update the page and the requirements table.
