# Claude Skills

Claude skills for early-stage go-to-market work, from [Mike Heller](https://floodgate.com) at Floodgate.

Each one is packaged as an [Agent Skill](https://docs.claude.com/en/docs/agents-and-tools/agent-skills/overview): a folder with a `SKILL.md` that Claude loads when the work matches its description.

Both are written for a founder running them on their own company.

## The skills

### `founder-gtm-audit`

Turns sales call transcripts into 3-8 prioritized recommendations, written the way a peer advisor would say them across the table rather than as a consulting report. It scales from quick feedback on one call to a full review of a sales motion across many.

The audit is anchored on two things that, when founders get them wrong, tend to sink the whole motion:

1. **Find their top problem and make the entire motion about it.** A senior buyer is working on two or three priorities. If you land on one of them and the motion stays there, there's a deal. If you find a glimmer of interest and then flood them with capabilities, there probably isn't.
2. **Design the buying process for the buyer.** Buyers don't evaluate new products all day and don't know the right next steps for something they just saw. Hand them an evaluation path instead of asking what they think makes sense. Call 1 to Call 2 conversion is the biggest differentiator between founders who close and founders who don't.

Two secondary lenses run alongside: following the breadcrumbs buyers drop and go unexplored, and spotting unexpected customer pull across multiple calls.

Feed it pasted transcripts or Granola / Gong / Chorus exports. A few calls are enough to run on. A whole quarter of calls is better in a way that isn't linear: that's where the needle-in-a-haystack findings live (the segment where Call 2 conversion is triple everyone else's, the offhand question five prospects asked, the buyer language the founder never uses), and the skill goes looking for them specifically once it has ten or more.

### `founder-market-architect`

Finds the structural, non-product moves that could let your company own its market, then tries to kill each one before you bet on it.

The thesis: AI has collapsed execution risk, so product creativity is table stakes. The rarer thing is creativity that extends past the product into the market itself, through acquisitions, institutional persuasion, improbable allies, incentive redesign, inventing job categories, engineering ecosystems. Market entrants compete inside an existing structure. Market architects treat market structure as something you build.

The diagnostic move is that the binding constraint usually isn't technology. It's a regulation, a standard, a labor structure, a trust deficit, a procurement process, or a distribution bottleneck. The dominant strategy is the non-product move that removes it.

It asks you for what it needs (what you sell, how you sell it, where you are, and the most ambitious version of the company you actually believe in), then writes a document: what it sees in the business, 3-5 pressure-tested strategies with a first step for each, an honest read on your go-to-market, and the questions worth sitting with.

Two rules do most of the work. **The ambition floor:** your own most ambitious statement is the minimum, and at least one strategy has to reach past it, because a tidier version of your own plan is a waste of your time. **Named targets:** "partner with a standards body" is a prompt, not a strategy, so where a play depends on a specific institution, dataset, community, or person, it names the candidate.

Every strategy runs a set of kill tests first (fungibility, density, attribution, neutrality, second-order go-to-market, cold start, buyer motivation, and the strongest rebuttal you would raise). Ideas that survive only in scoped form are presented scoped, with the reasoning. The point is that you shouldn't be able to puncture an idea in one sentence.

## Installing

**Claude Code and Cowork (local):** copy a skill folder into `~/.claude/skills/`, or into `.claude/skills/` inside a project to scope it there.

```bash
git clone https://github.com/mikeheller-gtm/claude-skills.git
cp -r claude-skills/skills/founder-market-architect ~/.claude/skills/
```

**Claude apps:** zip the skill folder and upload it under Settings > Capabilities > Skills.

```bash
cd skills && zip -r founder-market-architect.zip founder-market-architect
```

Claude picks a skill up on its own when a request matches the `description` in its frontmatter, so no invocation syntax is needed. Ask it something like "run market architect on my company" or "review this sales call" and it will load the right one.

## Notes

These are working documents, not finished frameworks. The current versions are tuned for the Claude Fable 5 generation of models (September 2026): they run unattended after one intake message, generate more candidates and kill harder, check load-bearing assumptions with a bounded amount of research before presenting an idea, and carry explicit rules on quoting, prose density, and formatting that newer models need and older ones didn't. They still work on Opus and Sonnet. `founder-market-architect` in particular changes as founders push back on its output. Feedback that says "this was less ambitious than my own thinking" is the most useful kind, and is exactly why the ambition floor rule exists.

## License

MIT. See [LICENSE](LICENSE).
