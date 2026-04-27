# Case Studies: How Real Companies Gate

Use these as analogies when explaining recommendations to the user. "This is similar to how Lovable does it" lands harder than "this scores 3, 5, 4 on the matrix".

## Lovable

**The product:** AI app builder. Users describe an app in natural language and Lovable generates a working React + Supabase application.

**What is free:**
- 5 daily bonus credits for all users including the free plan.
- The "Try to fix" button after an AI-generated error. Free because charging a credit for fixing the AI's own mistake feels hostile.
- Reading and viewing existing projects.

**What is metered with credits:**
- Plan mode messages: 1 credit per message.
- Agent mode tasks: variable credits depending on how the agent decomposes the task.
- A simple styling change costs around 0.5 credits, a complex feature like adding auth or new pages costs about 1.2 credits, and a basic MVP runs 150 to 300 credits start to deploy.

**What is tier-gated:**
- Custom domains require a paid plan.
- Collaboration and governance features distinguish Pro ($25 with 100 credits) from Business ($50 with 100 credits). Same credits, different tier features. This is unusually clean: credits are a commodity, workspace tooling is the premium differentiator.

**The lesson:** One message equals one credit is a brilliant simplification. Users do not have to think about tokens. The daily drip lets free users experiment without payment, while the monthly credit pool is the real product. Tier gates are decoupled from credits, which means raising tier prices does not require renegotiating the credit math.

## Cursor

**The product:** AI-powered code editor (a fork of VS Code).

**What is free:**
- The Hobby tier is free with limited usage.
- Auto mode (where Cursor picks the best available model) is effectively unlimited even on Pro.

**What is metered with credits:**
- Premium model requests (Claude Sonnet, GPT-4) on the Pro tier and above. Pro includes about 225 Claude Sonnet requests, 550 Gemini, or 650 GPT-4.1 per month.
- Pro+ ($60) gives 3x the usage credits.

**What is tier-gated:**
- Team features ($40/user) include admin controls and shared billing.
- Enterprise adds compliance and SSO.

**The lesson:** Cursor's "Auto mode is unlimited, premium models are metered" model is a clever way to give heavy users an always-works experience while still gating the most expensive operations. It also avoids the "I can't use the product because I'm out of credits" panic that destroys retention.

**The cautionary tale:** Cursor's transition from a more generous free tier to the current credit model in mid-2025 caused significant user backlash. The community read it as a bait-and-switch. Lesson: credit changes are change-management problems, not pricing problems.

## Replit

**The product:** Cloud IDE with an AI agent that can build entire apps.

**What is free:**
- Starter tier with free daily Agent credits and free credits for AI integrations.
- One published app on the free tier.

**What is metered with credits:**
- Agent checkpoints (the AI's units of work) cost variable credits based on effort.
- Always-on deployments and database storage consume credits.
- Heavy users report $100 to $300 per month overage.

**What is tier-gated:**
- Core ($17/mo): unlimited workspaces, removes the "Made with Replit" badge, autonomous long builds.
- Pro ($95/mo): private deployments, premium support, longer database restore window.
- Enterprise: SSO, compliance.

**The lesson:** Effort-based pricing protects margins on agent tasks but creates predictability problems. "I don't know what this will cost" is a real customer pain point.

**The cautionary tale:** Replit's mid-2024 switch to effort-based pricing produced significant community backlash. The President had to publish a defense explaining that the median checkpoint price only went up slightly. Anytime you raise the variable component of pricing, communicate the median user impact, not the worst case.

## ChatGPT (OpenAI)

**The product:** Conversational AI with a tiered consumer model.

**What is free:**
- Basic chat with a usage cap on the best model. After cap, the user falls back to a cheaper model.

**What is metered with credits (in the API, not consumer):**
- API users pay per token by model.

**What is tier-gated:**
- Plus ($20/mo): higher caps on the best model, image generation, GPT-4 access.
- Pro ($200/mo): Deep Research, more advanced reasoning models, longer context.
- Team and Enterprise: collaboration, admin, training opt-out.

**The lesson:** ChatGPT gates models, not access. The free user gets the same product, just with a cheaper backend. This is a brilliant pattern for AI-native products: the user always gets an answer, but the quality of the answer scales with the plan. No "you've been locked out" moment.

## Slack

**The product:** Team messaging.

**What is free:**
- Messaging itself, forever.
- Channel creation, DMs, integrations.

**What is metered:**
- Nothing in the classic Slack model (pre-AI).
- New AI features are credit-metered as overlays.

**What is tier-gated:**
- Message history beyond 90 days (the canonical example).
- More integrations, longer message retention, SSO, admin controls.

**The lesson:** Slack let teams form a habit (free messaging) and gated the value-amplifier (history). When teams grew large enough that searching old conversations mattered, the 90-day limit created a natural pain point that drove team-level upgrades, not individual ones. This is the textbook "gate the amplifier, not the core".

## Canva

**The product:** Design tool.

**What is free:**
- Templates, basic editing, downloads at standard quality.

**What is metered (in newer AI features):**
- AI image generation has monthly credit caps.

**What is tier-gated:**
- Background remover (the canonical example).
- Premium templates, brand kit, team features, larger storage.

**The conversion trick:** Free users can apply background removal and see the result with a watermark. The visible value plus the sunk-cost of the design they already built drives upgrade. This is a great pattern for any AI feature that produces a previewable output.

**The lesson:** Don't lock the door, lock the high-quality export. Show users what they could have. Sunk cost plus visible value beats abstract upgrade prompts.

## Figma

**The product:** Design and collaboration tool.

**What is free:**
- Up to 3 files, unlimited viewers, basic features.

**What is metered (newly):**
- AI features layered on top with credit-based access.

**What is tier-gated:**
- Professional ($15/mo): unlimited files, version history, sharing controls.
- Organization: SSO, advanced admin, design systems.

**The lesson:** Figma's pricing is essentially seat-based with an AI credit overlay. The seat is still the primary commercial unit. This is the dominant pattern for established SaaS adding AI: do not blow up the existing model, layer credits on top.

## HubSpot, Salesforce, Miro

These three are worth grouping because they all made the same move in 2025: layered AI credits on top of existing seat or tier pricing rather than replacing it. The pattern:

- Seats and tiers stay as the commercial primary unit.
- AI features get a credit overlay.
- Customers can buy additional credit packs when they exceed the included allowance.
- Some plans (Enterprise, Education) have shared credit pools without per-seat caps.

This is the safe path for established SaaS. The trade-off is that customers feel like AI is a tax rather than a feature.

## Synthesia, Fireflies, Decagon

These are early examples of the post-credit world: outcome-based pricing.

- **Synthesia** prices per minute of video generated.
- **Fireflies** prices per minute of meeting transcribed.
- **Decagon** prices per resolved customer service conversation.
- **Salesforce Agentforce** prices at $2 per customer conversation handled.
- **Zendesk** prices per automated resolution.

The unit is intuitive (a minute, a resolution). The customer can map cost directly to value. Credits are not needed because the unit is already meaningful.

**The lesson:** If your product naturally produces a measurable outcome, skip credits and price the outcome. Credits are a stopgap when the outcome is too varied to price directly.

## MCP servers (the 2026 distribution play)

A pattern emerging in late 2025 and early 2026: companies are putting MCP server access in the free tier even when the underlying API is paid.

- **Otter** offers MCP for free, letting users pipe transcripts into Claude or ChatGPT. The MCP itself is not monetized; it drives downstream usage that hits other limits.
- **Zapier** offers MCP free, but each MCP tool call counts as 2 tasks toward the free 100-task quota.
- **PricingSaaS** offers MCP free as a distribution play.

**The lesson:** When a capability creates LLM-embedded distribution (your product becomes a tool that lives inside someone else's AI workflow), the user-acquisition value beats the metering value. Make it free.

## What to take from these case studies

Look at what each company did NOT gate. Slack did not gate messaging. Lovable did not gate the daily 5 credits. ChatGPT did not gate access entirely. Figma did not gate viewers. The core capability stays free in every successful case. Power, scale, governance, and history get gated.

When a user pushes back on a gating recommendation, find the analogous case study and explain what that company learned. Founders generally do not want to repeat Cursor's or Replit's backlash. They do want to do what Slack and Lovable did.
