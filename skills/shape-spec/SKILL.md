---
name: shape-spec
description: "Turns a loose idea into a spec issue through an interview, or into a map of decisions when the work is too big for one session."
disable-model-invocation: true
argument-hint: "<idea, issue number, or map issue>"
metadata:
  kind: shaping
  calls: "investigate, shape-architecture"
  role: builder
  consumes: "a loose idea, a conversation, or a map issue"
  produces: "a spec issue labeled spec, or a map issue labeled map with its decision issues; access/<app>.md in the project folder for a surface without a driver"
  hypothesis: "Without a spec, the builder under-scopes the work; without an interview, the spec carries the agent's guesses instead of the user's decisions."
---

# Shape spec

Read [the constitution](../constitution/README.md) first, and `~/.agents/projects/<project>/issue-tracker.md`: this skill publishes to the tracker. Without that file, write the default tracker as the constitution says, and tell the user the spec stays private until `/setup-repo` moves it to a tracker the team sees.

You turn what the user wants into decisions, then into a spec. You do not write product code. The spec is product-level: a technical error in a spec cascades through the whole build, so the spec names behavior and decisions, not files. The shape of the code is the builder's, unless the user settles it with `shape-architecture`.

You do not cut the spec into implementation slices for parallel agents. One builder carries the spec; when it is large, the builder lands it as an ordered series of PRs with the `bespoke` playbook. Work that looks independent turns out tangled, and only a builder holding the whole spec sees how.

## Steps

1. **Pick the mode.** From what the user brings:
   - a loose idea, or a plan with open decisions: **grill**, then **spec**;
   - a spec issue with an open product decision: **grill** it, then edit the spec in place;
   - a conversation that already settled the decisions: **spec** directly;
   - work too big for one session, where the way to the goal is not visible yet: **map**;
   - a map issue: **map**, working its next decision.

   A question of fact a run can answer, such as a timing, is not the user's to decide: run [investigate](../investigate/SKILL.md) in prototype mode, and the observation decides. A question of look or feel gets a prototype too, but the user picks from its variants.

   When a story is a heavy visual change, as the [glossary](../constitution/references/glossary.md) defines it, say why: the grill adds its design mode and a pick among prototypes, which becomes visual targets. A small change on an existing screen takes none, and follows the design system as it is.
   Done when: the mode is named to the user with the reason, and whether the change is a heavy visual one.

2. **Grill.** Interview the user in rounds, as [references/grill.md](references/grill.md) describes, and keep the repo's domain model up to date as [references/domain.md](references/domain.md) describes. Facts are your job; decisions are the user's. Subagents read the code; you do not.
   Done when: no open decision is left, every story has a journey and every promise its harm, and what cannot be verified is named, all confirmed by the user, a heavy visual change has its design mode and a visual target the user picked, the drivers and formal checks of the area are looked up, the access for any surface without a driver is written down, every resolved term is in the repo glossary, and the user confirmed you share the same understanding.

3. **Write the spec.** Follow [references/spec.md](references/spec.md): problem, solution, `done_when` agreed with the user, user stories with their journeys, promises, visual targets, what is not verifiable, the seams to test at, decisions, technical decisions, testing decisions, out of scope. Check the seams with the user, then publish it as an issue labeled `spec`.
   The docs PR goes through a verdict and `babysit-pr`, as rule 2 of the constitution says.
   Done when: the issue exists and links the docs PR that holds the glossary terms and ADRs, the user approved the seams, and every numbered journey, promise, and visual target can become a case in `frame`.

4. **Map.** For work too big for one session, chart or work the map as [references/map.md](references/map.md) describes. Resolve at most one decision per session, except research.
   Done when: charting: the map issue and its first decision issues exist, wired by blocking links. Working: one decision is resolved, recorded on the map, and the fog it cleared is turned into new decision issues.

5. **Hand over.** When the spec is ready, spawn a fresh subagent to look in the code it touches for the signals [shape-architecture](../shape-architecture/SKILL.md#when-it-is-worth-it) lists. With one, name it and why, and ask whether to settle the architecture now: on a yes, run shape-architecture in this session. Otherwise, give the user the issue link and the next command, `/ship <issue>`, and say that the builder picks the shape alone. A spec too large for one PR names the `bespoke` playbook. A finished map hands over its destination: usually a spec, sometimes a decision.
   Done when: the user has the link and the next command, or shape-architecture runs on their yes.

## Reply

The mode, the decisions made and who made them, the design mode and the visual targets picked, the terms added to the glossary, the ADRs written, the drivers and formal checks found (stale ones named) and the access collected, the spec or map link, the architecture signals found and whether the architecture was shaped, and what is still open.
