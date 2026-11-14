# P-30: MREP authorizes its agents by action class and validates their output in five steps

Nov 14, 2026 · @dinky

| Field | Value |
| --- | --- |
| Status | Accepted, November 14, 2026 |
| Amends | P-22 (the write-back gate and the kill switch) and P-26 (what the Genuineness Estimate monitors) |
| Related | [P-03](../roadmap.md) (test money only), [P-23](P-23-aws-platform.md) (AgentCore Policy) and [P-29](P-29-mrep-name-and-path.md) |

## Summary

**MREP authorizes each thing its agents may do by action class rather than by calling an agent autonomous, and every agent-written artifact passes five validation steps before it reaches a reader.** The six safety habits already stop particular failures; what they lack is a single table saying which actions an agent may take alone, which need a person first, and which are forbidden outright. This record adds that table and the validation sequence that goes with it.

The reasoning comes from the DEVOPS INSTITUTE standard's chapter on AI-native delivery (PeopleCert, October 2026, pp. 52–62, 221–222), read as a source of method. None of its text, tables or figures enters this repository or MREP's teaching material, because its license forbids that and P-14 keeps book material out of Git; what follows is MREP's own matrix, written from first principles for a desk that spends money.

## Context

**Risk rises as an agent moves from describing to acting.** The standard separates AI that detects patterns, AI that creates artifacts and AI that takes action, and it argues for tightening control as the consequences of a wrong action grow (p. 54). MREP has all three: Nova-tier generators draft, a cross-vendor judge classifies, and payment agents spend. Only the last can lose money, so only the last needs the strictest treatment.

**A blanket label is the failure mode.** Authorizing "an autonomous research agent" says nothing about which tools, data and environments it may touch, what must be true before it acts, or who answers for the result. Naming each class of action does (p. 54).

**Generated work outruns the capacity to review it.** The standard names an anti-pattern in which a team takes fast generation as a reason to review less, so defects move downstream while review capacity stays flat (p. 58). A one-person desk building with coding agents is the extreme case of this, which is why the business plan puts the evaluation suite ahead of the classifier.

**Irreversibility is the dividing line.** The standard reserves its strictest class for actions whose consequences cannot be made acceptably reversible, and it says a kill switch counts only once ownership, access and recovery have been rehearsed rather than merely built (p. 55). A settled on-chain payment cannot be recalled, and a published accusation against a named party cannot be unpublished.

## Decision

**Every action an MREP agent can take belongs to one of four classes.**

| Class | Examples at MREP | Who decides | Minimum control |
| --- | --- | --- | --- |
| Advisory | Reading Base and Tempo ledgers, pulling warehouse rows, summarizing a protocol change, proposing a test | The agent proposes, a person decides | Read-only access, a source link for every claim, uncertainty stated, output retained |
| Assisted | Drafting a brief, a scorecard row, a lesson or a quarterly Genuineness Estimate | A person reviews and signs before anything is published | Scoped access, no direct publication, the approval recorded with the artifact |
| Bounded automated | Spending test money on a testnet, running the signal code, rebuilding payments from events, opening a draft pull request | A person pre-authorizes the class and reviews the exceptions | A pre-approved pattern with a fixed prompt and model version, least privilege, preconditions checked before and results verified after, a per-run cost ceiling, rollback, and an audit trail |
| Forbidden | Signing any mainnet transaction, publishing a verdict that a named address, agent or business is fake, changing the scoring method without a new version, publishing any estimate without a human signature | No one; the capability is not granted | Denied in AgentCore Policy, not merely discouraged in a prompt, and the denial itself is tested |

**The forbidden row restates three existing rules rather than adding new ones.** Mainnet spending is already barred by the test-money rule, a public verdict on a named party by P-26's rule R17, and an unversioned method change by P-26's versioning requirement. Collecting them in one row makes the boundary legible to a reader and checkable in one place.

**Every agent-written artifact passes five steps before a reader sees it,** which is the write-back gate of P-22 stated in full:

1. **Provenance.** Which agent, model and prompt version produced this, from which sources, at what time.
2. **Human review.** A person reads the claim and the reasoning behind it, not only its formatting.
3. **Automated checks.** The Compliance judge's rules, the test-set gate and the staleness check run and must pass.
4. **Risk controls.** The named-party check, the cost ceiling and the network check run last, because these are the ones whose failure cannot be repaired after publication.
5. **Evidence.** The release manifest records the sources, the checks, the decision and the person who made it.

**The outcome is accept, rework or reject, and rejecting is a normal result.** An output that is shallow, unsafe or more expensive to fix than to rewrite is thrown away without that counting against the agent or the tool (p. 57).

**The kill switch is rehearsed, not merely wired.** P-22 requires a kill switch; this record requires a drill before each rung gate in which the founder revokes payment tools, confirms the deny takes effect on the next call, and restores service, with the result written to the near-miss log.

## What the Genuineness Estimate monitors about itself

**Three measures are added to P-26's method, because a classifier that is not watched decays quietly** (pp. 221–222).

- **Drift.** An alarm fires when the genuine share moves sharply between runs. Because a change in the world and a change in the method look identical in the output, the previous quarter is rerun under the new method version to tell them apart.
- **Decision quality.** The rate at which the founder overrides a draft classification is recorded. A rate that falls toward zero is read as a warning of over-trust or of review that has become a formality, not as evidence that the method improved.
- **Operations.** Cost per run is tracked against the ceiling, and a run that would exceed it stops rather than completes.

**A change to a prompt, a model, a retrieval index, a data pipeline or an agent's tool permissions is treated as a production change,** with its own version and manifest entry, exactly as a code change is.

## Consequences

**The matrix has to exist in code, not only in prose.** Each forbidden action needs a corresponding deny in AgentCore Policy, and each denial needs a test that proves it holds, which adds work to module 9 where the payment paths are built.

**Module 12 gains a lesson.** Authorizing an agent by action class is exactly what a reader building their own paying agent needs, and MREP can teach it from its own policy file rather than in the abstract.

**Review time is now a named cost.** Treating human review as the throttle means the per-run budget covers generation while the founder's hours cover acceptance, and the roadmap's rung gates should say how many hours a rung is expected to take.

## Alternatives considered

| Option | Why not |
| --- | --- |
| Keep the six habits without a matrix | The habits stop known failures but do not say what an agent may do unsupervised, so each new tool reopens the question |
| Adopt the standard's framework and vocabulary wholesale | Its content is licensed and trademarked, it assumes platform and security teams MREP does not have, and MREP's neutrality is weakened by teaching one vendor's framework |
| Require human sign-off on every agent action | The desk would stop running; the point of the classes is to spend the founder's attention where consequences are irreversible |

## Revisit when

At each rung gate, and whenever an agent gains a tool that can spend money, write to a public place or touch a named party.

## Sources

- PeopleCert, *The DevOps Standard*, DEVOPS INSTITUTE official book, version 1.0 (October 2026), pp. 52–62 and 221–222, consulted for method and cited by page; no text or figures reproduced
- MREP decision records [P-22](../roadmap.md), [P-23](P-23-aws-platform.md) and [P-26](P-26-measure-agent-genuineness.md)
