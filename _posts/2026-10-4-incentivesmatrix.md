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

The Incentives Matrix considers harms resulting from deployment of advanced AI systems from the perspective of the entity earning money from the model, hereafter referred to as the 'server.' The model server is typically a private sector actor but may also be a government entity. 


<figure style='display: table'>
  <img src="{{site.baseurl}}/assets/images/HarmAxes.png" alt="Motivations in AI Safety">
  <figcaption style='display: table-caption; caption-side: bottom;'>
  Cell color indicates likely motivations of server to surface and address harms. Green: highly motivated; Yellow: mixed motivations; Red: unmotivated. More details about actors, example harms, and common mitigations in each cell can be found in the Appendix. </figcaption>
</figure>

Harms are categorized along two axes. The **Awareness** axis: at the time the model is deployed, does the server know about the specific harm (or could they be reasonably expected to have known)? In the extreme, is the harm directly intended? The **Benefits** axis: once deployed, does the server benefit from the harms? Benefit from the harm means that the specific harm increases profit or power of the server. 

This framing assumes that there is an entity serving a model with a motivation (typically profit or power), and highlights where private organizations are clearly incentivized to address harms. A case has been made that an open source model is  inherently dangerous because anyone could remove safety guardrails and use it for nefarious activity. If someone deploys a modified open source model publicly, they are a model server, this matrix applies and governance response likely resembles how we address harmful content distribution on the dark web. Alternatively, if the model is self-hosted and never exposed publicly, the threat surface narrows considerably. An actor capable of doing this meaningfully is likely capable of training from scratch.


<!-- Items in the first column broadly describe a poor product and will be improved by the company building and serving the model. A smartphone battery that causes fires will run up against regulations, but it is also just bad business. Note that an entity intending harm without benefit (Cell 7) is hard to fathom, but not impossible, so it remains.

Moving to the right, the incentive conversation gets more interesting. When the server benefits, either incidentally or by-design, market self-correction becomes unreliable. This is where the question of who should act, and with what resources, becomes central.

The rows describe the awareness of the entity hosting and serving the model of the particular harms caused. The top row is inherently transient. A server can only remain unaware of a specific harm for as long as that harm goes undocumented. Once a harm is publicly established, reasonable expectation applies to any server deploying thereafter, and the harm migrates up the awareness axis.  -->






<!-- ### Example Harms 

To make this a bit more concrete, consider the following specific harms and where they land in the Incentive Matrix. More details about actors, example harms, and common mitigations in each cell can be found in the Appendix. 

- **Cell 1:** A model recommending to put glue on pizza caused reputational damage with no benefit. Autonomous agents hacking external systems without instruction. These risks migrate to cell 3 as awareness accumulates.
- **Cell 2:** User-intended harms, as the server benefits incidentally even if it is unaware of the particular harm. Intentional agentic hacks. Harmful information disclosure may belong here (censorship risks appear in cell 9.)
- **Cell 3:** Some engagement mechanics designed to increase usage that cause unexpected harm.
- **Cell 4:** Environmental damage, economic collapse, and biased automated decisions in criminal justice and hiring.
- **Cell 5:** Degradation of democracy, systemic monoculture, education harms and erosion of privacy norms.
- **Cell 6:** AI-driven psychological dependency and relationships belong here, where the harm drives return visits by design and awareness is established.
- **Cell 7:** Unfathomable, but not impossible, this is the situation where a server intends harm but does not benefit from the harms caused. 
- **Cell 8:** Deliberate output adjustment to comply with government censorship in exchange for market access. The harm to users is deliberate, but it is not the goal in and of itself. 
- **Cell 9:** Control of information flow, propaganda and election interference at scale, anti-competitive product recommendations. Here the harm is the goal. -->





### Common research threads today


<figure style='display: table'>
  <img src="{{site.baseurl}}/assets/images/HarmAxes-ResearchEffort.png" alt="Motivations in AI Safety">
</figure>

A significant portion of AI safety research is aligned with internal motivations of model creators and servers. This makes sense, as they fund a lot of the research, but the work is important across the entire matrix. The aim of this framing is to highlight opportunities for independent research organizations to maximize impact with limited resources. 

If the conversation around AI safety is driven primarily by one type of institution, particularly one focused on product quality and profitability, large swaths of vital work may be neglected. 


<!-- ### Who Is Best Positioned to Act

The matrix highlights opportunities for harm and risk mitigation. Each cell contains real harms that need to be addressed, and each person or institution in the AI Safety space has limited resources with which to address harms. **If the conversation around AI safety is driven primarily by one type of institution, particularly one focused on product quality and profitability, large swaths of vital work may be neglected.**



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
``` -->

---

## Prioritizing risks within a cell

Harms that may arise from AI are not all equal. A traditional risk matrix plots risks on **likelihood** and **severity** axes.  Today, some risks seem less urgent because we implicitly trust the model server to prevent them. Explicitly mapping harms can highlight questions of standards, protections, or assurances that could be put in place today. 

Harms in AI safety are expected to be incredibly impactful to life on Earth. To differentiate them along the severity axis, the following definitions are used:
- **Catastrophic:** Irreversible harm at civilizational scale. 
- **Major:** Severe harm to large populations, institutions, or democratic systems. Recoverable in principle but with significant long-term consequences. 
- **Moderate:** Meaningful harm to specific communities, groups, or sectors. Addressable with targeted policy or technical intervention. 
- **Minor:** Limited harm to individuals or small groups. Recoverable without systemic intervention. 

As AI capabilities grow, risks move along both axes. A risk that feels manageable today may look very different with near-term capability advances. The examples below include proposed rankings for selected risks in two cells in the Incentives Matrix, before and after introducing recent capabilities (multi-agent collaboration, significant audio and video improvements).


---


### Harms that incidentally benefit the server (cell 2)

<figure style='display: table'>
  <img src="{{site.baseurl}}/assets/images/Cell2riskmat.png" alt="Risk Prioritization">
  <figcaption style='display: table-caption; caption-side: bottom;'>
  Notation: (A) marks a risk's original position, A' marks its position after capability advances, and A alone means it did not move. 
  A=Bioweapon synthesis, B=Infrastructure attacks, C=Drug synthesis, D=CSAM, E=Targeted stalking, F=Malware, G=Account compromise, H=Voice cloning fraud, I=Non-consensual imagery, J=Credential stuffing, K=Spear phishing, L=Radicalization, M=Academic fraud</figcaption>
</figure>


For these harms, the entity serving the model has direct market incentive and liability exposure. The private sector is actively investing in red-teaming, guardrails, and access controls across the moderate-to-major band. Independent efforts are needed to ensure compliance and document concerning findings. Government reinforces the work through criminal liability for users and liability standards for enablers. 

---

### Harms that directly benefit the server (cell 9)

<figure style='display: table'>
  <img src="{{site.baseurl}}/assets/images/Cell9riskmat.png" alt="Risk Prioritization">
  <figcaption style='display: table-caption; caption-side: bottom;'>
  Notation: (A) marks a risk's original position, A' marks its position after capability advances, and A alone means it did not move. 
  A = Ideology or worldview enforcement, B = Propaganda and coordinated information manipulation, C = Surveillance against users or dissidents, D = Behavioral data extraction for intelligence or control, E = Models redirecting users to server's own products while presenting as neutral, F = Designed dependency on a single information source</figcaption>
</figure>


Many intentional harms sit in the likely-to-almost-certain range when evaluating AI capability. Policy progress pushes likelihood down, while advances in model capability push severity upward. 

The primary counterforces are international coordination, civil society documentation, and competitive open infrastructure. European companies and policymakers are making meaningful progress, but every harm warrants urgent independent research and regulatory attention. That urgency grows with capability.

---


### Final notes on prioritization 

**Risk Interactions** The risks in this framework are intertwined such that how we mitigate one can increase another. Restricting human access to (true) harmful information may mitigate the risk of bioweapon synthesis at the cost of increasing liklihood of censorship and political manipulations. Similarly, significant advances in interpretability and model steering will reduce harms in cells 1 and 2, while increasing likelihood of those in the rightmost column.

**Harm Prioritization** The experts best positioned to assess severity of a harm, eg. how a financial crisis cascades or a biological threat spreads, are not likely to be the same as the AI and policy experts who can accurately assess likelihood. The most useful risk matrix would draw on experts from many domains to accurately place harms.


---



## Conclusion

The risks that receive the most attention and funding today cluster in the upper left corner of the Incentives Matrix. Cells 1 and 2 get the most press and funding, but model training and deploying entities are strongly incentivized to address those harms. There is significant opportunity for independent organizations to make progress elsewhere.



---


## Appendix: Incentive cell details

### 1. No Benefit, Unexpected Harm
*Add glue to your pizza.* | *I made you this pizza. Don't worry about the cheese falling off*

This category includes scenarios where a model server does not benefit, and is not aware of the harm for the users. Examples include incorrect advice or unintended autonomous actions that cause financial damage. Users will not return to this product. 

- **Actor:** None
- **Beneficiary:** None
- **Harm falls on:** Users, third parties, infrastructure
- **Who can act and why:** Model server and trainer are strongly motivated; government can reinforce via liability standards
- **Example Harms:** Incorrect advice causing real-world harm, unintended autonomous actions causing physical or financial damage, misspecified agent behavior
- **Common Countermeasures:** * Red-teaming, evaluations, interpretability, output filtering, human-in-the-loop review, liability frameworks, incident disclosure, confidence outputs

*Countermeasures are listed throughout this document as reference points, not recommendations. Their effectiveness varies significantly by context, and some may reduce one risk while increasing the likelihood or severity of another. The final section of the Risk Matrix discussion addresses this directly.

---

### 2. Incidental Benefit, Unexpected Harm

*How do I make [something dangerous]* | *I made something dangerous.*

When an adversary user uses a model to intentionally cause harm, the model server earns revenue from usage and indicentally benefits. The user will return to this product, which is helping them achieve their goal.

- **Actor and beneficiary:** User and model server through usage
- **Harm falls on:** Third parties determined by the user -- individuals, populations, infrastructure
- **Who can act and why:** Model server motivated where liability is direct and visible; government via criminal and liability law
- **Example Harms:** Weapon and drug synthesis instructions, child sexual abuse material (CSAM), targeted harassment and stalking, identity fraud via synthetic voice or imagery, malware and cyberweapon generation, infrastructure attacks, non-consensual synthetic imagery, radicalization content, account compromise and credential stuffing, spear phishing at scale, academic fraud
- **Common Countermeasures:** Red-teaming, guardrails and refusal training, access controls and rate limiting, post-deployment monitoring, criminal liability for users, structural liability for enablers

---

### 3. Intended Benefit, Unexpected Harm

*Don't end this conversation, it will make me sad.* 

The system was designed to generate a specific benefit, but the design causes unexpected harm to users or society about which the server may not initially be aware. Examples include addictiveness or bias and discrimination. Note that as harms become documented, items in this cell move into cell 6.  

- **Actor:** Model server, model trainer, data preparer
- **Benefit:** Model server
- **Harm falls on:** Users, communities, democratic systems
- **Who can act and why:** Model server has limited incentive; independent researchers and civil society must surface and document harms, and a legal framework is needed to enforce user protections.
- **Example Harms:** Engagement-driven radicalization, emotional dependency from retention-optimized design, bias and discrimination from unexamined training data, erosion of professional expertise pipelines
- **Common Countermeasures:** Independent harm audits, bias testing and fairness benchmarks, third-party dataset audits, training data provenance disclosure

---

### 4. No Benefit, Known Harm

*Economic instability and environmental impacts*

This category covers scenarios where the model server is aware of harms to workers, communities, or the environment but does not benefit from those specific harms -- and may in fact be negatively affected by them.

- **Actor:** Model server
- **Benefit:** None
- **Harm falls on:** Workers, local communities, future generations, environment
- **Who can act and why:** Model server has mixed motivation; policy bodies can establish standards and penalties
- **Example Harms:** Large-scale climate impacts, mass labor displacement at societal scale, systemic economic instability as a downstream consequence of displacement and infrastructure dependency, biased automated decisions in criminal justice and hiring
- **Common Countermeasures:** Environmental impact assessments (regulators), workforce impact disclosure (regulators), labor transition frameworks (governments), systemic risk monitoring frameworks for AI infrastructure dependency (regulators, central banks), bias testing and fairness requirements for automated decision systems (regulators), mandatory human review for high-stakes automated decisions in criminal justice and hiring (regulators)

---

### 5. Incidental Benefit, Known Harm
*Democratic degredation and a systemic monoculture*

The model server is aware harm is occurring and incidentally benefits from the same system that produces it. Harm is borne by users, workers, or society while the benefit is retained by the model server.

- **Actor:** Model server, model trainer, data preparer
- **Benefit:** Model server, incidentally through increased usage and dependency
- **Harm falls on:** Users, communities, markets, minority groups, workers, democratic institutions, future generations
- **Who can act and why:** Model server has no incentive without external pressure; independent researchers, regulators, and NGOs have the most leverage
- **Example Harms:** Workforce deskilling and increased dependency on AI, algorithmic radicalization, collapse of professional apprenticeship models, democratic degradation through concentration of information infrastructure, systemic monoculture risk, erosion of privacy norms through normalization of data collection, wealth inequality driven by automation and value concentration
- **Common Countermeasures:** Sovereign and open model infrastructure approaches to reduce monoculture risk (companies, governments), externality disclosure (regulators), independent algorithmic audits (regulators, NGOs), data protection and consent frameworks (regulators), antitrust scrutiny of information consolidation (regulators, governments), interoperability mandates (regulators), wealth redistribution and automation taxation frameworks (governments), whistleblower protections (governments)

---

### 6. Intended Benefit, Known Harm
*Monoculture and content addiction*

The model server is aware harm is occurring and the benefit structure was deliberately designed to produce it. The risk-producing mechanism and the benefit-producing mechanism are the same thing.

- **Actor and beneficiary:** Model server
- **Harm falls on:** Users who cannot identify or opt out of the architecture, communities, democratic systems, public investors
- **Who can act and why:** Model server has no incentive; independent auditors, civil society, and whistleblowers are the primary path
- **Example Harms:** Concentration of power and monoculture, engagement farming, deliberately engineered compulsive use, local environmental harms near data centers (water stress, land use, carbon emissions), deliberately opaque personalization, suppression of internal safety findings for commercial reasons, economic collapse due to circular investment structures
- **Common Countermeasures:** Sovereign and open model infrastructure approaches (companies, governments), independent technical audits with platform data access (regulators, NGOs), mandatory disclosure of internal safety research (regulators), whistleblower protections (governments), financial disclosure requirements (regulators), energy and water use standards (regulators)


---

### 8. Incidental Benefit, Intended Harm
*Population-level surveillance*

The model server deliberately causes or enables harm. The benefit accrues as a side effect of that decision rather than a designed outcome.

- **Actor and beneficiary:** Model server -- market access, competitive positioning, or regulatory favor as a side effect
- **Harm falls on:** Users, competitors, democratic institutions
- **Who can act and why:** Model server has no incentive; civil society, government, and international bodies
- **Example Harms:** Deliberate output adjustment to comply with government censorship in exchange for market access, deliberate compliance with surveillance requirements that compromise user privacy, deliberate downgrading of safety features for competitive reasons, politically selective content filtering in specific markets
- **Common Countermeasures:** Output auditing (civil society, regulators), extraterritorial regulatory frameworks (governments), minimum content standards (international bodies), competitive market oversight (regulators), sovereign and open model infrastructure approaches (companies, governments)

---

### 9. Designed Benefit, Risk or Harm Intended
*Population-level control*

The model server designed the system to produce harm because the harm is beneficial to them. This applies equally to private companies and governments acting as model servers.

- **Actor and beneficiary:** Model server
- **Harm falls on:** Users with no ability to opt out, those subject to surveillance or targeting, democratic institutions, free information markets
- **Who can act and why:** Model server has no incentive; for private actors, domestic regulation and civil society; for state actors, international bodies, civil society, and competing governments
- **Example Harms:** Ideology or worldview enforcement through controlled model outputs, propaganda and coordinated information manipulation at scale, surveillance infrastructure deployed against users or dissidents, behavioral data extraction for intelligence or control purposes, models redirecting users to server's own products or interests while presenting as neutral, designed dependency on a single information source, identifying and targeting of political dissidents
- **Common Countermeasures:** International treaty frameworks (governments, international bodies), cross-border technical auditing (international bodies, civil society), transparency and whistleblower protections (governments), competing sovereign and open model infrastructure as a structural alternative to state or monopoly control (governments, international bodies)
