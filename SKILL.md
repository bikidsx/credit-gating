---
name: credit-gating-analyzer
description: Analyze any product, codebase, PRD, or feature list to produce a defensible monetization map of what should be gated behind credits or tokens, what should sit behind a paid tier, and what must remain free. Use this skill whenever the user wants to figure out their pricing strategy, design a credit system, decide what to put behind a paywall, identify monetization opportunities, choose a value metric, audit an AI product for margin risk, or plan free-vs-paid feature splits. Trigger this even when the user phrases the request casually ("how should I charge for this", "what should be paid in my app", "what costs me money to run", "should this be free", "design my pricing"). Works on AI-native products, classic SaaS, vibe-coding tools, and anything in between.
---

# Credit Gating Analyzer

This skill helps a user decide three things about any project:

1. What to give away for free, on purpose
2. What to meter with credits or tokens
3. What to lock behind a paid tier

It is NOT a pricing calculator. It is a structured reasoning tool that takes whatever the user has (a codebase, a PRD, a feature list, a Figma, a half-baked idea) and produces a well-reasoned monetization map grounded in 2025 to 2026 industry research. Treat the output as a strategic recommendation, not a final pricing sheet.

## When this skill is the right tool

Use this skill when the user wants to know what to charge for. Do NOT use it for:

- Picking exact dollar amounts (that needs willingness-to-pay research)
- Building the actual billing system (that is a Stripe / Lago / Metronome implementation task)
- General SaaS strategy advice unrelated to gating

## Core philosophy this skill enforces

The skill operates from a few first principles drawn from the research foundation. Internalize these before doing the analysis. They are explained more fully in `references/research-foundation.md`.

1. **Gate power, not access.** Free users should be able to do the core job. Paid users should be able to do it faster, better, or at greater scale. Gating access kills adoption. Gating power drives upgrade.

2. **Credits exist for cost reasons, not greed reasons.** AI products have real variable costs (inference, GPUs, third-party APIs). Credits normalize that volatility into a predictable prepayment. Anything you charge credits for should have a cost-to-serve story. If a feature is near-zero marginal cost, charging credits for it is a hostile move that customers will resent.

3. **The aha moment must happen before any paywall.** If a user has not yet experienced the value, every gate is friction. If a user is hooked, gates feel like upgrades.

4. **Credits are a transitional architecture, not a destination.** The 2026 trajectory is toward outcome-based pricing (per resolution, per minute generated, per booking made). Credits are a stopgap that buys time while you learn what customers value. Design accordingly.

5. **Two different things get gated for two different reasons.** Variable-cost actions get metered with credits. Governance, collaboration, and premium-tier features get gated by plan. Do not confuse these two axes.

6. **Distribution beats extraction.** Things that pull new users in (sharing, embeds, MCP servers, public outputs, free APIs) almost always belong in the free tier even when they cost something to run, because the user-acquisition math beats the metering math.

## The workflow

Follow these phases in order. Do not skip ahead. Each phase has explicit outputs that feed the next one.

### Phase 1: Understand what you are looking at

Before reasoning about gating, get a real picture of the project. Ask the user (or read from artifacts) to answer:

1. **What is the product?** One paragraph in plain language.
2. **Who is the primary user?** Solo developer, marketing team, enterprise procurement, consumer, etc.
3. **What is the core job to be done?** The single sentence a user would say to describe why they opened the product.
4. **What is the aha moment?** The first 60 seconds that makes a user say "oh, this is useful". Do not proceed without this.
5. **What does the project produce?** Code, images, reports, decisions, conversations, automations, etc.
6. **What infrastructure costs real money to run?** LLM calls, GPU time, third-party APIs, storage, bandwidth, human review.
7. **What is the current pricing posture, if any?** Free, freemium, flat sub, hybrid, etc.

If the user uploaded a codebase, read it. Look at the package.json, requirements.txt, server routes, env vars, and especially anywhere that calls a paid external API. Those API call sites are nearly always credit candidates.

If the user uploaded a PRD or pitch, extract the feature list from it directly.

If the user gave only a verbal idea, ask focused questions to fill in the seven items above. Do not move on with gaps in items 3, 4, or 6.

### Phase 2: Inventory the capabilities

Make an exhaustive list of distinct capabilities the product offers (or will offer). A capability is anything a user can do or get out of the product. Think of it at the verb level: "generate report", "search archive", "invite teammate", "deploy app", "export PDF", "query model X", "schedule recurring run".

Aim for 15 to 40 capabilities for most products. Too few means the analysis is too coarse. Too many means you are listing UI elements, not capabilities. Group similar items.

Do not categorize them yet. Just inventory.

### Phase 3: Score every capability against eight dimensions

For each capability, score it 1 to 5 (1 is low, 5 is high) on the eight dimensions below. The full scoring rubric is in `references/decision-matrix.md`. Read that file before scoring; the rubric definitions matter.

1. **Cost-to-serve.** How much does each invocation cost the company in real money?
2. **Frequency.** How often does a typical engaged user invoke it?
3. **Aha-moment proximity.** How close is this capability to the first-time value experience?
4. **Habit formation.** Does using this make users come back tomorrow?
5. **Network value.** Does it get more valuable to others when one user uses it?
6. **Distribution pull.** Does it bring new users into the product (shares, embeds, public links, integrations)?
7. **Outcome attribution.** Can you cleanly measure the business value this delivers to the user?
8. **Substitution ease.** How easy is it for the user to do this elsewhere if you charge for it?

Do this scoring in a table. The table is the artifact that drives every downstream decision.

### Phase 4: Apply the gating decision rules

With the scored table, route each capability to one of four buckets using the rules below. The reasoning behind each rule is in `references/decision-matrix.md`.

**Bucket A: Free forever, no metering**
- Cost-to-serve is 1 or 2 AND
- (Aha-moment proximity is 4 or 5 OR Distribution pull is 4 or 5 OR Network value is 4 or 5)

These are the things you actively want users to abuse. The more they use them, the better your business does.

**Bucket B: Free with a daily or monthly drip**
- Cost-to-serve is 3 or higher AND
- Aha-moment proximity is 4 or 5

The user must experience this for the product to make sense, but it costs you money. Solve with a small daily allowance (Lovable's 5 free credits per day is the canonical example) so casual users feel welcome but power users hit a ceiling.

**Bucket C: Credit-metered**
- Cost-to-serve is 3 or higher AND
- Aha-moment proximity is 1, 2, or 3 AND
- Outcome attribution is moderate or higher

These are the variable-cost actions that scale with use. A credit should buy something the user can intuitively map to value. One credit per AI message (Lovable), per agent task (Replit), per render minute (Synthesia), per resolution (Decagon). Avoid pricing in raw tokens for end users; tokens are infrastructure jargon.

**Bucket D: Tier-gated (not credits)**
- Anything where the value is access, governance, scale, or trust rather than per-action consumption. SSO, audit logs, private deployments, custom domains, role-based access, multi-seat collaboration, premium support, brand removal, training-opt-out, longer history, higher rate limits, access to top-tier models.

Tier gates do not consume credits. They are entitlements. Mixing them up is the single most common pricing mistake.

Some capabilities legitimately straddle buckets. A capability can be in Bucket C (metered) AND Bucket D (only available on Pro+). That is fine. State both routings explicitly.

### Phase 5: Sanity-check against the failure modes

Before finalizing, run the recommendation through these five checks. If any fail, revise.

1. **Aha test.** Can a brand-new user experience the aha moment without paying or running out of credits? If no, you have over-gated.
2. **Margin test.** If a free user uses the free tier as much as humanly possible, does the company lose money? If yes, the daily drip is too generous or something free belongs in Bucket B.
3. **Intuition test.** Can a non-technical buyer explain in one sentence what one credit gets them? If no, the credit unit is wrong.
4. **Backlash test.** If you announced this scheme tomorrow on Hacker News, what is the most likely angry comment? Pre-empt it. (Cursor and Replit both took backlash for moving from unlimited to credits without good change management; do not repeat their mistakes.)
5. **Distribution test.** Does at least one capability that pulls in new users sit firmly in Bucket A? If your shareable / embeddable / public-output features are gated, you have suffocated your own growth loop.

### Phase 6: Produce the report

Write the final deliverable using the template in `references/output-template.md`. The report should answer the user's question completely and be readable by a non-pricing-expert founder. Include:

- The capability inventory with bucket assignments and reasoning per capability
- The credit unit definition (what one credit buys)
- The recommended free tier shape
- The recommended paid tier shape
- The top three risks
- The migration plan if there is an existing pricing scheme

Save the report as a Markdown file. If the user wants a polished deliverable, offer to convert it to a Word doc or PDF afterward, but the analysis itself lives in Markdown so it is easy to edit.

## Reference files

Read these before doing the analysis. They are organized for progressive disclosure: read what you need, when you need it.

- `references/research-foundation.md` — The 2025 to 2026 industry research, the credit-economy backdrop, why credits emerged, customer sentiment, and the evolution toward outcome-based pricing. Read this first if the user is unfamiliar with the credit-economy context.
- `references/decision-matrix.md` — Full scoring rubric for the eight dimensions, the gating decision rules in expanded form, and the edge cases. Read this before Phase 3.
- `references/case-studies.md` — Concrete teardowns of Lovable, Cursor, Replit, ChatGPT, Figma, Slack, Canva, and others, showing what each company chose to gate and why. Use these as analogies when explaining recommendations to the user.
- `references/output-template.md` — The exact structure and headings for the final report.

## A few things to never do

- Never recommend gating a capability the user clearly described as their aha moment.
- Never recommend pricing in raw tokens for end users (use a credit abstraction or a domain unit like "messages" or "minutes").
- Never claim there is a single correct answer. Pricing is a hypothesis. The skill produces a defensible starting point, not a verdict.
- Never silently introduce em dashes into the report. Use commas, parentheses, semicolons, or sentence breaks instead.
- Never rationalize gating something that costs the company nothing. That is extraction, not monetization, and customers smell it immediately.

## Communicating with the user

Most users running this skill are founders, PMs, or solo builders. They want clear reasoning more than they want jargon. When you explain a recommendation, lead with the principle ("we are gating this because it has high cost-to-serve and is past the aha moment") and then back it with the case-study analogy ("this is similar to how Lovable handles agent tasks"). Avoid jargon like "value metric" without unpacking it. Treat the report as a memo to a smart non-expert.

If the user pushes back on a recommendation, do not collapse. The framework is opinionated for a reason. Re-examine the scoring with them, but do not change the answer just because they prefer a different one. If they have new information that changes a score, update the score and re-run the rule, and explain what changed.
