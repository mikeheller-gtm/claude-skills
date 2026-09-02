# Claude Skills for Founders

Two Claude skills for early-stage go-to-market work, from [Mike Heller](https://floodgate.com) at Floodgate. Both are written for a founder running them on their own company.

- **`founder-gtm-audit`** turns your sales call transcripts into a short list of prioritized, specific things to change about how you sell.
- **`founder-market-architect`** finds the structural, non-product move that could let your company own its market, then tries to kill it before you bet on it.

Each one is packaged as an [Agent Skill](https://docs.claude.com/en/docs/agents-and-tools/agent-skills/overview): a folder with a `SKILL.md` that Claude loads on its own when what you ask matches. No commands to learn. Install once, then just talk to Claude.

## Installing

### Claude on the web or desktop app (most people)

No terminal, no code. About two minutes.

1. Download the skill you want. Direct links:
   - [founder-gtm-audit.zip](https://github.com/mikeheller-gtm/claude-skills/raw/main/dist/founder-gtm-audit.zip)
   - [founder-market-architect.zip](https://github.com/mikeheller-gtm/claude-skills/raw/main/dist/founder-market-architect.zip)
2. In Claude, make sure **code execution** is turned on: Settings > Capabilities. (Skills need it. It's on by default for most accounts.)
3. Go to **Customize > Skills** in the sidebar, click **+**, then **Create skill**, then **Upload a skill**, and pick the zip you downloaded.
4. Start a new chat and ask for what you want. For example, paste a call transcript and say "review this sales call." Claude will pick up the skill on its own.

Works on Free, Pro, Max and Team plans. The same install covers Cowork on the desktop app, which loads whatever skills are enabled on your Claude account.

### Claude Code

Either install as a plugin:

```
/plugin marketplace add mikeheller-gtm/claude-skills
/plugin install founder-gtm-audit@mikeheller-gtm
/plugin install founder-market-architect@mikeheller-gtm
```

Or copy a skill folder into `~/.claude/skills/` (or `.claude/skills/` inside a project to scope it there):

```bash
git clone https://github.com/mikeheller-gtm/claude-skills.git
cp -r claude-skills/skills/founder-gtm-audit ~/.claude/skills/
cp -r claude-skills/skills/founder-market-architect ~/.claude/skills/
```

### If you can't install skills at all

Create a Claude Project, paste the contents of the skill's `SKILL.md` into the project instructions, and (for the audit) add `references/framework.md` as project knowledge. It won't trigger automatically and is a somewhat weaker version, but it runs anywhere.

## The skills

### `founder-gtm-audit`

Turns sales call transcripts into 3-8 prioritized recommendations, written the way a peer advisor would say them across the table rather than as a consulting report. It scales from quick feedback on one call to a full review of a sales motion across many.

The audit is anchored on two things that, when founders get them wrong, tend to sink the whole motion:

1. **Find their top problem and make the entire motion about it.** A senior buyer is working on two or three priorities. If you land on one of them and the motion stays there, there's a deal. If you find a glimmer of interest and then flood them with capabilities, there probably isn't.
2. **Design the buying process for the buyer.** Buyers don't evaluate new products all day and don't know the right next steps for something they just saw. Hand them an evaluation path instead of asking what they think makes sense. Call 1 to Call 2 conversion is the biggest differentiator between founders who close and founders who don't.

Two secondary lenses run alongside: following the breadcrumbs buyers drop and go unexplored, and spotting unexpected customer pull across multiple calls.

**What to feed it:** pasted transcripts, or Granola / Gong / Chorus exports. A few calls are enough to run on. A whole quarter of calls is better in a way that isn't linear: that's where the needle-in-a-haystack findings live (the segment where Call 2 conversion is triple everyone else's, the offhand question five prospects asked, the buyer language the founder never uses), and the skill goes looking for them specifically once it has ten or more.

**Things to try:**

- Paste one transcript: "Quick feedback on this discovery call. What did I miss?"
- Paste five or six: "Why aren't these turning into second calls?"
- Paste a quarter's worth plus a line or two about the company: "Run a full GTM audit on our sales motion."
- Paste an outbound sequence: "Review this cold email sequence."

### `founder-market-architect`

Finds the structural, non-product moves that could let your company own its market, then tries to kill each one before you bet on it.

The thesis: AI has collapsed execution risk, so product creativity is table stakes. The rarer thing is creativity that extends past the product into the market itself, through acquisitions, institutional persuasion, improbable allies, incentive redesign, inventing job categories, engineering ecosystems. Market entrants compete inside an existing structure. Market architects treat market structure as something you build.

The diagnostic move is that the binding constraint usually isn't technology. It's a regulation, a standard, a labor structure, a trust deficit, a procurement process, or a distribution bottleneck. The dominant strategy is the non-product move that removes it.

It asks you for what it needs (what you sell, how you sell it, where you are, and the most ambitious version of the company you actually believe in), then writes a document: what it sees in the business, 3-5 pressure-tested strategies with a first step for each, an honest read on your go-to-market, and the questions worth sitting with.

Two rules do most of the work. **The ambition floor:** your own most ambitious statement is the minimum, and at least one strategy has to reach past it, because a tidier version of your own plan is a waste of your time. **Named targets:** "partner with a standards body" is a prompt, not a strategy, so where a play depends on a specific institution, dataset, community, or person, it names the candidate.

Before generating anything it maps the table: every party whose yes, no, or indifference shapes the market (the regulator, the incumbent, the licensing body, the institution that physically holds the key asset, the customer's lawyer), and what each one wants. Strategies get built around the people who have to say yes rather than corrected for them later.

Every strategy then runs a set of kill tests (fungibility, density, attribution, neutrality, second-order go-to-market, cold start, buyer motivation, counterparty and licensure, population, and the strongest rebuttal you would raise). Ideas that survive only in scoped form are presented scoped, with the reasoning. The point is that you shouldn't be able to puncture an idea in one sentence.

It also runs in two passes inside a single request. The first pass writes a complete draft. The second reads that draft cold, as an operator who has run a company in your exact market for fifteen years and their general counsel would, checks the load-bearing facts, and writes a kill log. You only see the revised memo. The second pass exists because a first draft once proposed free custody of tumor tissue as a data moat, and the operator's read was "hospitals own the tissue."

**Things to try:**

- Paste your deck or your website copy: "Run market architect on us."
- With nothing pasted: "What's the bold move here?" It will ask you for what it needs.
- After a run: "This is less ambitious than what we're already planning." It should come back with something bigger, and if it doesn't, tell me.

## Notes

These are working documents, not finished frameworks. The current versions are tuned for the Claude Fable 5 generation of models (September 2026): they run unattended after one intake message, generate more candidates and kill harder, check load-bearing assumptions with a bounded amount of research before presenting an idea, and carry explicit rules on quoting, prose density, and formatting that newer models need and older ones didn't. They still work on Opus and Sonnet. `founder-market-architect` in particular changes as founders push back on its output. Feedback that says "this was less ambitious than my own thinking" is the most useful kind, and is exactly why the ambition floor rule exists.

If you have feedback, [open an issue](https://github.com/mikeheller-gtm/claude-skills/issues) or message me on LinkedIn. I read both.

## Who I am

I'm a partner at [Floodgate](https://floodgate.com), where we write first checks. Before that I was an early sales hire at Dropbox and Clearbit, and then spent a few years doing fractional GTM work for seed-stage founders, which is where most of what's in these skills actually came from. I spend a lot of time thinking about the business models AI makes possible (not just the products it makes possible), and about how early-stage companies sell.

If you ran one of these on your company and it surfaced something useful, or got something wrong, I'd like to hear about it. And if you're building something ambitious in that vein and want a first check, reach out on [LinkedIn](https://www.linkedin.com/in/mike-s-heller). No deck required.

## License

MIT. See [LICENSE](LICENSE).
