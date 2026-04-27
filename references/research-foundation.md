# Research Foundation: The Credit Economy in 2025 to 2026

This file is the empirical backbone of the skill. Everything in `SKILL.md` is grounded in the patterns documented here. Read this first if you are unfamiliar with how the credit-pricing landscape evolved.

## The macro picture

Credit-based pricing went mainstream in 2025. The numbers, drawn from the PricingSaaS 500 Index analysis covered by Growth Unhinged and HubSpot in late 2025 and early 2026, are striking:

- 79 of the top 500 SaaS companies offered a credit model by end of 2025, up from 35 the year before. That is a 126 percent year-over-year jump.
- Roughly 65 percent of SaaS vendors adding generative AI capabilities had adopted hybrid pricing (flat subscription plus a credit or usage meter) by late 2025, per Bain analysis.
- 78 percent of IT leaders surveyed by Zylo for the 2026 SaaS Management Index reported "unexpected charges tied to AI or consumption" in the past year. Credit pricing is creating real budget pain.
- Hybrid models (subscription plus usage) showed a 21 percent median growth rate in Maxio's 2025 Pricing Trends Report, the highest of any model.
- Seat-based pricing dropped from 21 percent to 15 percent of B2B AI/SaaS pricing in twelve months. Hybrid grew from 27 percent to 41 percent.
- Ibbaka and Constellation Research forecasts published in late 2025 and early 2026 predict that credit-based pricing will be the default pattern for new AI-native products through 2027.

Read those numbers carefully. They tell a specific story: credits are surging, but customers are not happy, and the next generation of pricing will move toward outcome-based metrics where vendors can attribute value cleanly.

## Why credits exist (the honest version)

Credits are not a marketing innovation. They emerged because the unit economics of AI products do not work under flat subscriptions. A product manager building a credit system should understand the four real reasons credits exist:

1. **Variable cost protection.** A flat $20 per month plan does not work when one user makes 50 LLM calls and another makes 50,000. Inference costs are real money. Without a meter, the heavy users subsidize the light ones, and the company eats margin.

2. **Cost normalization across volatile usage.** LLM consumption is bursty. A user might run nothing for a week, then run a thousand agent tasks in a day. Credits convert that volatility into a predictable monthly prepayment.

3. **Operational simplicity at the platform level.** When you have ten AI features, each with its own cost profile, you do not want ten different meters. Credits roll everything into one currency. Internal teams stop arguing about whether feature X should bill in tokens or images, and customers see one balance.

4. **Margin protection during pricing experimentation.** If you launch a new feature and the cost-to-serve turns out to be triple what you expected, you can quietly increase its credit cost without renegotiating customer contracts. Credits are a buffer between your COGS and your customer-facing price.

Notice what is not on this list: extracting more revenue from a flat subscriber. If your only motivation for credits is to charge more for the same thing, customers will revolt.

## Why customers dislike credits (the honest version)

The Metronome 2025 field report and the Tropic credit pricing analysis surfaced a consistent pattern across every interviewed pricing leader: customers tolerate credits, but they do not love them. Direct quotes from the research:

- "Credits gave us breathing room while we figured out the real value metric. But they're not intuitive to buyers." (director of monetization at an enterprise productivity company)
- "Our finance team likes it. Our customers don't know what a credit does." (GTM lead, productivity tool)
- "We don't love credits, but we didn't have time to define outcomes." (head of product monetization, horizontal SaaS vendor)

The buyer-side complaints cluster around four issues:

1. **No mental model.** A user who buys 1,000 credits has no idea what that gets them in practice. Compare to "100 minutes of video" or "500 transcribed meetings". The latter is intuitive. The former is not.
2. **Surprise depletion.** Different actions cost different credits, and users do not see this in advance. Heavy actions (agent tasks, long generations) drain a balance fast.
3. **Cross-vendor confusion.** One company's credit is another company's milli-credit. Buyers cannot compare across vendors.
4. **Expiration anxiety.** Monthly resets and rollover caps make customers feel like they are losing money they already paid for.

A credit system that ignores these complaints will get backlash. The Cursor, V0, and Replit transitions in mid-2024 to mid-2025 from unlimited or generous tiers to tighter credit-based models all triggered user backlash that is still discussed on Hacker News and Reddit. The lesson: change management matters more than the credit math.

## The trajectory: where credits are going

Credits are a transitional architecture. The endgame, per Metronome's field report and Reforge's pricing analysis, is outcome-based pricing where vendors charge per measurable result rather than per action. Examples that are already shipping:

- Synthesia and Fireflies price per minute of video or transcription generated.
- Decagon charges per resolved customer service conversation.
- Salesforce's Agentforce charges $2 per customer conversation handled.
- Zendesk charges per automated resolution.

Pure outcome-based remains rare in 2026 because attribution is hard. When AI does part of the work and a human finishes, who gets credit for the outcome? Until that gets solved, credits are the bridge.

The implication for someone designing pricing today: design your credits in a way that maps cleanly to a future outcome unit. If the natural outcome is "a deployed app", let one credit roughly map to one deploy-equivalent unit of work. If the natural outcome is "a generated image", price one credit per image. Do not invent abstract credit units that have no relationship to the user's mental model.

## How leading credit products are designed (snapshot view)

Detailed teardowns are in `case-studies.md`. The summary patterns:

- **Lovable** prices one credit per AI message in plan mode, more for agent mode, and gives 5 daily bonus credits to all users (including free). The "Try to fix" button is free because it would feel hostile to charge for fixing your own bug. Pro and Business plans cost the same in credits but differ in collaboration and governance features.
- **Cursor** uses a request-based credit model. Pro is $20 per month with about 225 Claude Sonnet requests. Auto mode (where Cursor picks the model) is effectively unlimited, which is a clever way to give heavy users an "always works" path while still gating premium model access.
- **Replit** uses effort-based pricing where the agent's checkpoints consume credits at variable rates. Heavy users report $100 to $300 per month overage. The pricing change in mid-2024 to effort-based pricing caused significant user backlash.
- **OpenAI ChatGPT** gates models, not access. The free tier gets a usage cap on the best model and falls back to cheaper models. Plus and Pro tiers raise the cap and add features like longer context, deep research, and more advanced reasoning models.
- **Figma, HubSpot, Salesforce** layered AI credits on top of existing seat-based pricing rather than replacing it. The seat is still the primary commercial unit; credits are an AI-usage overlay.

## Frameworks consulted

This skill synthesizes ideas from several published pricing frameworks. The most useful ones to know:

- **HOPE Framework (Pace Pricing).** Evaluates value metrics on whether they are (H) high-correlated with value, (O) observable, (P) predictable, and (E) easy to understand.
- **Engagement Graph (SeedToScale).** Plots activities on frequency-versus-importance axes. The monetization sweet spot is medium-frequency, medium-importance activities. High-frequency activities should be priced low or free to prevent competitive undercutting.
- **Gate Power Not Access (Stratrix).** The most consequential principle in feature-gating. Free users should be able to do the core job; paid users should be able to do it faster, better, or at greater scale.
- **Slack's history-versus-messaging gate.** Slack let teams message freely (the core job) but gated history beyond 90 days. The team formed a habit, then hit a natural pain point that drove team-level upgrades. This is the textbook example of gating a value-amplifier rather than the core capability.
- **Canva's preview-then-paywall.** Canva's background-remover lets free users see the result with a watermark, then prompts upgrade. Sunk-cost psychology plus immediate visible value drives conversion. Applies anywhere the AI output can be previewed cheaply.
- **PricingSaaS feature-gating taxonomy.** Categories: feature differentiated, usage tiered, outcome based, hybrid. Each works in specific situations.

## The "what to give away" research

A consistent finding across the freemium research (RevenueCat, Stratrix, Stackmatix, ProductLed) is that the wrong things to gate are the things users need to form a habit. Specifically:

1. **Never gate the aha moment.** A user who has not yet experienced value cannot be convinced to pay.
2. **Never gate the things that pull others in.** If sharing, embedding, public outputs, MCP servers, or referral links are gated, you have shut off your own distribution.
3. **Never gate things that compound usage.** If a feature makes users use the product more, free is the right answer because more usage means more paid conversion downstream.
4. **Always gate the things that scale with cost.** Variable-cost features must have a meter, or the company eats margin.
5. **Always gate things that scale with success.** A user generating $1M in revenue from your tool should pay more than a user testing it on weekends. Find the metric that scales with their success and gate on that.

The MCP Freemium Strategy article (PricingSaaS, February 2026) is worth knowing: companies are increasingly putting MCP server access in the free tier because MCPs drive distribution into LLM workflows, and the user-acquisition value of being embedded in someone's Claude or ChatGPT setup outweighs the metering revenue from gating it.

## A note on the 2026 pendulum

Kyle Poyar's analysis at Growth Unhinged in early 2026 noted that the pendulum may swing back toward simplicity. The flood of credit models has created customer fatigue. The companies that win in 2026 and 2027 may be the ones who simplify back toward a clear unit ("100 generations per month" rather than "1,500 credits"), or who jump straight to outcome-based pricing.

The implication for new products: pick a credit unit that has an obvious mapping to user outcomes, even if your internal billing system uses a more granular meter. Customers should never have to do math to know what they are buying.
