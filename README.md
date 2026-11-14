# MREP

**The independent check on whether AI agents are really spending money.**

MREP, the Micro Research and Education Platform, is an open-source research and education platform for agentic commerce, made by Kirksey Research and built on AWS and Base: a toolkit that lets AI agents hold and spend stablecoins safely, a research desk that scores payment rails and stablecoins on one neutral scorecard and estimates how much agent-payment traffic comes from genuine agents, and lessons that teach both. "Micro" names its subject: agents paying other agents a few cents at a time over x402 and Tempo's Machine Payments Protocol, the payments an agent starts for itself rather than the larger ones it makes on a person's behalf. Its mission is to help AI builders give their agents money safely, one small win at a time. It is built in public one module at a time, with contracts in Solidity and everything else in Python, and each module ends with a reader challenge anyone can prove they did. It climbs a ladder whose rungs end at gates rather than dates. It is also an MSAIE capstone project, and its dates return when the capstone course begins.

It grows in modules: agent wallets whose keys never leave AWS KMS, allowances a smart wallet enforces, x402 payments bound to their receipts, gasless stablecoin payments, money-back escrow, statements and spending alerts. Its design system adds the money components that agent-payments apps need, on top of IBM's open-source Carbon.

The published figures for this market cannot be trusted. Nearly 200 million agent payments have been recorded, yet one major study judged that under 8% of the spending it screened came from real AI agents, with the rest scripts, tests and inflated volume. MREP publishes a quarterly estimate of the genuine share with a method anyone can rerun ([P-26](docs/decisions/P-26-measure-agent-genuineness.md)). The platform was called Ambition until November 8, 2026 and Agency Lab until November 14, 2026, and MREP is a working name while the final one is chosen ([P-29](docs/decisions/P-29-mrep-name-and-path.md)).

## What's here

| Path | What it is |
| --- | --- |
| [docs/build-in-public-plan.md](docs/build-in-public-plan.md) | The mission, the least-to-most ladder, the twelve modules, what we measure, the UX agent and the ground rules |
| [docs/roadmap.md](docs/roadmap.md) | The roadmap on AWS and Base: why this platform, the case study, the ladder, the twelve modules, the rail-neutral scorecard, six safety habits, the architecture and the Decision Register |
| [docs/decisions/](docs/decisions/) | Decision records. November 8, 2026: [P-23](docs/decisions/P-23-aws-platform.md) (AWS replaces Google Cloud), [P-24](docs/decisions/P-24-base-chain.md) (Base replaces Sui) and [P-25](docs/decisions/P-25-agency-lab-name.md) (the Agency Lab name, since superseded). November 11: [P-26](docs/decisions/P-26-measure-agent-genuineness.md) (measuring genuine agent activity), [P-27](docs/decisions/P-27-tempo-second-rail.md) (Tempo as a second measured rail) and [P-28](docs/decisions/P-28-micro-research-and-education-platform.md) (the Micro Research and Education Platform description). November 14: [P-29](docs/decisions/P-29-mrep-name-and-path.md) (MREP as the working name, Kirksey Research and the public-then-private path) and [P-30](docs/decisions/P-30-agent-authorization-and-validation.md) (agent authorization and validation) |
| [docs/archive/](docs/archive/) | Earlier roadmaps and specifications kept unchanged as dated records: the Base and Solidity roadmap of November 4 (D-01 to D-26), and the Sui and Google Cloud roadmap and agent specifications of November 7 |
| [docs/design-guidelines.md](docs/design-guidelines.md) | Principles and persuasion policy, foundations, brand assets, components, screen patterns, the reader journey, glossary and maintenance |
| [design-system/](design-system/) | The style guide, design tokens (`tokens.json`, `tokens.css`) and previews of the ten money components |
| [docs/research/usability-testing-plan.md](docs/research/usability-testing-plan.md) | Research on free and low-cost usability testing (UXtweak, Figma Make and alternatives) and the testing plan by module |
| [docs/research/participant-consent-form.md](docs/research/participant-consent-form.md) | The consent form every usability-study participant reads and signs, covering recordings, data protection and their rights |
| [docs/research/building-ai-agents-for-finance-notes.md](docs/research/building-ai-agents-for-finance-notes.md) | Reading notes on *Building AI Agents for Finance* (Packt, 2026): the rules from the book that MREP adopts, with page numbers |
| [docs/research/research-engine-agent-specs.md](docs/research/research-engine-agent-specs.md) | Specifications for the research desk's seven units on AWS: the order they join the ladder, their sources, tools, gate tests, failure modes and how the per-run ceiling is measured |
| [docs/research/research-engine-research-report.md](docs/research/research-engine-research-report.md) | The November 6 research behind those specifications, with every source and every page that could not be opened |
| [docs/pdf/](docs/pdf/) | PDF versions of the plan, the roadmap and Decision Register, the decision records, the guidelines, the design system, the testing plan, the consent form, the reading notes and the research engine specifications |

Code arrives module by module, starting with the agent wallet in module 1.

## Safety

Everything runs on Base Sepolia, Base's free test network, with test money only. No wallet key, seed phrase or API key ever goes into this repository or a post: the agent's key is created inside AWS KMS and signs there. MREP issues no token and no stablecoin. Never share a seed phrase with anyone.

## Contributing

The main copy of MREP lives on GitHub. [gitlab.com/dinkycoder/mrep](https://gitlab.com/dinkycoder/mrep) is an automatic mirror that GitHub overwrites on every change, so please open issues and pull requests on [GitHub](https://github.com/dinkycoder/mrep). Both repositories were renamed from `ambition` to `mrep` on November 13, 2026, and the old addresses redirect. [CONTRIBUTING.md](CONTRIBUTING.md) covers the safety rules, how to propose a change and the design rules.

## License

MREP is released under the [MIT License](LICENSE), which covers the code, docs and design system in this repository. The license doesn't cover the MREP name or any future logo.
