# P-31: MREP's product is the reputation that gates agent credit

Nov 18, 2026 · @dinky

| Field | Value |
| --- | --- |
| Status | Accepted, November 18, 2026 |
| Amends | P-26 (rule R17, and who receives a verdict), P-28 (education as a line of the platform) and P-29 (the positioning statement's second sentence) |
| Related | [P-24](P-24-base-chain.md) (Base), [P-27](P-27-tempo-second-rail.md) (Tempo and MPP), [P-30](P-30-agent-authorization-and-validation.md) (action classes) |

## Summary

**MREP's product is a score that decides whether an AI agent can be trusted with money, and the measurement work becomes the input to that score rather than the thing sold.** The machinery does not change: the platform still instruments its own agents, still labels genuine payment behavior against scripted behavior, and still reads x402 on Base and MPP on Tempo. What changes is who the answer is for. A quarterly share of market volume is read by people with no budget for it, while a per-agent score is read at the moment someone has to decide whether to let an unfamiliar agent spend, and that person bears a loss if they decide wrong.

**Education stops being a line of the platform and becomes the channel.** P-28 described research and education as the two halves of the work. Teaching stays, because it is how the platform earns labeled data and first design partners, but it carries no revenue and no roadmap of its own.

**The public method stays published; the verdicts become private.** The platform's credibility rests on a method a buyer can rerun, so the method, the signals and the published series remain open. Individual verdicts go to the party bearing the loss under contract and are never published, which is a change to P-26's rules and is recorded below rather than left to inference.

## Context

**The research product had no buyer, and the reason was structural rather than a matter of packaging.** Builders can reverse-engineer what they want and will not pay to be taught what they can teach themselves, which is the founder's own conclusion from November 14. The paying question is not how large the agent economy is; it is whether this particular agent should be allowed to spend.

**The gap sits between what an agent claims and what an agent has done.** The funded wave of agent-identity companies attests identity and authority: Baselayer raised a $35M Series A in September 2026 serving over 2,300 financial institutions, Beltic emerged from stealth with $8.8M led by Norwest describing itself as building agent verification infrastructure, and Vouched raised a $17M Series A. Each answers who an agent is and who authorized it. None of them prices what the agent has actually done over time, which is the input a lender needs and the thing a public ledger can supply.

**The money is already pointed at this.** The Base Ecosystem Fund's July 2026 Request for Builders named tokenization, stablecoins, credit and agentic commerce as its focus, and the fund describes itself as backing pre-seed and seed teams building enduring onchain primitives and businesses that drive real economic activity across trading, payments and AI agents. A measurement desk whose headline is that most agent volume is not genuine subtracts from activity; an underwriting layer that lets an agent transact at size creates it. The second is fundable by that sentence and the first is not.

**Measured behavior explains why the opportunity exists.** Keyrock's analysis of agent settlement from May 2025 to April 2026 found about $70M across 176 million payments, an average near $0.31, with over 98% in USDC. Payments stay that small because no one will risk more on an actor they cannot assess, so the ceiling on agent commerce today is an underwriting problem wearing the costume of a technology problem.

## Decision

**The product is a score, delivered at decision time, with the evidence behind it.** One rail, one decision, one endpoint to begin: given an agent identifier, return a judgment of how its observed payment behavior compares with known genuine and known scripted behavior, the confidence in that judgment, and the signals that produced it. The caller decides what to do with it; MREP never extends credit, never holds funds and never issues the money it scores, which keeps the independence rule from P-26 intact.

**What the pivot changes, stated plainly.**

| | Before | After |
| --- | --- | --- |
| Customer | Anyone wanting the market's size | Whoever bears the loss when an agent spends: wallet providers, lenders, processors, issuers, identity vendors |
| Deliverable | A quarterly published estimate | A per-agent score returned on request, plus the published method |
| Unit | Aggregate volume on a rail | One agent identity |
| Revenue | Report subscriptions and cohorts | Per decision, which is what makes it infrastructure |
| Education | A half of the platform (P-28) | The channel that yields labeled data and design partners; no revenue |
| Capstone | Publish a market estimate | Build the scoring service and prove it on instrumented testnet traffic |

**R17 is rewritten, and this is the load-bearing change.** P-26 forbade any public verdict on a named address, agent or business, and a credit gate consists of nothing but verdicts on named parties. The rule now separates by audience rather than forbidding outright:

1. **Public outputs stay as they are.** Totals, shares and ranges only, with no named party, which is what P-26 established and what keeps the published series safe to read.
2. **Private verdicts are permitted under contract**, delivered only to a party with a decision to make about that agent, carrying the method version and the confidence, and never published, resold or used in a public brief.
3. **The method stays published whichever side it serves**, because a score a buyer cannot rerun is a heuristic, and the competitors whose heuristics are unpublished are the ones this platform is positioned against.
4. **No verdict is rendered on a party the desk has a stake in**, and the desk's own agents stay excluded as P-26 already requires.

**The first design decision is what the reputation attaches to, and it is not the wallet address.** An agent can mint a fresh address for nothing, so a score bound to an address is worthless exactly when it matters. The anchor has to persist and cost something to replace, which leaves four candidates to test in order: the delegating business or person, established through an identity vendor's attestation; the funding source behind the agent; a stake or bond the operator posts; and the signed mandate chain that agent wallets now emit linking a human's approval to the agent's execution and the settled payment. The choice is made before the first endpoint ships and is recorded as an amendment to this record, because everything downstream depends on it.

**The relationship with the identity vendors is complementary by design.** They attest what an agent is and who stands behind it; MREP prices what it has done. The platform therefore sells beside them and to them, and it does not build identity attestation, which would put it in the business it depends on.

## The ladder

**Read from the bottom. Each rung is what becomes possible once the rung below works.**

| | |
| --- | --- |
| **The world** | **Anyone can send software out to earn and spend on their behalf, and be trusted with it.** |
| Rung 4 | Agents transact at sizes that matter, because an underwritten actor can also be insured and held liable, and markets form around that |
| Rung 3 | The score becomes a primitive other contracts read, so limits are set programmatically instead of a person approving each move |
| Rung 2 | A score: a wallet or lender can decide about an agent it has never seen before |
| Year 1 | Labeled ground truth: telling a genuine agent from a script, on Base, with a published method |

**The reason this reaches a billion people is specific, and the dependency is named.** Credit today is granted against an inherited file: a bureau record, collateral, or a relationship someone's family already had. The people without a bank account, and the far larger group who have one but no credit file, are excluded by the absence of a record rather than by their conduct. A reputation assembled from observed behavior is a different basis, because a micro-business whose agent has paid for inventory reliably for eighteen months holds a record it generated itself. That is the mechanism. The dependency, which belongs in the pitch rather than hidden from it, is that it only reaches those people if the wallets and lenders serving them adopt the primitive, which is not MREP's to control.

**The counter-vision is the world if nobody builds it.** Either agent commerce stays stuck at sub-cent scripts, because no one will risk real money on an actor they cannot assess, or real money arrives first and the category's rules are written around whatever the first large agent fraud looks like.

## The two visions

**Three-year vision.** MREP scores agent payment behavior on Base and Tempo, a handful of wallet providers and lenders call it before they set an agent's spending limit, the method is published and has been rerun by someone outside the company, and the quarterly series on genuineness and denomination is cited by people arguing about the size of the agent economy.

**Ten-year vision.** Software agents hold working capital on their own records. A person or a small business can send an agent out to earn and spend, and the counterparties it meets can price its trustworthiness in milliseconds without knowing who its owner banks with. MREP is the record those counterparties read.

## What happens next, and the gate

**The interview question is a question, not a pitch.** Ask whoever owns spend limits at a wallet provider, a lender, a processor or an identity vendor: *today, when an agent you have never seen asks to spend five hundred dollars, what do you actually do?* If the answer is that they allow it and nothing happens, there is no budget yet, and that is the finding that would stop this. Learning it in two weeks is the point.

**The build is one endpoint, not a platform.** One rail, one decision, a score with its evidence, proven on the platform's own instrumented testnet traffic before any mainnet observation is scored for a customer.

**The funding gate has a date.** Base Batches 004 closed on September 9, 2026 with ten teams at $100,000 each, cohorts run twice a year, and the previous spring cohort ran from mid-February to early March, so the next window is expected to open in January 2027. Its stage bar asks for a team between founder-market fit and post-MVP, pre-seed with no completed seed round, with Base as the primary network. P-24 already satisfies the network condition; nothing yet satisfies the product condition, so the gate for an application is a shipped module rather than a better description of one. Batch 003 already included a collateral-free lending protocol and an agent payment infrastructure company, so the position to take with both is supplier rather than competitor.

## Consequences

**Documents change, and the public repository stops promising a market report.** The README's lead line, the build-in-public plan, the design-system cover and P-29's positioning statement all describe a research and education platform and are rewritten to describe the score. The research engine specifications keep the Sector Specialist and its estimate, now described as the input to the score rather than the output of the platform.

**The Genuineness Estimate survives with a different job.** It stays published, because it is the credibility asset and the capstone's public artifact, and because the denomination series added on November 17 is a tripwire worth keeping. It is no longer the product.

**Proprietary material stays out of the public repository from the start**, as P-29 phase 1 already requires, and the score's thresholds, the labeled example set and any customer verdict are proprietary by default.

**Nothing here authorizes an agent to act on its own.** The score is advisory output under P-30's classes, the caller makes the decision, and rendering a verdict on a named party stays in the forbidden class for public outputs.

## Alternatives considered

| Option | Why not |
| --- | --- |
| Keep selling the quarterly estimate as the product | Priced for readers without budgets, and it positions the platform against the ecosystem it needs to sell to |
| Build the lending itself, not just the score | It breaks the rule that the desk never builds what it assesses, and it would compete with the customers |
| Build identity attestation too | Funded and crowded, and it would put the platform in the business its own input depends on |
| Score wallet addresses | An agent mints a new address for nothing, so the score fails exactly when the stakes rise |
| Publish per-agent verdicts | Defamation and procurement risk with no upside, and the private verdict is the thing customers pay for |
| Wait for the market to prove itself first | The interview question answers this in two weeks at near-zero cost, and the funding window is in January |

## Revisit when

At the first interview round, if the answer to the spend-limit question is that nobody is yet deciding anything; when the anchor is chosen, which amends this record; at the Base application, whether or not it succeeds; and if an identity vendor ships observed-behavior scoring of its own, which would make this a feature rather than a company.

## Sources

- Base, [Base Ecosystem Fund](https://docs.base.org/get-started/base-ecosystem-fund) and [Get funded](https://docs.base.org/get-started/get-funded), for the fund's stated focus and what it offers
- Base, [Request for Builders](https://x.com/buildonbase) (July 16, 2026), for tokenization, stablecoins, credit and agentic commerce as the named focus areas
- Crypto Briefing, [Base opens applications for its fourth accelerator cohort](https://cryptobriefing.com/base-batches-004-investing-1m-startups/), and Base, [Base Batches](https://docs.base.org/get-started/base-batches), for the cohort size, the investment and the twice-yearly cadence
- Keyrock, *Who pays the agent*, as [reported by Bitcoin.com](https://news.bitcoin.com/keyrock-report-76-of-ai-agent-transactions-fall-below-visas-0-30-fee-floor/), for the size and denomination of measured agent settlement
- PR Newswire, [Beltic emerges from stealth](https://www.prnewswire.com/news-releases/beltic-emerges-from-stealth-to-secure-autonomous-agent-transactions-at-scale-302614000.html), for the agent-verification category and its funding
- Naveen Jain, as set out in *The Ten-Year Pitch Workbook* (Extraordinary Minds, November 2026), for the ladder, the counter-vision and the test that a message stands for something the buyer already wants
