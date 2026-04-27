# Decision Matrix: Scoring Rubric and Gating Rules

This file expands Phase 3 and Phase 4 of the workflow. Read it before scoring capabilities. The eight dimensions and the four buckets are defined here in full.

## The eight scoring dimensions

Score every capability 1 to 5 on each dimension. Be honest. Inflated scores produce useless recommendations.

### 1. Cost-to-serve

How much does each invocation actually cost the company in real money?

- **1.** Effectively zero. Static page render, cached lookup, simple database write, frontend interaction. The marginal cost is rounding error.
- **2.** Low and bounded. A small database query, a cheap third-party API call (sub-cent), or a small cached LLM call. Predictable and small.
- **3.** Moderate. A typical LLM call to a mid-tier model, a moderate API call to a paid third party, a brief GPU job. A few cents per invocation.
- **4.** High. A long-context LLM call to a frontier model, a multi-step agent task, a 10-second GPU render, a paid third-party API with per-call pricing in the dimes.
- **5.** Severe. A full agent run that spawns sub-agents, a long video render, fine-tuning, a multi-minute GPU job, or anything that can plausibly cost a dollar or more per invocation.

When in doubt, look at the actual API bill the company would receive if a single user invoked this 1,000 times in a day. If the answer is "we would not notice", it is a 1 or 2. If the answer is "we would call an emergency meeting", it is a 5.

### 2. Frequency

How often does an engaged, satisfied user invoke this capability per week?

- **1.** Rarely. Once a month or less. Reset password, change billing.
- **2.** Occasional. A few times a month. Export a report, invite a teammate.
- **3.** Weekly. Once or twice a week. Generate a new project, run a deployment.
- **4.** Daily. Most days an engaged user touches it.
- **5.** Constant. Multiple times per session. Autocomplete, chat messages, search queries.

High frequency is not the same as high value. Daily-use features are habit-forming and often deserve to be free (or have a very generous allowance) because gating them creates constant friction.

### 3. Aha-moment proximity

How close is this capability to the experience that makes a new user say "oh, this is the thing"?

- **1.** Distant. Used only after months of engagement. Admin features, archive, reports across past periods.
- **2.** Tangential. Useful but not what got the user excited. Settings, integrations, billing.
- **3.** Adjacent. Part of a typical first session but not the headline. Sharing, exporting, naming projects.
- **4.** Direct. The user lands on the product and within minutes uses this. The first generation, the first chat, the first deploy.
- **5.** The aha itself. Without this, the product does not work. The signature capability.

Anything scoring 4 or 5 must be reachable for free, even if rate-limited.

### 4. Habit formation

Does using this capability today increase the chance the user comes back tomorrow?

- **1.** No. One-and-done. A user uses it once and never again.
- **2.** Mild. Increases retention slightly but is not the hook.
- **3.** Moderate. Users who use it weekly are noticeably stickier.
- **4.** Strong. The capability is the reason users return.
- **5.** Defining. Users describe their relationship to your product through this capability ("I'm a Cursor user", "I journal with Day One").

High-habit features pay you back through retention and word of mouth. Gating them too aggressively kills the habit before it forms.

### 5. Network value

Does the capability become more valuable to others when one user uses it?

- **1.** Solo. Only the using user benefits.
- **2.** Adjacent. Marginally helps teammates.
- **3.** Team-multiplied. Each new user adds linear value to teammates (Slack, Notion, Figma).
- **4.** Cross-organization. Users from different orgs benefit from each other's usage (LinkedIn, Calendly, Zoom).
- **5.** True network effect. The product is meaningfully more valuable when more people use it. Marketplace, social, communication.

Network-valuable features should almost always be free at the entry point. The user count is the moat.

### 6. Distribution pull

Does using this capability bring new users into the product?

- **1.** None. Internal-only.
- **2.** Minimal. Maybe a "made with X" badge somewhere.
- **3.** Moderate. Public outputs that occasionally lead to signups (Calendly's booking pages).
- **4.** Strong. The capability creates content or integrations that drop into other people's workflows (embed widgets, MCP servers, public share links).
- **5.** Viral. The capability is itself a growth loop (referral programs, "create a copy of this template", embeddable interactives).

Distribution-pulling features deserve to be free or near-free even when they have non-trivial cost-to-serve, because the user-acquisition arithmetic dominates.

### 7. Outcome attribution

How cleanly can you measure the business value this capability delivers to the user?

- **1.** Opaque. You cannot tell whether using this helped them or not.
- **2.** Inferred. You can guess at value through proxy metrics.
- **3.** Visible. The capability produces a measurable thing (a report, a generated asset, a completed step).
- **4.** Tangible. The output has obvious dollar or time value (minutes saved, leads captured, words written).
- **5.** Direct. The output is the business outcome (a booking, a resolution, a transaction, a closed deal).

High outcome attribution opens the door to outcome-based pricing in the future. Capabilities that score 4 or 5 are the natural candidates for the eventual transition away from credits.

### 8. Substitution ease

If you charge for this capability, how easy is it for the user to do it elsewhere?

- **1.** Locked in. The user has nowhere else to go (proprietary data, deep integration, no competitor).
- **2.** Hard. Substitution is technically possible but expensive in time or trust.
- **3.** Moderate. Several competitors exist and switching is annoying.
- **4.** Easy. Substitution is a Google search away (free alternatives, well-known competitors).
- **5.** Trivial. The user can do this in ChatGPT for free in five seconds.

If substitution is trivial (4 or 5), gating this capability does not increase revenue, it increases churn. Consider keeping it free and gating around it instead (workflow integration, history, collaboration).

## The four buckets, in expanded form

After scoring, route each capability into one of four buckets. The decision rules are stated tersely in the SKILL.md; here are the expanded versions with edge cases.

### Bucket A: Free forever, no metering

**Rule:** Cost-to-serve is 1 or 2 AND (Aha-moment proximity is 4 or 5 OR Distribution pull is 4 or 5 OR Network value is 4 or 5).

**Why:** These are capabilities where the math says "more usage is always good". Free users invoking these features 100 times a day is a feature, not a bug. They cost almost nothing to serve, they bring more users in, and they make the product feel alive.

**Examples in the wild:**
- Slack's messaging itself.
- Calendly's booking pages.
- ChatGPT's basic chat (yes, even with the cost-to-serve being non-trivial, the network and distribution value justifies a generous free tier).
- The "Try to fix" button in Lovable (zero cost, high aha proximity).

**Edge case:** A capability that scores 5 on distribution pull but 4 on cost-to-serve is still probably Bucket A. The acquisition value usually wins. But put a sane abuse-prevention rate limit on it.

### Bucket B: Free with a daily or monthly drip

**Rule:** Cost-to-serve is 3 or higher AND Aha-moment proximity is 4 or 5.

**Why:** The user has to experience this for the product to make any sense, but it costs you real money. The solution is a small allowance that lets a casual user feel the value without putting up a credit card, while a power user hits the ceiling fast and gets a clear upgrade prompt.

**Examples in the wild:**
- Lovable's 5 free credits per day for all users including free.
- ChatGPT's free-tier usage cap on the best model.
- Replit's free daily Agent credits.
- Midjourney's first batch of free generations (when active).

**Implementation note:** The daily drip should be enough for one meaningful task, not enough for a real workflow. Lovable's 5 credits per day caps out at roughly 30 per month, which is enough to experiment but not enough to ship anything serious. That ratio is the goal.

### Bucket C: Credit-metered

**Rule:** Cost-to-serve is 3 or higher AND Aha-moment proximity is 1, 2, or 3 AND Outcome attribution is moderate or higher.

**Why:** This is the classic credit territory. The capability is past the aha moment (so users already know they want it), it costs real money to serve (so the company needs a meter), and the outcome is measurable enough that the user can reason about value.

**Examples in the wild:**
- Lovable agent-mode tasks (variable credits based on complexity).
- Cursor agent requests in premium models.
- Replit checkpoint cost during agent runs.
- Synthesia per minute of video generated.

**The credit unit choice:** The single most important decision in Bucket C is what one credit buys. Bad credit units are abstract numbers that customers cannot reason about. Good credit units map to a real-world thing the user wants. Rank these from worst to best:

- Worst: tokens. Users do not know what a token is.
- Mediocre: arbitrary credits with a published price list. Better than tokens but still requires the user to do math.
- Good: domain-natural units. One message, one image, one minute, one task, one resolution.
- Best: outcome units. One booking, one closed deal, one resolved ticket.

Aim for "good" at minimum. Aim for "best" when outcome attribution is high.

**Edge case:** A capability with high cost-to-serve and high aha proximity belongs in Bucket B (drip), not Bucket C (credits). Do not put aha-essential things behind a credit gate.

### Bucket D: Tier-gated, not metered

**Rule:** The value being delivered is access, governance, scale, or trust rather than per-invocation consumption.

**Why:** Credits are a meter for variable-cost actions. Tiers are an entitlement system for capabilities where the value is "I am allowed to do this kind of thing" rather than "I just did N units of this thing". Conflating the two confuses customers and undermines both pricing axes.

**Bucket D capabilities cluster into themes:**

- **Governance and security:** SSO, audit logs, role-based access, SCIM, data residency, training opt-out.
- **Collaboration and scale:** more seats, shared workspaces, pooled credits across team, admin dashboards.
- **Trust and brand:** brand removal, white-labeling, custom domains.
- **Capability ceilings:** longer context, larger file uploads, longer history retention, higher rate limits, access to top-tier models.
- **Service level:** priority support, dedicated CSM, SLAs, training.
- **Privacy:** private deployments, dedicated tenancy, on-prem.

**Implementation note:** A capability can be in Bucket C AND Bucket D simultaneously. For example, agent runs are credit-metered (Bucket C), but private agent runs that do not log to the shared platform are tier-gated to Pro+ (Bucket D). Stating both routings explicitly is correct.

## Edge cases to watch for

**The "freemium trap" capability.** A capability with cost-to-serve 3 and aha-proximity 4 looks like Bucket B (drip). But if substitution ease is 5 (the user can do this in ChatGPT for free in seconds), the drip will not convert. Instead, keep the capability fully free and gate around it (integrations, history, collaboration).

**The "false power feature".** Sometimes a capability looks like a Bucket D power feature (advanced report builder, custom workflows) but actually scores 4 or 5 on aha proximity for the target persona. If your power users discover the product through the power feature, gating it kills the funnel. Re-score honestly.

**The "infrastructure cost masquerading as value".** Storage is often gated as a tier feature. But for the user, more storage is not a benefit, it is a cost they grudgingly pay. Storage gates work when storage is bundled into a clear value unit (1,000 hours of video, 50 projects). Naked GB tiers feel like extraction.

**The "cost-to-serve that drops over time".** Inference costs are dropping sharply year over year. A capability that scored 4 on cost-to-serve in 2024 may score 2 in 2026. Re-score quarterly. As cost drops, capabilities can graduate from Bucket C to Bucket B or even Bucket A, which is a clean way to deliver "more value at the same price" to customers.

**The "credit hoarding problem".** If credits roll over indefinitely, customers stockpile them and you have no usage signal. If they expire too aggressively, customers feel cheated. The Lovable model (monthly credits roll over for one billing cycle, daily credits do not roll over) is a reasonable default. Gamma's 2x rollover cap is also a reasonable pattern.

**The "agent task" sub-decision.** Agent tasks are special because they have unbounded variable cost. A single agent task can spawn dozens of sub-tasks. Always meter agent tasks proportional to compute consumed (Replit's effort-based model) rather than per task initiation, or you will eat heavy users' lunch.
