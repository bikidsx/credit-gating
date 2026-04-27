# Output Template: The Final Report

The deliverable from this skill is a Markdown report saved to disk. Use this exact structure. Do not add em dashes.

---

# Monetization Map: [Product Name]

**Prepared on:** [date]
**Analysis basis:** [codebase / PRD / pitch / verbal description]

## 1. Product summary

One paragraph capturing what the product does, who it serves, what it produces, and what the aha moment is. This is the orientation for any reader.

## 2. Cost reality

A short section listing what costs the company money per use. This is the anchor for everything that follows. Be specific:

- LLM calls and which models
- GPU or compute jobs
- Third-party paid APIs
- Storage and bandwidth (if material)
- Human-in-the-loop costs (if any)

If the company does not yet know their cost-to-serve numbers, say so. Do not pretend to know what cannot be known yet.

## 3. Capability inventory and bucket assignments

A table listing every capability with its scores and bucket. This is the heart of the report.

| Capability | Cost | Freq | Aha | Habit | Net | Dist | Outcome | Sub | Bucket | Notes |
|---|---|---|---|---|---|---|---|---|---|---|
| Generate first project | 4 | 4 | 5 | 3 | 1 | 3 | 4 | 3 | B (drip) | Aha-essential, high cost. Free with daily allowance. |

Use single-letter abbreviations in the headers to keep the table readable. After the table, write a paragraph explaining the routing for the most consequential 5 to 8 capabilities. Do not explain every row in prose; the table speaks for itself for the routine ones.

## 4. Recommended free tier shape

Describe what a free user can do, written as a user story. Example:

"Free users can describe an app, see Lovable generate a first version, deploy it to a public URL, and share it with friends. They get 5 credits per day, which is enough to make several small edits or one significant feature change. After they hit the daily cap, they see a clear upgrade prompt with the exact number of credits the next plan would have given them."

The free tier should let a user reach the aha moment, form a habit, and bring others in. It should not let them ship a production app.

## 5. Recommended paid tier shape

Tier the paid plans. Three tiers is usually the sweet spot. For each tier, state:

- The price point (rough order of magnitude is fine, exact pricing is a separate exercise)
- The credit allowance
- The tier-gated features unlocked
- The target persona

Do not invent enterprise features the product does not need yet.

## 6. The credit unit

State explicitly:

- What one credit represents in user-facing terms.
- What actions cost how many credits, in a small price list.
- What the rollover and expiration policy is.

If the natural unit is "messages" or "minutes" rather than abstract credits, recommend that. Pricing in raw tokens is forbidden for end-user products.

## 7. What stays free, on purpose

A short list of capabilities that are deliberately free even though some of them cost something to serve. Explain why for each one. This section exists because founders often try to gate things that should not be gated, and an explicit "do not gate this" list pre-empts that mistake.

## 8. Top three risks

The three most likely failure modes of this monetization plan. Examples:

- "If GPT-4 pricing drops 50 percent, the credit math becomes too generous and customers will demand more credits per dollar."
- "Power users on the Pro plan will hit the credit ceiling within two weeks. Need a Pro+ tier or auto top-up."
- "Free users may abuse the daily drip to ship full apps without paying. Add a per-project quota in addition to the daily credit drip."

For each risk, name the early warning signal and the mitigation.

## 9. Migration plan (only if the product already has pricing)

If the user is changing pricing rather than designing it from scratch, address change management explicitly:

- Who is grandfathered, on what terms, for how long.
- How the change is announced.
- What the median user impact is in dollars per month.
- What the worst-case user impact is.
- How customer success will handle the angry replies.

The Cursor and Replit backlashes happened not because the new pricing was wrong, but because the change was announced badly. Plan for this.

## 10. Open questions

A short list of things the user needs to figure out before this plan can ship. Examples:

- What is the actual cost-to-serve per agent task?
- What is the willingness-to-pay among the target persona?
- Are there competitor moves that would force a re-tier?

This section signals that the report is a starting point, not a final answer.

---

## Style notes for the report

- Lead with the answer in each section. No throat-clearing.
- Concrete numbers where possible. Dollar amounts, credit counts, percentages.
- No em dashes. Use commas, semicolons, colons, parentheses, or a sentence break.
- Write to the founder, not to a pricing committee. Plain language.
- Use the case studies from `case-studies.md` as analogies sparingly. Once or twice in the report is fine.
- The report should be readable in 10 minutes. If it is longer than that, cut.
