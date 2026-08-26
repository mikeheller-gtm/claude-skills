# Claude Skills

Two Claude skills for early-stage go-to-market work, from [Mike Heller](https://floodgate.com) at Floodgate.

Both are packaged as [Agent Skills](https://docs.claude.com/en/docs/agents-and-tools/agent-skills/overview): a folder with a `SKILL.md` that Claude loads when the work matches its description.

## The skills

### `founder-gtm-audit`

Turns sales call transcripts into 3-8 prioritized recommendations, written the way a peer advisor would say them across the table rather than as a consulting report. It scales from quick feedback on one call to a full review of a sales motion across many.

The audit is anchored on two things that, when founders get them wrong, tend to sink the whole motion:

1. **Find their top problem and make the entire motion about it.** A senior buyer is working on two or three priorities. If you land on one of them and the motion stays there, there's a deal. If you find a glimmer of interest and then flood them with capabilities, there probably isn't.
2. **Design the buying process for the buyer.** Buyers don't evaluate new products all day and don't know the right next steps for something they just saw. Hand them an evaluation path instead of asking what they think makes sense. Call 1 to Call 2 conversion is the biggest differentiator between founders who close and founders who don't.

Two secondary lenses run alongside: following the breadcrumbs buyers drop and go unexplored, and spotting unexpected customer pull across multiple calls.

Feed it pasted transcripts or Granola / Gong / Chorus exports.

### `market-architect`

Takes a pitch call or general business context and produces two linked things: 3-5 bold structural moves the founder could make to restructure the market, and a read on go-to-market quality treated as a quality of the business itself.

The thesis: AI has collapsed execution risk, so product creativity is table stakes. The rarer thing is creativity that extends past the product into the market itself, through acquisitions, institutional persuasion, improbable allies, incentive redesign, inventing job categories, engineering ecosystems. Market entrants compete inside an existing structure. Market architects treat market structure as something you build.

The diagnostic move is that the binding constraint usually isn't technology. It's a regulation, a standard, a labor structure, a trust deficit, a procurement process, or a distribution bottleneck. The dominant strategy is the non-product move that removes it.

It carries a set of thinking prompts rather than a playbook, a pressure-test step every strategy has to survive, and an ambition floor: the founder's own most ambitious statement is the minimum, and at least one strategy has to reach past it.

## Installing

**Claude Code and Cowork (local):** copy a skill folder into `~/.claude/skills/`, or into `.claude/skills/` inside a project to scope it there.

```bash
git clone https://github.com/USERNAME/claude-skills.git
cp -r claude-skills/skills/founder-gtm-audit ~/.claude/skills/
```

**Claude apps:** zip the skill folder and upload it under Settings > Capabilities > Skills.

```bash
cd skills && zip -r founder-gtm-audit.zip founder-gtm-audit
```

Claude picks a skill up on its own when a request matches the `description` in its frontmatter, so no invocation syntax is needed. `market-architect` is deliberately set to trigger only on explicit requests ("run market architect on X") so it doesn't fire on ordinary pitch analysis.

## Notes

These are working documents, not finished frameworks. `market-architect` in particular changes as founders push back on its output. Feedback that says "this was less ambitious than my own thinking" is the most useful kind, and has already produced rules that live in the skill.

## License

MIT. See [LICENSE](LICENSE).
