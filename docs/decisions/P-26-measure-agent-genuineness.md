# P-26: MREP measures which agent payments come from real agents

Nov 11, 2026 · @dinky

| Field | Value |
| --- | --- |
| Status | Accepted, November 11, 2026; amended November 17, 2026 to measure the settlement denomination alongside genuineness, and November 18, 2026 by P-31, which rewrites rule R17 by audience |
| Supersedes | P-13 (the charter excluded measuring fake or wash agent activity) |
| Related | [P-24](P-24-base-chain.md) (Base), [P-27](P-27-tempo-second-rail.md) (Tempo) and [P-28](P-28-micro-research-and-education-platform.md) (the platform's description) |

## Summary

**MREP now measures how much agent-payment traffic comes from genuine AI agents rather than scripts, tests or wash trading, because that measurement is the most valuable data in the field and no one publishes a method others can check.** Every headline figure for agent payments is inflated by traffic that only looks like agents paying, so a builder, a payment company or a regulator who reads raw counts reads mostly noise. The Sector Specialist publishes a Genuineness Estimate each quarter: the share of x402 and MPP payments that look genuine, as a range with a confidence band, under a versioned method published in full.

Two limits keep the work safe. The desk publishes only totals and shares, never a public verdict that a named address, agent or business is fake, and it reads public ledgers without ever sending a real-money transaction.

**The November 17, 2026 amendment adds one measured dimension and one named blind spot.** Every payment the desk already classifies also carries the asset that settled it, so the desk records that asset and publishes the denomination mix of genuine agent settlement beside the genuineness share. Lightning settles off-chain, so the share denominated in bitcoin cannot be read from public ledgers and is published as a floor rather than a measure, with the gap stated every time the series appears.

## Context

P-13, accepted on November 7, 2026, kept this work out for three reasons: it needed data access MREP wouldn't have, it needed legal review, and it would turn a teaching desk into a policing one. Each reason now has an answer.

**The data is public.** Every x402 payment on Base and every MPP charge on Tempo settles on a public ledger, so reading it costs nothing and needs no one's permission. Dune's curated agentic-payments dataset already covers x402 and MPP's on-chain Tempo payments in one table.

**Publishing totals avoids the legal risk.** Calling a named address or business fake invites claims of defamation and interference with its business, while a share computed over all traffic accuses no one. TRM Labs and Visa with Artemis publish exactly this kind of total. MREP follows that practice and adds what they leave out: a method anyone can rerun.

**A measurement is research, not policing.** The desk reports what share of traffic looks genuine and how sure it is, the same way an economist estimates unemployment without naming who is out of work.

**The gap is real.** TRM Labs judged only 0.6% to 7.5% of $25.62 million of screened x402 commerce to come from real agents (September 9, 2026), a range more than twelve times wide, and it notes that nothing in the protocol requires an agent, so a scheduled script and an agent can leave the same record. Visa and Artemis cut $135.7 million of raw x402 volume to $15.0 million (July 2026) with heuristics they have not published. Three reputable studies count the same protocol differently, and none can be rerun by an outsider.

**The founder's background fits the problem.** Telling genuine agents from scripts is a judgment made from behavioral signatures under uncertainty, which is the daily work of intelligence analysis and sanctions screening. That work brings habits the current studies lack: graded sources, stated confidence and a written method that a second analyst can check.

### Why the amendment adds denomination (November 17, 2026)

**A widely argued claim about agent money is falsifiable, and no one publishes the series that would test it.** Bitcoin-first analysts argue that because AI can make more of almost everything except bitcoin, whose supply is capped at 21 million, agents comparing assets on yield, risk and purchasing power will converge on money that cannot be diluted, and that agentic commerce therefore pulls bitcoin adoption forward. The claim is about a ratio moving over time: the share of agent-initiated settlement denominated in money whose supply is fixed. Today that share is close to nothing, because Keyrock's analysis of agent settlement from May 2025 to April 2026 found more than 98% of it in USDC across 176 million payments averaging about $0.31. Whether it stays there is an open question with two audiences who disagree, which is the position a referee wants to occupy.

**The desk can add the measure almost for free, because the expensive half is already built.** Reading which asset settled a transfer is trivial; knowing the transfer came from a genuine agent rather than a script is the hard part, and that is the classifier this record already establishes. Denomination is therefore a second column on an existing table rather than a second pipeline, which is the only reason it enters the charter before a module ships.

**The claim cannot be settled on behavior alone, so the desk does not try.** A denomination series says what agents paid with; it does not say whether they chose the unit for its scarcity, its stability or because their seller invoiced in it. The desk reports the mix and leaves the reason to the reader, and it makes no price call on any asset, which P-04 already forbids.

## Decision

**The Sector Specialist owns the Genuineness Estimate, and it follows seven rules.**

1. **Totals only in public.** Briefs report shares and counts over all traffic or over named segments, such as a facilitator or a price band, never a verdict on an identifiable address, agent or business. The Compliance Agent fails any brief that does (rule R17). [P-31](P-31-agent-reputation-credit-gate.md) rewrites this rule by audience: public outputs stay as described here, while a private verdict on a named agent may go, under contract, to a party with a decision to make about it, never published or resold.
2. **A range, not a point.** Each estimate gives a permissive and a strict share, in the style of TRM's two tests, with a confidence band and estimative words ("likely", "almost certainly") defined in the glossary.
3. **A published, versioned method.** The signals, thresholds and code version that produced an estimate are published with it, and a method change takes a new version number and a rerun of the previous quarter, so a change in the estimate can be told apart from a change in the method.
4. **Labeled examples from known sources.** The desk's own instrumented agents produce payments known to be genuine, and a deliberately simple scripted bot produces payments known to be scripted, both on test networks. These labels calibrate the method; because testnet behavior only approximates mainnet, the published shares come from mainnet signals, and the labels never stand in for them.
5. **Read, never send.** The desk reads Base and Tempo mainnet ledgers through public endpoints and data warehouses, and it never sends a mainnet transaction. P-03's test-money rule is unchanged, because reading moves no money.
6. **The desk's own traffic stays out of the market figures.** Its addresses are listed and excluded from every mainnet estimate, and its testnet payments appear only as labeled examples.
7. **Denomination is recorded and published beside the share (added November 17, 2026).** Every payment the method classifies also records the asset that settled it, and each quarterly estimate carries the denomination mix of the traffic judged genuine, under the same version number and the same confidence language as the share itself. The mix is reported for what agents settled in, never as a view on any asset's value.

The signals start from what the published studies use, such as how long an address stays active, how many separate sellers it pays, whether it is registered under ERC-8004, how regular its timing is and whether its funds go round in a loop, and the method records which ones each version uses.

### Named unobservables

**The desk publishes what it cannot see, in the same brief as what it can.** Two kinds of agent payment leave no public record of their individual transfers, so every figure that could be affected carries the gap next to it.

| Unobservable | Why it cannot be read | Effect on the published figure |
| --- | --- | --- |
| Lightning settlement, including L402, the HTTP 402 standard Lightning Labs published in 2020 and extended with agent tooling in February 2026 | Lightning payments settle off-chain between channel partners, so only channel opens and closes reach the Bitcoin ledger, and the individual payments never do | The bitcoin-denominated share of agent settlement is a floor, not a measure. The bias runs one way: the true share can only be equal to or higher than the published one, and the series says so each time |
| MPP sessions (P-27) | An agent deposits, signs off-chain vouchers per request and settles at the end, so only the start and finish reach the chain | Counts of MPP payments understate request volume, and the per-payment average overstates it, which P-27 already records |

**Closing the Lightning gap would take cooperation, not better analysis**, because the data sits with node operators and routing services rather than on a ledger, so it enters the method only if a counterparty publishes it or shares it under terms the desk can disclose. Until then the desk states the floor and the reason, and does not infer the missing volume.

**One development would make this gap matter more than the measure.** If dollar-denominated assets issued on Bitcoin's own rails, such as Taproot Assets, carry agent payments at scale, then the rail and the unit come apart: settlement would move to bitcoin infrastructure while the unit of account stayed the dollar, and a denomination series alone would report that as no change at all. The method therefore records the rail and the unit as separate fields from the start, so that the two can be read apart when it happens.

## Consequences

**The register gains its most valuable output and its most sensitive one.** The estimate gives readers and paying agents a number they cannot get elsewhere, and it gives the education track a lesson in reading evidence that is mostly noise. It also creates the one output that could hurt a named party if it leaked into a brief, so the public-totals rule is enforced in code and by the Compliance judge, not left to the writer.

**The Director's scope changes.** "What share of x402 payments come from genuine agents?" is now in scope, while "Is this address a wash trader?" still ends before any money is spent.

**Earlier text changes.** The Sector Specialist's rule "a disclosure, never a score" becomes the seven rules above. The Micro Economist no longer declines an unfiltered agent transaction count; it reports one only beside the genuineness-adjusted estimate and its method.

**The denomination mix is a tripwire, not a headline, and it earns no revenue.** With the measured share of agent settlement overwhelmingly in one dollar stablecoin, the series will read much the same for several quarters, and a figure that does not move is not a finding. Its value is concentrated in the quarter it starts moving, which is what a tripwire is for and why it is worth keeping at almost no cost. It belongs to the published method, the public series and the capstone; it is not a product line, and no part of the revenue plan rests on it.

## Alternatives considered

| Option | Why not |
| --- | --- |
| Keep P-13 | The field's headline numbers would stay unchecked, and the desk would give up the data that makes its research worth paying for |
| Publish address-level scores | A public verdict on a named party carries legal risk and could harm an honest builder wrongly flagged |
| Rely on TRM's or Artemis's figures | Their ranges are wide or their methods unpublished, so the desk could not explain a change in its own briefs |
| Give denomination its own decision record | It extends what an existing measure records rather than changing what the desk does, so it belongs in this record's rules and blind spots |
| Publish a bitcoin share without the Lightning caveat | The unreadable volume sits exactly where the claim being tested would first appear, so an uncaveated zero would be an artifact of the method presented as a finding |
| Estimate the missing Lightning volume | The data sits with node operators rather than on a ledger, so any figure would be a guess dressed as a measurement |

## Revisit when

At the rung-5 gate, or before any output names an address, agent or business, which needs a written legal review first. For the denomination rule, when the non-dollar share of genuine agent settlement holds above a tenth for a full quarter, or when dollar-denominated assets on Bitcoin's own rails carry agent payments at scale, since either would turn the tripwire into a subject of its own.

## Sources

- TRM Labs, [Who's actually paying? Measuring AI agent payments on-chain](https://www.trmlabs.com/trm-tech-blog/whos-actually-paying-measuring-ai-agent-payments-onchain) (September 9, 2026)
- Visa, [Agentic payments report](https://www.visa.com/api/image-proxy?path=%2Fcontent%2Fdam%2Fvisa%2Freimagine-visa%2Fthought-leadership%2Fdocuments%2Fagentic-payments-report.pdf) (July 2026), with Artemis data to April 21, 2026
- Four Pillars, [x402 on Polygon: real or gamed?](https://research.4pillars.io/en/research/x402-on-polygon-real-or-gamed)
- Allium, [Visa x Allium: making sense of stablecoins](https://allium.so/blog/visa-x-allium-making-sense-of-stablecoins/)
- Dune, [Agentic payments curated dataset](https://docs.dune.com/data-catalog/curated/payments/agentic-payments.md), covering x402 and MPP's on-chain Tempo payments
- Token Terminal, [Agentic payments explorer](https://tokenterminal.com/explorer/agentic-payments)
- Notabene, [Know your agent: KYA in agentic payments](https://notabene.id/post/know-your-agent-kya-agentic-payments), on why an agent choosing the payee doesn't remove sanctions liability

Added by the November 17, 2026 amendment:

- Keyrock, *Who pays the agent*, as [reported by Bitcoin.com](https://news.bitcoin.com/keyrock-report-76-of-ai-agent-transactions-fall-below-visas-0-30-fee-floor/), for the share of agent settlement in USDC and the count and average size of agent payments
- Lightning Labs' L402, as [reported by Crypto Briefing](https://cryptobriefing.com/lightning-labs-l402-bitcoin-payments-ai/), for the Bitcoin-native HTTP 402 standard aimed at agents
- Alby, [Agentic commerce: a guide to L402, x402 and MPP](https://getalby.com/blog/agentic-commerce-a-guide-to-l402-x402-and-mpp), for how the three protocols differ on settlement rail and asset
