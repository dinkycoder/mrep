# P-29: The platform is MREP, by Kirksey Research, built in public then taken private

Nov 14, 2026 · @dinky

| Field | Value |
| --- | --- |
| Status | Accepted, November 14, 2026 |
| Supersedes | P-25 (the platform's name is Agency Lab) |
| Amends | P-28 (MREP as a description rather than a name) and P-14 (repository addresses) |
| Related | [P-26](P-26-measure-agent-genuineness.md), [P-27](P-27-tempo-second-rail.md), [P-28](P-28-micro-research-and-education-platform.md) and [P-30](P-30-agent-authorization-and-validation.md) |

## Summary

**The platform's name is MREP, it is made by Kirksey Research, and it is built in public as the capstone and then taken private for the go-to-market version.** P-28 made "Micro Research and Education Platform" the description beneath the name Agency Lab, and the description has since proved to say more about the work than the name did, so the description becomes the name and Agency Lab retires. MREP is written out in full at first use in any document meant for readers outside the repository.

Kirksey Research is the agentic commerce intelligence company that makes MREP. The repositories were renamed on November 13, 2026, and the company's GitHub organization now exists.

## Context

**One product, one name.** Earlier work carried a public platform and a separate private product under two names, which split the build and the audience. There is now one product, so a second name would only divide attention.

**"Micro" names what the platform studies.** Visa's July 2026 report with Artemis splits agent payments into two categories: large purchases an agent makes on a person's behalf, which resemble ordinary online shopping, and high-frequency, low-value purchases the agent starts for itself, such as an API call, a data query, compute or a tool. It argues that the second category is where new payment architecture is most needed and where new protocols are appearing, which is x402 and MPP, and so where MREP works. Chainalysis measured that scale: more than 87% of the x402 payments it sampled on Base fell between $0.0001 and $0.10.

**The name has to survive a rename, so this is the last one.** Ambition became Agency Lab on November 8 and Agency Lab becomes MREP on November 14. Each rename costs a rewrite of every document and interrupts the public build, so P-29 is the final naming decision, and a later change would need an argument stronger than any made so far.

## Decision

**MREP is the product's name, and four things follow.**

| Item | Before | After |
| --- | --- | --- |
| Name | Agency Lab (P-25) | MREP, written out as the Micro Research and Education Platform at first use |
| Maker | Not recorded | Kirksey Research, an agentic commerce intelligence company |
| Repositories | `dinkycoder/ambition` on GitHub and GitLab | `dinkycoder/mrep` on both, renamed November 13, 2026, with the old addresses redirecting |
| Organization | None | `github.com/kirksey-research`, created November 13, 2026, on the free plan, owned by the founder's personal account and still empty |

**The positioning statement is this, and every public document leads with it or a shortened form of it.**

> **MREP: the independent check on whether AI agents are really spending money.**
>
> AI programs have begun buying data, computing power and tools on their own, a few cents at a time, and MREP is a research and education platform that measures those payments and teaches people to build them safely. It is needed because the published numbers cannot be trusted: nearly 200 million such payments have been recorded, yet one major study judged that under 8% of the spending it screened came from real AI agents, with the rest scripts, tests and inflated volume. Anyone who builds, funds, insures or regulates in this market is deciding on those numbers, and MREP gives them numbers they can check.

**The thesis MREP tests is stated as a claim, never asserted.** A widely argued view holds that agents will move commerce onto blockchains, because an agent can hold a key but cannot open a bank account, and because fees on the existing rails cannot fall to zero while an intermediary sits in the path. MREP measures whether that is happening: how much agent spending is genuine, on which rails, at what cost, and which intermediaries remain in the path. The desk neither endorses nor dismisses the claim, makes no price calls and recommends no asset, because a referee that cheers is not believed.

**The build runs public, then private, in four phases.**

| Phase | What happens | Gate to the next |
| --- | --- | --- |
| 0, now | Names, repositories and the organization are in place, and proprietary material is kept out of the public repository from the start | None |
| 1, through graduation | The twelve modules are built in public as the capstone, while the labelled examples, any client-only scoring and client deliverables live in a private repository | The capstone is graded and the submission is tagged `capstone-v1.0` |
| 2, after grading | MREP's full history moves to a private repository under the Kirksey Research organization, and the mirror is repointed at a private GitLab project that is checked to be private before anything is copied | The MVP gate in the business plan passes |
| 3, go to market | The measurement method stays published as a written specification even though the code is private, because a method buyers can rerun is the advantage over a competitor whose heuristics are unpublished | — |

**Two constraints bind phase 2.** Quantic requires the capstone's GitLab repository to be public, so the switch waits until grading is finished and until the school confirms how long it must stay public afterwards. And anything already published cannot be withdrawn, so material meant to stay proprietary never enters the public repository in phase 1 rather than being removed from it later.

## Open decisions this record does not make

**The public phase's license is unresolved, and the deadline is the first code module.** The repository is under the MIT License (P-14), which lets anyone copy and sell the work permanently, and that cannot be undone for anything already published. The repository holds only documents today, where the cost is small, so the choice can wait; once modules ship it cannot. A source-available license, which lets readers study the code but not compete with it, is the alternative to weigh with a lawyer. No change is made here, because the license on the founder's own work is his to choose.

**The bonded-claim mechanism is held for the private phase.** The earlier private product's mechanism, in which a seller locks a deposit behind a claim and a stranger can earn that deposit by proving the claim false, is neither built in public nor dropped; it waits for phase 2 or later. This records the default applied in the absence of a decision, and saying so reverses it.

## Consequences

**Every document is rewritten once more.** The README, the roadmap and register, the research engine specifications, the build-in-public plan, the design guidelines, the design system, the usability plan and the reading notes all take the new name, and the P-23 to P-28 records are updated so that a reader meets one name throughout. The archive keeps its old names, because an archived document is a dated record.

**The register's convention holds.** The book's platform stays the Macro Research and Education Platform, written in full, so that MREP always means this platform, which is what P-28 established and this record keeps.

## Alternatives considered

| Option | Why not |
| --- | --- |
| Keep Agency Lab, with MREP as its description | The description says what the platform does and the name did not, and carrying both divided the story |
| MMREP, adding Macro | It claims a category whose data is private and unmeasurable from public ledgers, and it undoes the distinction from the book's platform |
| Keep the capstone and the go-to-market product under separate names | There is one product now, so a second name would split the build and the audience |

## Revisit when

Never, for the name. For the path, at the capstone grading and again at the MVP gate.

## Sources

- Visa, [Agentic payments from the ground up](https://www.visa.com/en-us/thought-leadership/innovation/agentic-payments-from-the-ground-up) (July 2026), with Artemis, for the split between large agent purchases and machine-initiated micropayments
- Chainalysis, as reported by [Blockhead](https://www.blockhead.co/2026/10/15/ai-agents-have-made-138-million-payments-over-x402-most-of-them-under-10-cents/) (October 15, 2026), for payment sizes on Base
- TRM Labs, [Who's actually paying? Measuring AI agent payments on-chain](https://www.trmlabs.com/trm-tech-blog/whos-actually-paying-measuring-ai-agent-payments-onchain) (September 9, 2026), for the share judged genuinely agentic
