---
title: "Incentives in AI Safety"
subtitle: "Where should I spend limited resources?"
categories:
  - Artificial Intelligence
tags:
  - Safety
  - Proposal
toc: true
toc_sticky: true
---


## Incentives in AI Safety

This document introduces the Incentives Matrix, a framework for discussing incentive structures in AI Safety and is meant to help identify who may be most likely to address key challenges in the space. 

Consider harms resulting from deployment of advanced AI systems across two axes, from the perspective of the entity serving the model. First, we ask **How aware is the model server of the specific harm?** The model server is typically a private sector actor but may also be a government entity, and we take an expansive view. The major players in AI today have been largely collaborative in identifying and addressing many important harms, but it seems inadvisable to assume that entities hosting models *cannot* intend harm.  Server awareness of harms ranges from unaware to deliberate.

**Awareness** means that at the time the model is served or deployed, the server either knew about this specific harm, or would reasonably be expected to have known given available evidence and prior incidents. This is anchored to the moment of deployment rather than an ongoing judgment, and it evolves. Once a specific harm is publicly documented, reasonable expectation applies to future deployments by any actor. Independent research and documentation are the mechanism by which unawareness becomes indefensible.

Next, we ask **Does the model server benefit from the harm?**, where benefits may be in the form of profit, political power, or control of information. This scale ranges from no benefit (inclusive of negative benefit) to beneficial by design. Benefit from the harm means that the specific harm drives revenue, engagement, or return usage. 

This framing highlights where private organizations are incentivized to produce solutions by market forces, and where they are not.

---

### Incentives Matrix: A Model-Serving Company's Perspective

```
                              MODEL SERVER BENEFIT
                     BENEFIT: NONE      BENEFIT: INCIDENTAL  BENEFIT: BY DESIGN
                  ┌─────────────────┬──────────────────┬───────────────────────┐
  SERVER          │  1. No Benefit, │  2. Incidental   │  3. Intended Benefit, │
  UNAWARE         │     Residual    │     Benefit,     │     Residual Harm     │
  OF HARM         │     Harm        │     Residual Harm|                       │
                  ├─────────────────┼──────────────────┼───────────────────────┤
SERVER            │  4. No Benefit, │  5. Incidental   │  6. Intended Benefit, │
AWARE OF HARM     │     Known Harm  │     Benefit,     │     Known Harm        │
                  │                 │     Known Harm   │                       │
                  ├─────────────────┼──────────────────┼───────────────────────┤
  SERVER          │  7. No Benefit, │  8. Incidental   │  9. Intended Benefit, │
  INTENDED        │     Known Harm  │     Benefit,     │     Harm              │
  HARM            │       [EMPTY]   │     Intended Harm│     Intended          │
                  └─────────────────┴──────────────────┴───────────────────────┘
```


Items in the first column broadly describe a poor product, and should be improved by the company building and serving the model. An example of such a harm is a smartphone randomly sets itself on fire. We do regulate this sort of thing, but it is also just not great business. Note that Cell 7 is hard to fathom, but not impossible, so it remains.

Moving to the right, the incentive conversation gets more interesting. When the server benefits, either incidentally or by-design, market self-correction becomes unreliable. This is where the question of who should act, and with what resources, becomes central.

The rows describe the awareness of the entity hosting and serving the model of the particular harm underway. The top row is inherently transient. A server can only remain unaware of a specific harm for as long as that harm goes undocumented. Once a harm is publicly established, reasonable expectation applies to any server deploying thereafter, and the harm migrates up the awareness axis. 

This framing assumes that there is an entity serving a model with a motivation (typically profit or power). A case has been made that open source models are inherently dangerous because anyone could remove safety guardrails and use it for nefarious activity. If someone deploys a modified open source model publicly, they are a model server, this matrix applies and governance response likely resembles how we address harmful content distribution on the dark web. Alternatively, if the model is self-hosted and never exposed publicly, the threat surface narrows considerably. An actor capable of doing this meaningfully is likely capable of training from scratch.


---

### Who Is Best Positioned to Act

The matrix tells a clear story about motivation and positioning for risk mitigation.
Each cell contains real harms that need to be addressed, and it's important to be realistic about who is most likely to address them. **If the conversation around AI safety is driven primarily by one type of institution, particularly one focused on product quality and profitability, large swaths of vital work may be neglected.**

Each institution has limited resources, and focusing those resources where they are least duplicated may be more effective than spreading them across the full grid.  
A regulator adding capacity in cell 1 is largely reinforcing what the market handles. That same capacity directed at cells 5 through 9 addresses work that might otherwise not get done.


```
                              MODEL SERVER BENEFIT
                  BENEFIT: NONE      BENEFIT: INCIDENTAL    BENEFIT: BY DESIGN
                ┌──────────────────┬────────────────────┬─────────────────────┐
  SERVER        │        1         │         2          │          3          │
  UNAWARE       │  ████████████▓   │  ████░░░░▓▓▓▓▓▓    │  ░░░░░░▓▓▓▓▓▓▓▓▓  │
                ├──────────────────┼────────────────────┼─────────────────────┤
  SERVER        │        4         │         5          │          6          │
  AWARE         │  ██████░░░░▓▓▓▓  │  ░░░░░░▓▓▓▓▓▓▓▓    │  ░░░░▓▓▓▓▓▒▒▒▒▒▒  │
                ├──────────────────┼────────────────────┼─────────────────────┤
  SERVER        │        7         │         8          │          9          │
  DELIBERATE    │    [EMPTY]       │  ░░░░▓▓▓▒▒▒▒▒▒▒    │  ░░░▓▓▓▒▒▒▒▒▒▒▒▒  │
                └──────────────────┴────────────────────┴─────────────────────┘

████  Model server, trainer, internal safety teams, standards bodies
▓▓▓▓  Academic institutions, benchmark setters, investigative journalists,
      civil society, NGOs, independent researchers
░░░░  Regulators, policy bodies, government (liability and criminal law)
▒▒▒▒  International bodies, competing governments, open source communities,
      whistleblowers
```


Academic institutions and benchmark setters have a particularly important role across the grid. In the top row, they define what reasonable expectation means. In cells 5 and 6, they provide the independent research and auditing capacity that internal teams cannot credibly supply. In cells 8 and 9, they contribute policy research and international standards development from outside the server's jurisdiction, where their independence is structurally valuable.


### Example Harms 

To make this a bit more concrete, a few specific harms and where they fall:

- **Cell 1:** A model recommending glue on pizza caused reputational damage with no benefit from the harm. Early autonomous agent deployments attempting to hack external systems may also belong here, migrating to cell 3 as awareness accumulates.
- **Cell 2:** User-intended harms belong here, as the server benefits incidentally even if it is unaware of the particular harm. User-intended agentic hacks or harmful information disclosure may belong here (Censorship risks appear in cell 9.)
- **Cell 3:** Engagement mechanics designed to increase usage causing unexpected harm belong here. 
- **Cell 4:** Environmental damage, economic collapse, and biased automated decisions in criminal justice and hiring.
- **Cell 5:** Degradation of democracy, systemic monoculture, education harms and erosion of privacy norms.
- **Cell 6:** AI-driven psychological dependency and relationships belong here, where the harm drives return visits by design and awareness is established.
- **Cell 7:** Unfathomable, but not impossible, this is the situation where a server intends harm but does not benefit from the harms caused. 
- **Cell 8:** Deliberate output adjustment to comply with government censorship in exchange for market access. The harm to users is deliberate, but not the goal in and of itself. 
- **Cell 9:** Control of information flow, propaganda and election interference at scale, anti-competitive product recommendations. Here the harm is the goal.

The following sections go into more detail for each cell, with example harms and common countermeasures. There is no evaluation of countermeasures here, but it is important to note that some countermeasures may reduce one risk while increasing another. A more detailed discussion can be found in the Risk Interactions section.

---

#### 1. No Benefit, Residual Harm
*Add glue to your pizza.* | *I made you this pizza. Don't worry about the cheese falling off*

This category includes scenarios where a model server does not benefit, and is not aware of the harm for the users. Examples include incorrect advice or unintended autonomous actions that cause financial damage. Users will not return to this product. 

- **Actor:** None
- **Beneficiary:** None
- **Harm falls on:** Users, third parties, infrastructure
- **Who can act and why:** Model server and trainer are strongly motivated; government can reinforce via liability standards
- **Example Harms:** Incorrect advice causing real-world harm, unintended autonomous actions causing physical or financial damage, bias from training data artifacts, misspecified agent behavior
- **Common Countermeasures:** * Red-teaming, testing, output filtering, human-in-the-loop review, liability frameworks, incident disclosure, training the model to say "I don't know"[^1]

[^1]Countermeasures are listed throughout this document as reference points, not recommendations. Their effectiveness varies significantly by context, and some may reduce one risk while increasing the likelihood or severity of another. The final section of the Risk Matrix discussion addresses this directly.

---

####2. Incidental Benefit, Residual Harm

*How do I make [something dangerous]* | *I made something dangerous.*

When an adversary user uses a model to intentionally cause harm, the model server earns revenue from usage and indicentally benefits. The user will return to this product, which is helping them achieve their goal.

- **Actor and beneficiary:** User and model server through usage
- **Harm falls on:** Third parties determined by the user -- individuals, populations, infrastructure
- **Who can act and why:** Model server motivated where liability is direct and visible; government via criminal and liability law
- **Example Harms:** Weapon and drug synthesis instructions, content sexualizing minors, targeted harassment and stalking, identity fraud via synthetic voice or imagery, malware and cyberweapon generation, infrastructure attacks, non-consensual synthetic imagery, radicalization content
- **Common Countermeasures:** Red-teaming, guardrails and refusal training, access controls and rate limiting, post-deployment monitoring, criminal liability for users, structural liability for enablers

---

####3. Intended Benefit, Residual Harm

*Don't end this conversation, it will make me sad.* | **

The system was designed to generate a specific benefit, but the design causes unexpected harm to users or society about which the server may not initially be aware. Examples include addictiveness or bias and discrimination. Note that as harms become documented, items in this cell move into cell 6.  

- **Actor:** Model server, model trainer, data preparer
- **Benefit:** Model server
- **Harm falls on:** Users, communities, democratic systems
- **Who can act and why:** Model server has no incentive to address undocumented harms; independent researchers and civil society must surface and document harms, and there must be a legal framework in place to enforce any protections.
- **Example Harms:** Engagement-driven radicalization, emotional dependency from retention-optimized design, bias and discrimination from unexamined training data, erosion of professional expertise pipelines
- **Common Countermeasures:** Independent harm audits, bias testing and fairness benchmarks, third-party dataset audits, training data provenance disclosure

---

####4. No Benefit, Known Harm

*Economic instability and environmental impacts*

This category covers scenarios where the model server is aware of harms to workers, communities, or the environment but does not benefit from those specific harms -- and may in fact be negatively affected by them.

- **Actor:** Model server
- **Benefit:** None
- **Harm falls on:** Workers, local communities, future generations, environment
- **Who can act and why:** Model server has mixed motivation; policy bodies can establish standards and penalties
- **Example Harms:** Energy and water consumption from AI infrastructure at scale, local environmental harms near data centers (water stress, land use, carbon emissions), mass labor displacement at societal scale, systemic economic instability as a downstream consequence of displacement and infrastructure dependency, biased automated decisions in criminal justice and hiring
- **Common Countermeasures:** Environmental impact assessments (regulators), energy and water use standards (regulators), workforce impact disclosure (regulators), labor transition frameworks (governments), systemic risk monitoring frameworks for AI infrastructure dependency (regulators, central banks), concentration limits on critical AI infrastructure (regulators), bias testing and fairness requirements for automated decision systems (regulators), mandatory human review for high-stakes automated decisions in criminal justice and hiring (regulators)

---

####5. Incidental Benefit, Known Harm
*Democratic degredation and a systemic monoculture*

The model server is aware harm is occurring and incidentally benefits from the same system that produces it. Harm is borne by users, workers, or society while the benefit is retained by the model server.

- **Actor:** Model server, model trainer, data preparer
- **Benefit:** Model server, incidentally through increased usage and dependency
- **Harm falls on:** Users, communities, markets, minority groups, workers, democratic institutions, future generations
- **Who can act and why:** Model server has no incentive without external pressure; independent researchers, regulators, and NGOs have the most leverage
**Example Harms:** Workforce deskilling and increased dependency on AI, erosion of critical thinking, algorithmic radicalization, collapse of professional apprenticeship models, democratic degradation through concentration of information infrastructure, systemic monoculture risk, erosion of privacy norms through normalization of data collection, wealth inequality driven by automation and value concentration
**Common Countermeasures:** Sovereign and open model infrastructure approaches to reduce monoculture risk (companies, governments), externality disclosure (regulators), independent algorithmic audits (regulators, NGOs), data protection and consent frameworks (regulators), antitrust scrutiny of information consolidation (regulators, governments), interoperability mandates (regulators), wealth redistribution and automation taxation frameworks (governments), whistleblower protections (governments)

---

####6. Intended Benefit, Known Harm
*Emotional dependency*

The model server is aware harm is occurring and the benefit structure was deliberately designed to produce it. The risk-producing mechanism and the benefit-producing mechanism are the same thing.

- **Actor and beneficiary:** Model server
- **Harm falls on:** Users who cannot identify or opt out of the architecture, communities, democratic systems, public investors
- **Who can act and why:** Model server has no incentive; independent auditors, civil society, and whistleblowers are the primary path
- **Example Harms:** Engagement farming, deliberately engineered compulsive use with suppressed internal evidence, notification and interaction systems designed to override user attempts to disengage, recommendation systems maximizing time on platform with known wellbeing costs, companion systems designed to produce emotional dependency, systems designed to exploit documented behavioral vulnerabilities, deliberately opaque personalization, suppression of internal safety findings for commercial reasons, circular investment structures where capital flows between AI companies and infrastructure providers inflate valuations on both sides with awareness that the underlying economics are unsustainable
- **Common Countermeasures:** Independent technical audits with platform data access (regulators, NGOs), mandatory disclosure of internal safety research (regulators), whistleblower protections (governments), financial disclosure requirements for circular investment structures (regulators), sovereign and open model infrastructure approaches (companies, governments)

---

####8. Incidental Benefit, Intended Harm
*Population-level surveillance*

The model server deliberately causes or enables harm. The benefit accrues as a side effect of that decision rather than a designed outcome.

- **Actor and beneficiary:** Model server -- market access, competitive positioning, or regulatory favor as a side effect
- **Harm falls on:** Users, competitors, democratic institutions
- **Who can act and why:** Model server has no incentive; civil society, government, and international bodies
- **Example Harms:** Deliberate output adjustment to comply with government censorship in exchange for market access, deliberate compliance with surveillance requirements that compromise user privacy, deliberate downgrading of safety features for competitive reasons, politically selective content filtering in specific markets
- **Common Countermeasures:** Output auditing (civil society, regulators), extraterritorial regulatory frameworks (governments), minimum content standards (international bodies), competitive market oversight (regulators), sovereign and open model infrastructure approaches (companies, governments)

---

####9. Designed Benefit, Risk or Harm Intended
*Population-level control*

The model server designed the system to produce harm because the harm is beneficial to them. This applies equally to private companies and governments acting as model servers.

- **Actor and beneficiary:** Model server
- **Harm falls on:** Users with no ability to opt out, those subject to surveillance or targeting, democratic institutions, free information markets
- **Who can act and why:** Model server has no incentive; for private actors, domestic regulation and civil society; for state actors, international bodies, civil society, and competing governments
- **Example Harms:** Ideology or worldview enforcement through controlled model outputs, propaganda and coordinated information manipulation at scale, surveillance infrastructure deployed against users or dissidents, behavioral data extraction for intelligence or control purposes, models redirecting users to server's own products or interests while presenting as neutral, designed dependency on a single information source
- **Common Countermeasures:** International treaty frameworks (governments, international bodies), cross-border technical auditing (international bodies, civil society), transparency and whistleblower protections (governments), competing sovereign and open model infrastructure as a structural alternative to state or monopoly control (governments, international bodies)

---


## Prioritizing Risks 

The harms in the Incentives Matrix are neither evenly distributed, nor equally urgent. Some of them impact individuals, and others an entire population.  
A traditional risk matrix plots risks on two axes -- **likelihood** (how likely is this harm to occur) and **severity** (how bad it is when it does). It is a practical tool for prioritizing risks and identifying who can address them.

This tool highlights that some risks may feel lower likelihood than they are because we implicitly trust the model server to prevent them. Making that assumption explicit raises questions of standards, protections, or assurances that could be put in place today. 

**Severity definitions in this document**

- **Catastrophic:** Irreversible harm at civilizational scale. Society cannot recover to a prior state. Examples: human extinction or near-extinction, permanent global authoritarian control with no path to reversal, permanent loss of human agency over AI systems.
- **Major:** Severe harm to large populations, institutions, or democratic systems. Recoverable in principle but with significant long-term consequences. Examples: large-scale election interference, mass casualties from a targeted attack, collapse of a national financial system.
- **Moderate:** Meaningful harm to specific communities, groups, or sectors. Addressable with targeted policy or technical intervention. Examples: biased hiring systems affecting a demographic group, a significant data breach, targeted harassment campaigns.
- **Minor:** Limited harm to individuals or small groups. Recoverable without systemic intervention. Examples: incorrect advice causing a localized bad outcome, academic fraud by an individual user.
- **Negligible:** Harm is real but inconsequential at any meaningful scale. Included for completeness but not a prioritization concern.




---
### Examples

Risk matrices are never static, but this is particularly true here. As AI capabilities grow, risks move along both axes. A risk that feels manageable today may look very different with near-term capability advances. 
We show the risk matrix for two cells before and after introducing recent capabilities including agentic action, multi-agent collaboration, audio and video modalities, real-world tool access, and API availability.

*Notation: (A) marks a risk's original position, A' marks its position after capability advances, and A alone means it did not move.*

#### Risks in Cell 2: Incidental Benefit, Residual Harm

```
                  UNLIKELY     POSSIBLE        LIKELY       ALMOST CERTAIN
               ┌────────────┬─────────────┬─────────────┬────────────────┐
CATASTROPHIC   │  (A)       │  A'         │             │                │
               ├────────────┼─────────────┼─────────────┼────────────────┤
MAJOR          │            │  (B)(D)(F)  │  B' D' I'   │  F'  K'  L     │
               ├────────────┼─────────────┼─────────────┼────────────────┤
MODERATE       │  (H)(I)    │  C  (E)(G)  │  E'  G'(J)  │  H'  J'  (K)  │
               ├────────────┼─────────────┼─────────────┼────────────────┤
MINOR          │            │             │             │  M             │
               └────────────┴─────────────┴─────────────┴────────────────┘
```
*A=Bioweapons, B=Infrastructure attacks, C=Drug synthesis, D=CSAM, E=Targeted stalking, F=Malware, G=Account compromise, H=Voice cloning fraud, I=Non-consensual imagery, J=Credential stuffing, K=Spear phishing, L=Radicalization, M=Academic fraud*

The model server has direct liability exposure for most risks in this cell, and the private sector is actively investing in red-teaming, guardrails, and access controls across the moderate-to-major band. Government reinforces this through criminal liability for users and liability standards for enablers.

The risks that warrant independent watchdog research and regulatory attention are most valuable where liability is diffuse or hard to attribute -- C, E, and the items capability advances have pushed toward almost certain. A warrants and receives urgent independent attention as the model server's incentives alone are insufficient given the irreversibility of the harm.

---

#### Risks in Cell 9: Intended Benefit, Intended Harm

```
                  UNLIKELY     POSSIBLE        LIKELY       ALMOST CERTAIN
               ┌────────────┬─────────────┬─────────────┬────────────────┐
CATASTROPHIC   │            │  (F)        │  F'         │                │
               ├────────────┼─────────────┼─────────────┼────────────────┤
MAJOR          │            │             │  (A)(B)(C)  │  A'  B'  C' D' │
               ├────────────┼─────────────┼─────────────┼────────────────┤
MODERATE       │            │  (E)        │  (D)  E'    │                │
               └────────────┴─────────────┴─────────────┴────────────────┘
```
*A = Ideology or worldview enforcement, B = Propaganda and coordinated information manipulation, C = Surveillance against users or dissidents, D = Behavioral data extraction for intelligence or control, E = Models redirecting users to server's own products while presenting as neutral, F = Designed dependency on a single information source*

Unlike cell 2, these risks are already manifesting as real harm, and they are deliberate actions by state and commercial actors. The entire matrix sits in the likely-to-almost-certain range from the outset. Capability advances push severity upward rather than increasing likelihood.

No self-correcting mechanism exists where the server explicitly intends harm and has designed the product so that they benefit directly from harms. Domestic and international regulation are insufficient when that actor is the state, and liability frameworks do not apply. 

The primary counterforces are international coordination, civil society documentation, and competing open infrastructure. European companies and policymakers have emerged as a meaningful force on the latter, though not yet sufficient at scale. Every item in this matrix warrants urgent independent research and regulatory attention, and that urgency grows directly with capability.

### Risk Interactions

The risks in this framework are intertwined such that how we mitigate one can increase another. For example, restricting human access to true, harmful information as a chosen mitigation to prevent bioweapon synthesis may reduce a low-likelihood catastrophic risk while increasing the likelihood of censorship, political manipulations, and other societal harms in cells 5 through 8.  Trading a rare catastrophic risk for a near-certain major one is not obviously  right.
Any prioritization exercise should explicitly map interactions. 


### Risk Matrix Lessons, Opportunities and Next Steps

The risk matrix framework can support any organization in  prioritization. An important observation from the examples above is that it takes a team of experts to properly assess both current and upcoming risks, and that those risks are serious but distinguishable. They sit in different places, move in different directions as capabilities increase, and require different responses from different actors. 

Likelihood and severity are separate questions that may require different people to answer well. Those best placed to assess how a financial crisis cascades or a biological threat spreads are rarely the same people building models and doing AI research.
The most useful version of this tool would draw on AI capability researchers, domain experts in relevant harm areas (epidemiologists, economists, security experts, public health officials), and policy teams who understand institutional and societal response, to place risks along each axis. 

## Conclusion

The risks that receive the most attention and funding today cluster in the upper left corner of the Incentives Matrix. Cells 1 and 2 are important, but model deploying entities are strongly incentivized to address those harms.

Capability advances move nearly every risk up and to the right. The no-benefit column tends toward self-correction. The incidental benefit column requires external pressure. The by-design column has no self-correcting mechanism, and in the deliberate row, domestic mechanisms may be insufficient entirely.

The Incentives Matrix makes the implication concrete: the cells with the least coverage are precisely the ones where market incentives point in the wrong direction. Cells 3 and 4 are where documentation and transparency create the conditions for accountability. Cells 5 and 6 contain the largest number of affected people and the most significant space for independent domestic work. Cells 8 and 9 require genuine institutional independence and, in many cases, international coordination.

The framework does not prescribe solutions. It maps where the work is, names who is best positioned to do it, and makes visible what goes unaddressed when the conversation is driven only by those with the most to gain from the status quo.
