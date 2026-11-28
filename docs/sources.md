# Where the skills come from

Skills name no external source: an agent that read "Matt Pocock `grilling`" in a skill could go find that skill and leave the framework. The linter forbids it (P005, [ADR 0007](adr/0007-no-external-sources-in-skills.md)). Attribution lives here instead: for each file, the attribution text removed from it on 2026-11-19, as it was. The originals are in `knowledge/sources/`.

When a skill changes, update its section here, in the same PR.

## `skills/add-guardrail/SKILL.md`

- Source: pstack `correct`, Lauren Tan's inverted pyramid.
- (Matt Pocock `retro`)

## `skills/add-guardrail/references/levels.md`

- Source: pstack `correct`, Lauren Tan.

## `skills/analyze-impact/SKILL.md`

- Source: pstack `blast-radius`.

## `skills/analyze-impact/references/where-grep-stops.md`

- Source: pstack `blast-radius`.
- 2026-11-23: ours, [ADR 0017](adr/0017-a-formal-check-guards-every-task-that-touches-its-code.md): the Formal checks row runs the check as the PR updated it, and a check stale on the base proves nothing.
- 2026-11-24, [ADR 0019](adr/0019-the-spec-sets-the-bar-and-a-task-builds-the-proof-it-lacks.md), ours: a check stale on the base is repaired by the task before the change; only a failed repair leaves an issue to name.

## `skills/babysit-pr/SKILL.md`

- 2026-11-23: ours, [ADR 0018](adr/0018-a-verdict-covers-the-tested-base-and-head.md), based on our executed counterexample: an unchanged patch id after a conflict-free rebase can hide changed behavior. Verdicts record full base and head SHAs, rules, and replay setup; reuse follows that identity.

- 2026-11-20: one push per round and the stack rules (the lowest PR first, one babysitter per stack, fixes in the owning PR, the stack's shape kept), from pstack `poteto-mode` babysit playbook. Adapted: rebasing the PRs above after the lowest one is rebased stays the babysitter's job, since our builder owns the stack.
- Source: tstack `babysit-pr`, pstack `shipping`.
- (pstack `babysit`)
- (tstack `full-send`)
- 2026-11-20, from the coherence audit: a verdict requested when none covers the head, and `ready` removed when the patch id moved, from pstack `shipping` ("verify each PR independently before it lands", "Compare git patch-id at the verdict SHA with the current head"). The stack rules moved to `references/stack.md`.
- 2026-11-20, second coherence audit: a FAIL during babysit is fixed or disputed within the PR's 2-FAIL budget; without a PR watcher, a bounded check every 5 to 10 minutes for 2 hours, as pstack's `watch-pr` polls (ours: the bound).

## `skills/babysit-pr/references/stack.md` (2026-11-20)

- Source: pstack `poteto-mode` babysit playbook: the frontier, one babysitter per stack, the owner who babysits its own PR and rebases its own branch ("An Autopilot owner babysitting its own PR is that owner"), and the rebase reported to the owner (Lauren Tan).

## `skills/catch-me-up/SKILL.md` and its references (2026-11-20)

- Source: pstack `ketchup`, and `ketchup-video` for the video mode (Lauren Tan), condensed. Adapted: the window can be a set of PRs or a new session, since our tasks end in PRs; the reply leads with the PRs' demo videos.

## `skills/clean-worktrees/SKILL.md` (2026-11-20)

- Source: pstack `poteto-mode` worktree-cleanup playbook and its `worktree-audit.sh` (Lauren Tan). Adapted: the generic part only, without iOS simulators and editor caches; a worktree touched in the last 24 hours counts as in use, since our harnesses have no list of pinned chats.

## `skills/constitution/README.md`

- (pstack `poteto-mode`)
- 2026-11-20, rules 11 to 13 (ADR 0014): pstack `poteto-mode` Autonomy and Non-negotiables ("don't wait for confirmation", "broken skill mid-task"), and its `autonomous-run` playbook (mid-run discoveries are yours, out-of-band fixes in their own PR, a plateau is not a stop, never relax the predicate). Adapted: a framework skill that is wrong goes to `/learn-from-mistakes`, since a target repo cannot edit the installed plugin.
- 2026-11-20, Reading a principle: pstack `poteto-mode` ("Read the leaf skill in full for any principle you apply", "Cite only principles whose leaf SKILL.md you read this session") and `poteto-agent` ("Navigate to a leaf principle skill whenever you apply that principle"). Ours: never a whole group of the index, and the W002 budget in `tools/lint_skills.py`, since our full forms are longer than pstack's.
- 2026-11-20, from the coherence audit: rule 12 narrowed to what blocks the goal, from pstack `orchestrate` ("Keep only the fixes that block the program, and park the rest as follow-ups"); rule 2 extended to every PR a skill opens, from pstack `shipping`; principles in plain words in the decision log, from pstack `show-me-your-work` (ADR 0015).
- 2026-11-20, third coherence audit: a stop says the call in plain words, a recommended default, and what the user could say instead, keeps working on the rest, and the user's answer in their own words restarts it, from pstack `poteto-mode` ("apply a default, report it with a full explanation, and say in plain words what the operator could tell you to do instead. The operator answers in their own words. Never give a shorthand token to type back") and `babysit` ("Surface the escalation and keep working the rest"). Ours: the `needs-human` label stays as a visible marker.
- 2026-11-24, [ADR 0019](adr/0019-the-spec-sets-the-bar-and-a-task-builds-the-proof-it-lacks.md), ours: rule 11 stops for access only the user can give that no earlier step collected.

## `skills/constitution/references/languages/typescript.md` (examples, 2026-11-20)

- The Examples section condenses pstack `typescript-best-practices/references/patterns.md` (Lauren Tan).

## `skills/constitution/references/writing.md` (2026-11-20)

- Source: pstack `technical-writing` (its three top rules, Google developer style, STE, Global English, the Diataxis modes, and its worked example) and `unslop` (the pattern catalog), condensed (Lauren Tan).

## `skills/constitution/references/coverage.md`

- Source: Lauren Tan ("our code review process has now really shrunk into looking at verification artifacts instead. So things like videos, screenshots, diagrams"), pstack `create-verification-skill` (feature map), pstack `statechart`.
- (pstack `ketchup-video`)
- 2026-11-23: ours, [ADR 0017](adr/0017-a-formal-check-guards-every-task-that-touches-its-code.md): a formal check stale on the base proves nothing, so its case goes under Not verified.
- 2026-11-24, [ADR 0019](adr/0019-the-spec-sets-the-bar-and-a-task-builds-the-proof-it-lacks.md): one case per journey and per promise of the spec, by its id; a case below its target says why. The journeys follow Ray Amjad's account of Anthropic's practice; the rest is ours.
- 2026-11-25, [ADR 0020](adr/0020-a-heavy-visual-change-is-specified-by-a-target.md), ours: one case per visual target.

## `skills/constitution/references/decision-log.md`

- Source: pstack `show-me-your-work` (Lauren Tan).
- 2026-11-22: activity-first reconstruction comes from pstack `poteto-mode/playbooks/eval.md`, step 6; checking results as well as reads is our adaptation. Observed failures and the approved correction set are recorded below under First-use corrections.
- 2026-11-25, [ADR 0020](adr/0020-a-heavy-visual-change-is-specified-by-a-target.md), ours: the target loop keeps a log, one row per pass, as `hillclimb` keeps one per attempt.

## `skills/constitution/references/harness.md`

- 2026-11-20, Model per role: pstack `setup-pstack` and the "Match the model to the job" rules of `poteto-mode` (Lauren Tan). Adapted: roles map to the models of one subscription, Claude or Codex, never across providers; an override is a line in the user's agent file instead of a generated rule file.
- (tstack)
- 2026-11-20, second coherence audit: the verifier's verdict keeps ADR 0003's other family when the harness offers one.
- 2026-11-25, [ADR 0020](adr/0020-a-heavy-visual-change-is-specified-by-a-target.md): the capability to search real UI references, after the MCP server of captured sites Eric Tech's video recommends, and the browser tool it shows; the fallbacks, the capability to record a page and cut a video into frames (after Cook's frame extraction), and the critics' row in Model per role are ours.

## `skills/constitution/references/languages/typescript.md`

- Source: pstack `typescript-best-practices` (Lauren Tan).

## `skills/constitution/references/parallel.md`

- Source: pstack `arena` and `swarm` (Lauren Tan). Adapted: runners come from the harness's model families (see [harness.md](../skills/constitution/references/harness.md)), not from a model config file.
- 2026-11-20: the arena removed. The user runs on one subscription, not a panel of models, so the builder sketches a design twice itself.

## `skills/constitution/references/pr-format.md`

- 2026-11-20: Why opens with who notices and what the next maintainer inherits, from pstack `poteto-mode` "Frame impact for the consumer and the maintainer".
- (pstack `opening-a-pr`)
- 2026-11-20: the Design section, from pstack `architect`, whose rationale ships beside the sketch.
- 2026-11-20: the task's issue linked at the top, `Closes` on the PR that completes it and `Part of` on an earlier unit. Ours: pstack has no linking rule; the closing keywords are GitHub's and GitLab's own.

## `skills/constitution/references/principles.md` and `principles/`

- Most ids come from pstack (Lauren Tan, `cursor-pstack`), where each one is a full skill (`principle-<name>`). Since 2026-11-20, `principles.md` is the one-line index and `principles/<id>.md` holds the full form, condensed from the pstack skill.
- Ours: the uniform shape of every full form (Apply when, Rule, How, Test, Sign it was skipped, Example), so the builder applies a principle and the verifier judges it with the same test; and the ids renamed to say what they do, as skill names do.
- Renamed on 2026-11-20, with the pstack name each came from: `design-the-data-first` (pstack `foundational-thinking`), `validate-at-the-boundary` (pstack `boundary-discipline`), `make-illegal-states-unrepresentable` (pstack `type-system-discipline`), `make-the-smallest-change` (pstack `laziness-protocol`), `design-for-the-consumer` (pstack `experience-first`, added), `build-a-tight-loop` (ours, was `tight-loop`).
- `prove-it-works`: pstack
- `build-a-tight-loop`: Matt Pocock `diagnosing-bugs`
- `test-behavior-not-implementation`: pstack, Matt Pocock `tdd`
- `explain-the-number`: pstack
- `verify-at-the-edge`: Ray Amjad, Anthropic "harness design"
- `fix-root-causes`: pstack
- `attack-the-premise`: pstack
- `encode-lessons-in-structure`: pstack, Lauren Tan. 2026-11-24, ours: it also applies before a decision or a rule is written in a doc, and an ADR keeps only what the code cannot say.
- `build-the-lever`: pstack
- `design-the-data-first`, `redesign-from-first-principles`, `design-for-the-consumer`: pstack, added 2026-11-20
- `model-the-domain`: pstack
- `design-it-twice`: pstack `architect` and `principle-exhaust-the-design-space`
- `migrate-callers-then-delete`: pstack
- `minimize-reader-load`: pstack
- `make-illegal-states-unrepresentable`: pstack, with the examples of its TypeScript skill
- `validate-at-the-boundary`: pstack
- `make-the-smallest-change`: pstack
- `subtract-before-you-add`: pstack
- `sequence-verifiable-units`: pstack
- `scope-stays-put`: tstack `council`, pstack
- `guard-the-context-window`: pstack
- `make-operations-idempotent`: pstack
- `separate-before-serializing-shared-state`: pstack
- `never-block-on-the-human`: pstack
- `keep-the-codebase-clean`: Lauren Tan
- Not taken: pstack `principle-outcome-oriented-execution`, which accepts broken intermediate states; our units each land green, and a wide change uses expand, migrate, contract.
- The opening assumption of the red flags, an agent that sees only the files it opened, comes from pstack `architect` and `correct`.

## `skills/constitution/references/proof.md`

- Sources: tstack `full-send` (proof), pstack `principle-prove-it-works` and `blast-radius` (certainty levels), Matt Pocock `diagnosing-bugs` (red loop), Ray Amjad and Anthropic "harness design" (verify where the model is weakest).
- (pstack: "a small, obvious edit doesn't" need full rigor)
- (Ray Amjad: "you don't really need a verifier to like verify that the contact form submits"; Anthropic "harness design": the evaluator "is worth the cost when the task sits beyond what the current model does reliably solo")
- 2026-11-20, from the coherence audit: a missing driver is not a pass, from pstack "'Inconclusive' or wrong-surface is not a pass" and `autopilot-full` ("The verdict is not clean without the live lane"); a user-facing `low` change is proven on the app, from pstack `poteto-mode` ("Shipping UI: the matching control skill").
- 2026-11-23: ours, [ADR 0017](adr/0017-a-formal-check-guards-every-task-that-touches-its-code.md): every file a formal check covers is a hard zone; where formal checks live and how a diff finds them, beside the drivers.
- 2026-11-24, [ADR 0019](adr/0019-the-spec-sets-the-bar-and-a-task-builds-the-proof-it-lacks.md): a missing driver is built as the task's first unit, from Ray Amjad (the agent installs what it lacks during the task); the targets, a level for a journey and a breadth for a property, are ours, since no source sets them by kind of case.
- 2026-11-25, [ADR 0020](adr/0020-a-heavy-visual-change-is-specified-by-a-target.md), ours: a visual target, still or motion, reaches level 5, and a judged score stays level 1, after Cook's split between measured and eyeballed numbers.

## `skills/constitution/references/target-repo.md` (where skills and instructions live, 2026-11-19)

- Agent Skills, "How to add skills support to your agent": "The `.agents/skills/` paths have emerged as a widely-adopted convention for cross-client skill sharing. While the Agent Skills specification does not mandate where skill directories live…" <https://agentskills.io/client-implementation/adding-skills-support>
- Claude Code, Skills: project skills in `.claude/skills/`; "a `<skill-name>` entry in the enterprise, personal, or project location can be a symlink to a directory elsewhere on disk". <https://code.claude.com/docs/en/skills>
- Claude Code, Memory: reads `AGENTS.md` when no `CLAUDE.md` exists (v2.1.277+), and "Not read: … anything under a `.agents/` directory". <https://code.claude.com/docs/en/memory>
- Codex, Build skills: "Codex scans `.agents/skills` in every directory from your current working directory up to the repository root", "supports symlinked skill folders", and `agents/openai.yaml` `policy.allow_implicit_invocation`. <https://learn.chatgpt.com/docs/build-skills>
- 2026-11-24, [ADR 0019](adr/0019-the-spec-sets-the-bar-and-a-task-builds-the-proof-it-lacks.md), ours: `access/<app>.md` is never shared, since it says where a secret lives.

## `skills/constitution/references/formal.md`

- Source: pstack `create-formal-verification-skill` (What makes it good, Let the question choose the tool) and `maintain-formal-verification-skill` (Edit scope, update from the code) (Lauren Tan).
- 2026-11-23: our adaptation: the rules shared by creation, maintenance, and a builder's update in one file; the shape of `prove-<area>`; the definition of a stale check, from pstack's sync commit.
- 2026-11-23: ours, [ADR 0017](adr/0017-a-formal-check-guards-every-task-that-touches-its-code.md): In a task, staleness compared by content, not history, and where a private harness runs.
- 2026-11-24, [ADR 0019](adr/0019-the-spec-sets-the-bar-and-a-task-builds-the-proof-it-lacks.md), ours: a stale check is repaired as the task's first unit, a promise the user stated in a hard zone gets a check, and a private check's base version is saved for the verifier. pstack's rule that a verification update ships in a change of its own is kept for shared checks.

## `skills/constitution/references/statechart.md`

- Source: pstack `statechart` (Lauren Tan). Adapted: pstack ships a script that runs TLC and draws the chart; here the method is described and the tool is the repo's, or TLC run directly.

## `skills/constitution/references/architecture.md` (2026-11-27)

- [ADR 0024](adr/0024-the-architecture-is-shaped-apart-from-the-intent.md), ours: steps 1 to 4 of `skills/ship/references/design.md` and its red flags move here, so `ship` and `shape-architecture` follow one method. The screen now keeps both sketches, and the pick and its fold-in stay in `ship`. Their sources stay those listed under `skills/ship/references/design.md`.

## `skills/constitution/references/ui.md` (2026-11-25)

- [ADR 0020](adr/0020-a-heavy-visual-change-is-specified-by-a-target.md). Criteria to grade against instead of "is it beautiful", and the four criteria, from Anthropic "harness design". The generic defaults to drop, from Cook's slop ban list (`references/rules.md`) and the Taste Skill's Never list. One system, every width down to 320, tap targets of 44px, every control answering the pointer, and reduced motion where everything rests and nothing stays hidden, from the Taste Skill's checklist. The contrast ratios, 4.5:1 and 3:1, from WCAG 2.2 (1.4.3, 1.4.11). Layout before motion, from Eric Tech's video. The design system read from the code, the design modes, the motion criteria, and the 20% tolerance on an effect's duration are ours.

## `skills/create-app-driver/SKILL.md`

- 2026-11-20: the control CLI (`references/drivers.md`) and the template's "add a command, not a throwaway script", from pstack guide page "Verify the result and open a PR" (Lauren Tan).
- Source: pstack `create-verification-skill` and `maintain-verification-skill`.
- 2026-11-23: the formal mode moved out to `create-formal-verification` and `maintain-formal-verification`.
- 2026-11-24, [ADR 0019](adr/0019-the-spec-sets-the-bar-and-a-task-builds-the-proof-it-lacks.md): the skill reads the access `shape-spec` collected; inside a task, a fresh subagent follows the driver cold, after Ray Amjad's checker that makes sure the driver did not cheat.
- 2026-11-28, [ADR 0025](adr/0025-the-feature-map-grows-by-maintenance.md): the maintain mode moved out to `maintain-app-driver`, and the entry-point check is gone: the map starts with 3 to 5 features and grows by maintenance, as in pstack `create-verification-skill` ("aim for the top 3-5 to start", "the map exists so later runs can cover the rest"). The stand-in rule and "mocks only where a production boundary already isolates the external system" come back from it. A browser control CLI before a shipped script, after pstack's `control-ui` (`poteto-mode` multi-phase-plan playbook). Ours: a seed for a state no user path reaches, beside the driver, without asking; the driver's tools never in the repo's manifest.
- 2026-11-28: from pstack `create-verification-skill`: the repo's own documented dev command first, the primary surface picked and the others noted; from `maintain-verification-skill`: one long-lived instance driven serially, and one retry that restarts only what the fix invalidated. pstack writes no demo at creation; with [ADR 0019](adr/0019-the-spec-sets-the-bar-and-a-task-builds-the-proof-it-lacks.md), the first task that requires one adds it. Ours, after a 50-minute first run on a Next.js and Postgres repo on Windows: the preflight before any install, with a per-run runtime selector rather than a changed default, the `Windows hosts` recipes, each run in Git Bash on Windows 11 with Windows PowerShell 5.1 and PowerShell 7, a `Profile` line only when cheap, the side by side question answered from the code and proven by the first task that needs it, and a control CLI that starts with four commands.

## `skills/create-app-driver/references/feature-map.md`

- Source: pstack `create-verification-skill`, example `create-note.md`.
- 2026-11-28: the header of `features/README.md` (the baseline every recipe starts from, "never drive an instance that was not started by this verification run", restore seeded data after a mutation, what a UI and a CLI proof hold, a skipped entry point never verified through a different path), and the feature and entry point in every evidence file name, from pstack's example `feature-map-example/README.md`.

## `skills/maintain-app-driver/SKILL.md` (2026-11-28)

- Source: pstack `maintain-verification-skill` (Lauren Tan), which this repo first kept as `create-app-driver`'s maintain mode: the index, the read-only source wave, the reconcile, the live pass with its three invariants, the triage, and the three outcomes. pstack guide page "Verify the result and open a PR": run it often. Ours, [ADR 0025](adr/0025-the-feature-map-grows-by-maintenance.md): each pass maps up to five missing features, those `learn-from-mistakes` named first; the user launches it, by hand or from a schedule of their own ([ADR 0026](adr/0026-a-schedule-is-the-users-own.md)). The rule that a prerequisite the map omits is drift, from pstack.

## `skills/create-formal-verification/SKILL.md`

- Source: pstack `create-formal-verification-skill` (Lauren Tan): choose the strongest target from the code, the question picks the tool, show it can fail, findings stay findings, follow the generated skill once on a scratch break before the handoff, the handoff list.
- 2026-11-23: ours: the follow-it-cold run is done by a fresh subagent that holds only the path of `prove-<area>`; a shared check goes through a verdict and `babysit-pr`; no driver is required first.
- 2026-11-23: ours, [ADR 0017](adr/0017-a-formal-check-guards-every-task-that-touches-its-code.md): a shared check also runs in the repo's CI.
- 2026-11-24, [ADR 0019](adr/0019-the-spec-sets-the-bar-and-a-task-builds-the-proof-it-lacks.md), ours: run before a task's change, a shared check leaves `babysit-pr` to the task's stack, as the bespoke playbook does.

## `skills/maintain-formal-verification/SKILL.md`

- Source: pstack `maintain-formal-verification-skill` (Lauren Tan): the four outcomes, run before changing anything, the four kinds of change, update from the code and not from the result, re-break after a pass, replay a counterexample to tell drift from a bug, the sync commit rules, the report.
- 2026-11-23: ours: a builder's own change to covered code is handled in its run, so this pass covers the changes that skipped the check; each bug becomes an issue; the issue opened by `analyze-impact` for a stale check is closed or linked.
- 2026-11-24, [ADR 0019](adr/0019-the-spec-sets-the-bar-and-a-task-builds-the-proof-it-lacks.md), ours: a task runs this pass on a check stale on its base, before the change, and leaves `babysit-pr` to its stack.

## `skills/investigate/SKILL.md`

- Sources: pstack `poteto-mode` investigation, runtime-forensics, trace-forensics, and prototype playbooks, `how`, `why` (Lauren Tan). Grouping them in one skill is ours: they share an answer as output, and none of the steps that lead `ship` to a PR.

## `skills/investigate/references/diagnosis.md`

- Source: pstack `poteto-mode` runtime-forensics and trace-forensics playbooks (Lauren Tan), merged here.

## `skills/investigate/references/prototype.md`

- Source: pstack `poteto-mode` prototype playbook and `principle-exhaust-the-design-space` (Lauren Tan).
- 2026-11-25, [ADR 0020](adr/0020-a-heavy-visual-change-is-specified-by-a-target.md): the user's references first, then a library of real product screens, from Cook's "no references yet" path; a motion reference read frame by frame into an effect list, and no element copied one to one, from Cook (`references/target-and-bar.md`); describing how a part was built when the user cannot name a problem, from Cook (`references/loop-and-critics.md`); three variants checked at a phone width, from Eric Tech's video. The repo's real components under follow and extend, the recordings, and narrowing after three showings are ours.

## `skills/investigate/references/question.md`

- Source: pstack `poteto-mode` investigation playbook, `how`, and `why` (Lauren Tan).

## `skills/learn-from-mistakes/SKILL.md`

- Sources: pstack `reflect` (three lenses, a synthesizer, approval before any edit), Matt Pocock `retro` (categories of improvement; standards belong to the review agent), Lauren Tan (a correction becomes a check, not a rule).
- 2026-11-22: reconstruct session activity before trusting summaries, from pstack's evaluation transcript check; see First-use corrections below.

## `skills/learn-from-mistakes/references/reviewers.md`

- Source: pstack `reflect` reviewer prompts; the tooling lens also takes Matt Pocock `retro` categories.

## `skills/learn-from-mistakes/references/routes.md`

- Source: our verification layers (design note 02, section 5, removed with `docs/history/` by ADR 0022); Matt Pocock `retro` for the target repo files.
- (Matt Pocock `retro`)
- 2026-11-23: ours, [ADR 0017](adr/0017-a-formal-check-guards-every-task-that-touches-its-code.md): the formal check route.

## `skills/learn-from-mistakes/references/synthesis.md`

- Source: pstack `reflect` synthesizer.

## `skills/pause-task/SKILL.md` (2026-11-20)

- Source: pstack `poteto-mode` pause-safely playbook (Lauren Tan). Adapted: the resume note goes in the `wip:` commit body and on the open PR, where a later session finds it, instead of a temporary file; the pause also triggers on a usage limit, since the user runs on a subscription.
- 2026-11-20, from the coherence audit: a task with no branch writes its note to a file outside the repo, as pstack `pause-safely` does ("write it to a file like /tmp/<slug>-resume.md"); the decision log's rows go into the note, since the log lives out of git.

## `skills/recall-context/SKILL.md` (2026-11-20)

- Source: pstack `recall` (Lauren Tan): the two records, the scope fixed first, the fan-out over transcripts, the sweep of the shared record, the brief's contract and its tags. Adapted: transcripts found where the harness keeps them, the bulk-reading model of the Model per role, the repo's issue tracker.

## `skills/resume-task/SKILL.md` (2026-11-20)

- Source: pstack `poteto-mode` session-pickup playbook (Lauren Tan). Adapted: the trail starts from the `wip:` commit and the PR; the task continues without asking (ADR 0014).

## `skills/ship-queue/references/owner-brief.md` (2026-11-20)

- Source: pstack `orchestrate` ("Each kickoff names the evidence that proves the work is done... the paths the worker may and may not write") and `autopilot-full` (push early, push each finished unit), adapted to an owner that runs `ship`.

## `skills/ship-queue/SKILL.md` (2026-11-20)

- Source: pstack `poteto-mode` autopilot-stack and autopilot-full playbooks, and orchestrate for the supervision rules: start with one unit, judge agents by side effects, replace a stuck one with a consolidated brief (Lauren Tan). Adapted: no merge and no merge prep; each owner runs `ship`, whose fresh verifier gives the verdict, instead of a root swarm; at most three owners at once, for a subscription; no cloud agents.
- 2026-11-20, from the coherence audit: two replacements per task, then `needs-human`, from pstack `orchestrate` ("After two retries, drop the unit and replan around it"); each owner babysits its own PR, from pstack `babysit`.

## `skills/say-it-plainly/SKILL.md` (2026-11-20)

- Source: pstack `bro` (Lauren Tan).

## `skills/sharpen-prompt/SKILL.md` (2026-11-20)

- Source: pstack `sharpen` (Lauren Tan), nearly as is.

## `skills/setup-repo/references/trackers/` (an issue tracker of any kind, 2026-11-19)

- Matt Pocock `setup-matt-pocock-skills`: "Those files are the only thing that varies between repos. The skills themselves are identical everywhere. They read `docs/agents/issue-tracker.md` at run time and do what it says." Templates for GitHub, GitLab, and local markdown, and an "Other" option in prose for Jira, Linear, and the rest (`knowledge/sources/repos/mattpocock-skills/repo/docs/engineering/setup-matt-pocock-skills.md`).
- Matt Pocock, ADR 0001: an explicit pointer to the setup only in the skills that truly depend on it (`.agents/adr/0001-explicit-setup-pointer-only-for-hard-dependencies.md`). Adopted for `shape-spec` and `learn-from-mistakes`.
- The `gh` and `glab` commands of the templates are adapted from his `issue-tracker-github.md` and `issue-tracker-gitlab.md`.

## `skills/setup-repo/references/trackers/` (linking a PR, 2026-11-20)

- Ours: the operation "Link a PR to the issue it delivers", with each tracker's own form (GitHub and GitLab closing keywords, a `PR:` line in a local file).

## `skills/shape-architecture/SKILL.md` and its references (2026-11-27)

- [ADR 0024](adr/0024-the-architecture-is-shaped-apart-from-the-intent.md), ours: the architecture shaped apart from the intent, the four signals that make a run worth it, every question that can be left to the builder, the Technical decisions section, and `ship` building within it.
- The rounds and the frontier of `references/questions.md` come from `shape-spec`'s grill, so from Matt Pocock `grilling`. The design method, sketching in code and the red flags, comes from pstack `architect` (Lauren Tan), through `skills/constitution/references/architecture.md`.
- 2026-11-28, ours, from a first run on a real codebase: without a spec issue, the skill stops and sends to `/shape-spec` instead of writing the spec.
- 2026-11-28, [ADR 0027](adr/0027-behavior-is-settled-in-the-spec-the-shape-in-the-architecture.md), ours: a product decision the spec lacks is sent back to `/shape-spec`, never asked here.

## `skills/shape-spec/SKILL.md`

- Source: Ray Amjad (splitting a spec into parallel units gives worse results, the work is tangled in ways nobody expected), Anthropic "harness design" (planner kept, sprints dropped).
- Sources for the modes: Matt Pocock `grilling`, `domain-modeling`, `grill-with-docs`, `to-spec`, `wayfinder`.
- (Anthropic kept its planner for this reason)
- 2026-11-20, from the coherence audit: a question of fact is settled by a run, one of look or feel by the user, from pstack `poteto-mode` ("If the answer is a fact you could observe by running something, it is not the human's to answer").
- 2026-11-25, [ADR 0020](adr/0020-a-heavy-visual-change-is-specified-by-a-target.md), ours: the trigger for a heavy visual change, settled with the user.

- 2026-11-27, [ADR 0024](adr/0024-the-architecture-is-shaped-apart-from-the-intent.md), ours: the hand over looks for the signals of `shape-architecture` and offers it.
- 2026-11-28, [ADR 0027](adr/0027-behavior-is-settled-in-the-spec-the-shape-in-the-architecture.md), ours: a spec issue with an open product decision is grilled again and edited in place.

## `skills/shape-spec/references/domain.md`

- Source: Matt Pocock `domain-modeling`.
- 2026-11-24: ours, from pstack's `encode-lessons-in-structure` order (Lauren Tan): an ADR records only what the code cannot say. The code holds the decision first, and the ADR keeps the why.

## `skills/shape-spec/references/grill.md`

- Source: Matt Pocock `grilling` and `grill-with-docs`.
- 2026-11-24, [ADR 0019](adr/0019-the-spec-sets-the-bar-and-a-task-builds-the-proof-it-lacks.md): the verification branch. A journey per story follows Ray Amjad's account of Anthropic's practice, where the spec lists its flows and each is verified separately. Promises, what cannot be verified, and collecting access before the build are ours.
- 2026-11-25, [ADR 0020](adr/0020-a-heavy-visual-change-is-specified-by-a-target.md), ours: a heavy visual change adds two decisions, the design mode and the pick, whose steps are prototype mode's; the visual targets drafted for a yes.
- 2026-11-28, from a first run on a real codebase: a round is a message the user answers in their own words, as Matt Pocock `grilling` sends it, not a form of buttons. Digging into each answer is ours.
- 2026-11-28, from a second run on a real codebase: the round's format, ❓ and ➡️ lines separated by `---`, is Matt Pocock `grilling`'s, as written. The round alone in its message, and the recommendation never inside the body, are ours.
- 2026-11-28, ours, from a third run on a real codebase: the interviewer reads no code itself, and a subagent that returns while a round waits sends nothing new. Three runs with the same skill files and no code to read all kept the format; the run that read the code itself lost it.
- 2026-11-28, [ADR 0027](adr/0027-behavior-is-settled-in-the-spec-the-shape-in-the-architecture.md), ours: the branch What the code already does, whose collisions become the product questions.

## `skills/shape-spec/references/map.md`

- Source: Matt Pocock `wayfinder`.
- That keeps the map clear of the problem Ray Amjad describes: implementation split across agents that turn out to be tangled.

## `skills/shape-spec/references/spec.md`

- Source: Matt Pocock `to-spec`; the link between user stories and cases is ours.
- 2026-11-24, [ADR 0019](adr/0019-the-spec-sets-the-bar-and-a-task-builds-the-proof-it-lacks.md), ours: a journey per story, the Promises and Not verifiable sections, numbered stories and promises, and the journeys' surfaces as seams.
- 2026-11-25, [ADR 0020](adr/0020-a-heavy-visual-change-is-specified-by-a-target.md), ours: the Visual targets section, numbered `V1`, still or motion, with its design mode, measured checks, and bans. The motion target's effect list follows Cook's one line per effect (`references/target-and-bar.md`).

- 2026-11-27, [ADR 0024](adr/0024-the-architecture-is-shaped-apart-from-the-intent.md), ours: the Technical decisions section, numbered `D1`; the Decisions section keeps the product decisions.

## `skills/ship/references/clean.md`

- Source: pstack `no-comments` and its `comment-sicko` agent (Lauren Tan). Adapted: constraint encodings go to `/add-guardrail` instead of an inline approval.
- 2026-11-22: the single retry after an invalid report comes from `no-comments`. Proposal-only patches and retaining uncertain comments until their symbols are traced are our experiment in protecting public contracts; pstack's original deletes on doubt. See First-use corrections below.

## `skills/ship/SKILL.md`, `skills/ship/references/verification.md`, and `skills/ship/scripts/check_evidence.py`

- 2026-11-23: ours, [ADR 0018](adr/0018-a-verdict-covers-the-tested-base-and-head.md), based on our executed counterexample: an unchanged patch id after a conflict-free rebase can hide changed behavior. Verdicts record full base and head SHAs, rules, and replay setup; reuse follows that identity.

- 2026-11-22: pstack `figure-it-out` puts the verification harness before implementation; `poteto-mode/playbooks/eval.md` checks activity rather than self-report; `poteto-mode/scripts/check-plan.mjs` mechanically checks plan structure. Our adaptation checks a local evidence index for certainty levels, nonempty artifact files, step results and traces, and stale verdicts. It cannot judge content or completeness against the original task. Tests live in `tools/test_check_evidence.py`. This is a local task check, not a framework CI gate in target repos (ADR 0001).
- 2026-11-23: ours, [ADR 0017](adr/0017-a-formal-check-guards-every-task-that-touches-its-code.md): build's Done when requires each altered formal check to describe the head.
- 2026-11-24, [ADR 0019](adr/0019-the-spec-sets-the-bar-and-a-task-builds-the-proof-it-lacks.md), ours: the frame builds the proof the task lacks first, and the evidence record lists the spec's ids in `spec_ids`; `check_evidence.py` fails when one is not a case.
- 2026-11-25, [ADR 0020](adr/0020-a-heavy-visual-change-is-specified-by-a-target.md), ours: `check_evidence.py` accepts visual target ids, `V1`, and fails when one has no case. The glossary gains heavy visual change, visual target, effect list, design mode, target loop, and critic.

## `skills/ship/references/design.md`

- 2026-11-19, completed from pstack `principle-model-the-domain`: the small module boundary for invariants, structures chosen by access pattern, lifecycle risk, and the phase-named modules sign. The rule that the data shape takes its names from `GLOSSARY.md` is ours: it ties Matt's vocabulary to Lauren's code-as-truth.
- Source: pstack `principle-model-the-domain`, `architect` and its `design-red-flags.md` (Lauren Tan). Adapted: the arena runs as [parallel.md](../skills/constitution/references/parallel.md) describes, with the harness's model families instead of pstack's model config.
- 2026-11-20, architecture method brought closer to pstack (Lauren Tan, `knowledge/sources/repos/cursor-pstack/`): the method gains grounding in the history of the current shape (pstack `architect` Phase A, which runs `why`), the rules of a sketch (`sketch.md`), the design note (`design-note.md`), the design shown to the user for a one-way door or on request (pstack `architect` Phase C, opt-in there), building against the sketch, and the six tells and the procedure for scrapping it (pstack `architect` Phases D and E). The table of how much design a change needs adapts pstack's guide page "Design before you write code", and designs every feature, as pstack's feature playbook runs `architect` on every feature. Ours: the builder writes both sketches itself instead of an arena of models, and a task scraps once, then `needs-human`.
- 2026-11-25, [ADR 0020](adr/0020-a-heavy-visual-change-is-specified-by-a-target.md), ours: grounding a change to what a user sees reads the design system, as `ui.md` says.

- 2026-11-27, [ADR 0024](adr/0024-the-architecture-is-shaped-apart-from-the-intent.md), ours: steps 1 to 4 and the red flags move to `skills/constitution/references/architecture.md`; the build within the spec's technical decisions is new.

## `skills/ship/references/design-note.md`

- Source: pstack `architect/references/rationale-template.md` (Lauren Tan). Adapted: Synthesis becomes Choice between the builder's two sketches, a Deviations section is filled during the build, and "Next implementation step" is dropped.

## `skills/ship/references/sketch.md`, now `skills/constitution/references/sketch.md`

- Source: pstack `architect/references/runner-prompt.md` (Lauren Tan). Adapted: the builder follows it for both of its sketches, each rule names its principle id, and rule 12 comes from `principle-laziness-protocol`.

## `skills/ship/references/visual-loop.md` (2026-11-25)

- [ADR 0020](adr/0020-a-heavy-visual-change-is-specified-by-a-target.md). The loop is Leon Lin's Cook (`SKILL.md`, `references/loop-and-critics.md`, `references/target-and-bar.md`): one capture per screen state at a fixed width, contact sheets for motion, side-by-side images, at least two fresh critics with only the images and the rubric, the median, one more critic on disagreement, user feedback first, the user's estimate as calibration, a pass that drops a score fixed or reverted. Ours: a third critic when two differ by more than 2 points (Cook uses 1.0); critics run as a race; an unscored pass rather than a self-scored one; a budget of passes per kind of target under rule 7, instead of a time floor, ending `needs-human` only when a measured check still fails; keep or revert past the critics' spread, after `hillclimb`; the decision log outside the repo instead of a `cook/` folder; and scores that steer the build but never the verdict (ADR 0004).

## `skills/ship/references/frame.md`

- 2026-11-20: the frame is shown and the build goes on, as pstack `poteto-mode` restates the goal without waiting (ADR 0014).
- Source: pstack `in-your-own-words`, Anthropic "harness design" (agree on what done means before building), Matt Pocock `tdd` (agree the seams first).
- Source: pstack `poteto-mode` playbooks (Lauren Tan).
- 2026-11-20, second coherence audit: a symptom that will not reproduce goes through `investigate`'s diagnosis and the task goes on or stops, as pstack's bug-fix playbook does ("synthesize the trigger, tighten conditions, or instrument until it fires"); several open decisions stop the task and propose `/shape-spec`, since they are the user's (pstack `poteto-mode`: "Reserve the question for a genuine product or preference call").
- 2026-11-22: try verification setup before building, adapted from `figure-it-out`; see First-use corrections below.
- 2026-11-24, [ADR 0019](adr/0019-the-spec-sets-the-bar-and-a-task-builds-the-proof-it-lacks.md), ours: the frame builds or repairs the proof the task lacks first, and lists each case with its target.
- 2026-11-25, [ADR 0020](adr/0020-a-heavy-visual-change-is-specified-by-a-target.md), ours: `feature` covers a screen to build or redesign, and a heavy visual change with no visual target is proposed `/shape-spec`; `choose-skill` routes a new screen to `/shape-spec` the same way.

## `skills/ship/references/playbooks/bespoke.md`

- Source: pstack `figure-it-out` (Lauren Tan); the wide-change sequence comes from Matt Pocock `to-tickets`.
- (Ray Amjad; Anthropic "harness design" dropped sprints once the model could hold the whole build)
- (pstack `opening-a-pr`)

## `skills/ship/references/playbooks/bug-fix.md`

- Source: Matt Pocock `diagnosing-bugs`, pstack `poteto-mode` bug-fix playbook.
- (pstack)

## `skills/ship/references/playbooks/feature.md`

- Source: Matt Pocock `tdd`, pstack `principle-sequence-verifiable-units`.
- 2026-11-20: duty 2 from pstack `principle-redesign-from-first-principles` and `principle-foundational-thinking`.
- 2026-11-25, [ADR 0020](adr/0020-a-heavy-visual-change-is-specified-by-a-target.md): duty 8. Stills before motion is Eric Tech's lesson 6; running the target loop on each kind is ours, and the loop is described under `visual-loop.md`.

## `skills/ship/references/playbooks/hillclimb.md` (2026-11-20)

- Source: pstack `poteto-mode` hillclimb playbook (Lauren Tan). Adapted: proof duties in the shape of the other playbooks, and a line for the verifier.

## `skills/ship/references/playbooks/perf.md`

- Source: pstack `poteto-mode` perf-issue playbook and `benchmark-checklist` (Lauren Tan).

## `skills/ship/references/playbooks/refactoring.md`

- Source: pstack `poteto-mode` refactoring playbook, `principle-minimize-reader-load`, `principle-migrate-callers-then-delete-legacy-apis` (Lauren Tan).
- 2026-11-20: the target shape per pstack `principle-redesign-from-first-principles`, as the pstack playbook's step 3 names it.

## `skills/ship/references/playbooks/visual-parity.md`

- Source: pstack `poteto-mode` visual-parity playbook (Lauren Tan).

## `skills/show-me/SKILL.md` and its references (2026-11-24)

- Source: the `show-me` skill of humanlayer's skill set (Dex Horthy; [the announcement post](https://www.humanlayer.com/blog/show-me-skill), [the skill page](https://www.skills.sh/humanlayer/skills/show-me)), nearly as is for the catalog of views. Adapted: the catalog moves to `references/views.md` behind a link, the steps and the reply shape are ours, and the HTML artifact opens through the harness's preview instead of a shell `open`.

## `skills/test-skill-change/SKILL.md` (2026-11-20)

- Source: pstack `poteto-mode` eval playbook (Lauren Tan): the blinding rules, the organic prompt, the judge on neutral labels, chain-following graded from what the agent read. Adapted: every run and the judge on the session's model, with no panel of models (ADR 0014 lifts ADR 0002's removal of `eval`).

## `skills/verify-pr/SKILL.md`

- 2026-11-23: ours, [ADR 0018](adr/0018-a-verdict-covers-the-tested-base-and-head.md), based on our executed counterexample: an unchanged patch id after a conflict-free rebase can hide changed behavior. Verdicts record full base and head SHAs, rules, and replay setup; reuse follows that identity.

- Anthropic found that an untuned evaluator finds real issues, then talks itself into approving the work anyway ("harness design").
- 2026-11-22: holding prior diagnoses back until independent findings are saved is our adaptation of the controlled information exposure in pstack's evaluation playbook. Factual startup and access instructions address the observed inaccessible live environment. See First-use corrections below.

## `skills/verify-pr/references/calibration.md`

- (pstack `create-formal-verification-skill`)

## `skills/verify-pr/references/lanes.md`

- Source: tstack `full-send`.
- Source: Anthropic "harness design" (the evaluator drives the live app), pstack `create-verification-skill`.
- Source: pstack `blast-radius`.
- Source: pstack `interrogate`.
- Source: Matt Pocock `code-review` (Spec axis), `tdd`, pstack refactoring playbook.
- Source: Matt Pocock `code-review` (Standards axis, Fowler smells).
- 2026-11-20: the standards lane checks the shape against the red flags, the architecture principles, and the PR's design note, as pstack `architect` holds an implementation to its sketch.
- 2026-11-22: save independent live and breakage results before comparing the PR's evidence, paired with the information exposure change in `verify-pr` above.
- 2026-11-23: ours, [ADR 0017](adr/0017-a-formal-check-guards-every-task-that-touches-its-code.md): the `breakage` lane judges a formal check the change altered, by breaking the guarded code once.
- 2026-11-24, [ADR 0019](adr/0019-the-spec-sets-the-bar-and-a-task-builds-the-proof-it-lacks.md), ours: the brief carries the spec issue, `live` starts from its journeys and promises, `spec` reads its Out of scope, and `breakage` compares a check made or repaired in the task with its base version.
- 2026-11-25, [ADR 0020](adr/0020-a-heavy-visual-change-is-specified-by-a-target.md): `live` captures or records each visual target itself before reading the builder's images, after Anthropic "harness design", whose evaluator drives the live page before scoring. Ours, by ADR 0004: only a measured check, a missing or mistimed effect, or a ban a command detects can be a finding; `spec` counts a component the design mode excludes as unasked; `standards` reads `ui.md` for notes only.

## First-use corrections (2026-11-22)

- Observed session: [Tenant Custom Domain Admin Setup](t3-thread://v2/fbd209eb-b598-4771-a8c0-9e6077a24fde/bfcde634-64f0-4301-a875-2f8135610f6c), including [PR 180](https://github.com/Photo-Platform/photo-platform/pull/180). The analysis and approved recommendations are in [the framework analysis](t3-thread://v2/fbd209eb-b598-4771-a8c0-9e6077a24fde/e217306f-a744-40f4-b8a6-a8e657f835e1).
- The builder denied having run the comment hunter despite recorded activity; required reads and captures were omitted, certainty levels left the defined scale, reviewers lacked live access and saw prior diagnoses, and the hunter proposed protected public-contract deletions. Expected behavior: trace-backed reporting, complete replayable proof, independent findings, and protected keeps. These observations justify the changes above under `SCOPE.md`.
- Routing text in `skills/choose-skill/SKILL.md`, Reference entries in `README.md`, and map labels in `skills/README.md` describe these same corrections; no new skill or dependency edge is introduced. Plugin paths and Codex invocation policies remain valid. These procedures need another real session to measure whether omissions decrease; the script tests only mechanical rejection of the observed evidence defects.

## `skills/verify-pr/references/verdict.md`

- 2026-11-23: ours, [ADR 0018](adr/0018-a-verdict-covers-the-tested-base-and-head.md), based on our executed counterexample: an unchanged patch id after a conflict-free rebase can hide changed behavior. Verdicts record full base and head SHAs, rules, and replay setup; reuse follows that identity.

- Source: tstack severity scale, pstack blocking rule.
- Source: Matt Pocock `code-review` ("documented-standard breaches can be hard"), pstack ("a doc line the PR made wrong").

## `docs/guide.md` (2026-11-20)

- Source: pstack `poteto-help` references `prompting.md` and `recipes.md`, and the guide pages "Route work through /poteto-mode" and "Recipes and pitfalls" (Lauren Tan), rewritten for these skills. Checked by R011, as ADR 0013 asks of a doc.

## The layout of this repo (2026-11-19)

- Source: Matt Pocock's `mattpocock/skills` repo (`knowledge/sources/repos/mattpocock-skills/repo/`): a README that says why and lists every skill linked to its `SKILL.md`; `SCOPE.md` (its bar of an observed failure was dropped on 2026-11-20: a change needs only to fit the ADRs); a bug issue template with the skill, version, and harness; `CHANGELOG.md`; decisions as ADRs; the `AGENTS.md` rule that a skill added or renamed updates every list of skills in the same PR.
- Install: the plugin manifests (`.claude-plugin/plugin.json` listing each skill, `marketplace.json` with the repo as its own source), `agents/openai.yaml` beside each `SKILL.md` with `policy.allow_implicit_invocation: false` (his `.agents/invocation.md`), and `tools/link_skills.py`, adapted from his `scripts/link-skills.sh` (same destinations, same guard against a destination linked into the repo). Ours: shared folders linked beside the skills, a real folder never deleted, the Windows junction fallback, `--dry-run` and `--unlink`.
- Ours: the rule that a doc is either executed or dated ([ADR 0013](adr/0013-a-doc-stays-fresh-by-running-or-by-date.md)), and the ADRs in `docs/adr/`, the folder the framework gives target repos, instead of `.agents/adr/`.

## Verdict validity integration (2026-11-23)

- Ours, [ADR 0018](adr/0018-a-verdict-covers-the-tested-base-and-head.md): `skills/babysit-pr/references/stack.md`, `skills/ship-queue/SKILL.md`, `skills/choose-skill/SKILL.md`, `skills/constitution/references/glossary.md`, and `skills/constitution/references/pr-format.md` follow the base and head identity instead of patch-id reuse. The existing plugin paths and harness entries still apply.
