# 💰 Credit Gating Analyzer

**Stop guessing what to charge for.** This Kiro skill takes your product (a codebase, PRD, feature list, or even a half-baked idea) and produces a defensible monetization map: what stays free, what gets metered with credits, and what sits behind a paid tier.

Built on 2025-2026 industry research from the credit-economy boom. Grounded in real teardowns of Lovable, Cursor, Replit, ChatGPT, Slack, Canva, Figma, and more.

---

## What it does

You feed it your product. It gives you back:

- A scored inventory of every capability in your product
- Clear bucket assignments: Free / Free with drip / Credit-metered / Tier-gated
- A recommended credit unit definition (what one credit actually buys)
- Free tier and paid tier shapes
- Risk analysis and migration guidance
- Case-study analogies so you can explain decisions to your team

The output is a Markdown report you can hand to your co-founder, your board, or your pricing committee.

## Who it's for

- Founders figuring out pricing for the first time
- PMs adding AI features to existing products and wondering what to meter
- Solo builders who need a pricing strategy but don't have a monetization team
- Anyone staring at a product and asking "should this be free?"

## Core principles

The skill enforces opinionated rules backed by research:

1. **Gate power, not access.** Free users do the core job. Paid users do it faster, better, at scale.
2. **Credits exist for cost reasons, not greed.** If it doesn't cost you money to serve, don't charge credits for it.
3. **The aha moment must happen before any paywall.** No value experienced = no conversion.
4. **Credits are a bridge, not a destination.** Design toward outcome-based pricing.
5. **Don't confuse metering with entitlements.** Variable-cost actions get credits. Governance and scale get tiers.

---

## Installation

### Install the skill

```bash
npx skills add https://github.com/bikidsx/credit-gating
```

---

## Usage

Once installed, trigger the skill by asking Kiro anything related to pricing or monetization:

- "How should I charge for this?"
- "What should be paid in my app?"
- "Design my credit system"
- "What costs me money to run?"
- "Should this feature be free?"
- "Audit my product for margin risk"
- "Plan my free vs paid split"

The skill activates automatically when it detects pricing intent. You can feed it:

- A codebase (it will scan for paid API calls, LLM usage, GPU jobs)
- A PRD or feature doc
- A verbal description of your product
- A Figma link or pitch deck

### Example

```
You: I built an AI writing assistant that generates blog posts, rewrites content,
     and suggests SEO keywords. How should I price it?

Kiro: [Runs the 6-phase analysis, asks clarifying questions about your aha moment
      and cost structure, then delivers a full monetization map]
```

---

## What's inside

```
credit-gating-analyzer/
├── SKILL.md                          # Skill definition and workflow
├── references/
│   ├── research-foundation.md        # 2025-2026 credit economy research
│   ├── decision-matrix.md            # Scoring rubric (8 dimensions, 4 buckets)
│   ├── case-studies.md               # Real company teardowns
│   └── output-template.md            # Report structure template
├── LICENSE                           # MIT
└── README.md                         # You are here
```

---

## The framework at a glance

Every capability in your product gets scored 1-5 on eight dimensions:

| Dimension | What it measures |
|-----------|-----------------|
| Cost-to-serve | Real money per invocation |
| Frequency | How often users invoke it |
| Aha-moment proximity | How close to first-time value |
| Habit formation | Does it bring users back? |
| Network value | More valuable with more users? |
| Distribution pull | Does it bring new users in? |
| Outcome attribution | Can you measure the value delivered? |
| Substitution ease | Can users do this elsewhere for free? |

Then each capability routes to a bucket:

| Bucket | Rule | Example |
|--------|------|---------|
| **A: Free forever** | Low cost + high aha/distribution/network | Slack messaging, Calendly booking pages |
| **B: Free with drip** | High cost + high aha proximity | Lovable's 5 daily credits, ChatGPT free tier |
| **C: Credit-metered** | High cost + past aha + measurable outcome | Agent tasks, video generation, premium model calls |
| **D: Tier-gated** | Access/governance/scale value | SSO, audit logs, team features, custom domains |

---

## License

MIT. See [LICENSE](LICENSE).

---

## Contributing

Found a case study that should be included? Have research that updates the foundation? PRs welcome.

---

*Built for the credit economy. Designed to be opinionated. Your pricing is a hypothesis, not a verdict.*
