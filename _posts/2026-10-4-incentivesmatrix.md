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

We are in a period of unprecedented growth in AI safety, but resources and media attention concentrate heavily on harms caused by accidental model failures and user-generated exploits. Model creators have strong market incentives and liability exposure to manage this vital product work, leaving opportunities for independent bodies to elevate broader societal risks.

The AI Safety Incentives Matrix examines safety through the lens of economic and power motivations of the entity serving the model. Harms are categorized by the server's **Awareness** at the time of deployment, and the subsequent **Benefits** (in profit or power) that the server derives from that harm. The model server is typically a private sector actor but may also be a government entity. 

**Key Insights:**
- Market forces naturally fix product-level safety issues (like accidental errors or user exploits) because they directly threaten user retention and create corporate liability.
- Corporate alignment fails at societal externalities (like workforce deskilling, economic instability, or intentional data extraction) because these harms either generate revenue or serve as a structural byproduct of the business model.
- Comprehensive safety efforts require attention across the entire AI Safety Incentives Matrix and continuous collaboration between independent researchers, who inform public standards, and governance experts, whose evolving mandates actively shape the technical research agenda.
- Safety interventions involve trade-offs. Mitigating a technical threat can inadvertently amplify a governance risk, eg. restricting information access at the cost of expanding censorship infrastructure.
- Prioritizing risks is a collaborative exercise. AI experts are needed to estimate the likelihood of a new capability, policy experts to assess how regulatory coverage reduces that likelihood, and economists, epidemiologists, and domain specialists to assess the severity of real-world fallout.


## The AI Safety Incentives Matrix

<figure style='display: table'>
  <img src="{{site.baseurl}}/assets/images/HarmAxes.png" alt="Motivations in AI Safety">
  <figcaption style='display: table-caption; caption-side: bottom;'>
  Cell color indicates likely motivations of server to surface and address harms. More details about actors, example harms, and common mitigations in each cell can be found in the Appendix. </figcaption>
</figure>

Mapping the landscape along these boundaries offers a few advantages and observations:

- This framework is insensitive to advances in capability. Chatbots, code assistants, autonomous agents, and eventually embodied AI will have different reach, but the core incentives don't change.
- Tech creators are naturally motivated to fix harms that threaten user retention or create legal liability. This framework helps independent organizations spot the remaining gaps that the market has no financial interest in solving.
- Harms move from unaware to intentional with documented public awareness.
- Trade-offs among interventions emerge. For example, restricting information access to (true) dangerous information may come at the cost of expanding censorship infrastructure.


The following sections analyze where existing research and policy efforts overlap with corporate incentives, and identify gaps where independent oversight is required to secure the broader ecosystem.


*Note: This framing assumes that there is an entity serving a model with a motivation (typically profit or power), and highlights where the profit motive aligns with addressing harms. There are those who believe that open source models are inherently dangerous because a bad actor could remove safety guardrails to enable nefarious use. That actor would either deploy the model, in which case this framework applies, or they would use it internally. Internal use narrows the threat surface, and an actor with the capability and resources to do this meaningfully would not require open source weights as a starting point.*

## Key research and governance efforts

A significant portion of AI safety efforts are aligned with internal motivations of model creators and servers. This makes sense, as they fund a lot of the work, but the entire matrix matters. Consider some of the largest efforts underway, and where they sit on the matrix. 

<figure style='display: table'>
  <figcaption style='display: table-caption; caption-side: top; font-weight: bold; margin-bottom: 8px;'>
    Safety Research Areas: Evidence and Action
  </figcaption>
  <img src="{{site.baseurl}}/assets/images/HarmAxes-Efforts.png" alt="Motivations in AI Safety">
</figure>


Across the upper rows, researcher benchmarks define what a server could be expected to know, and governance efforts translate expectation to obligation. 

In the lower region of the matrix, the interaction between governance and research shifts. Mandates around privacy and model sovereignty establish initial boundaries and compliance criteria, driving AI research toward new, trustworthy system architectures.

Continuous collaboration across governance, policy research, and AI research is vital to combat AI harms. Commercial institutions are motivated primarily by product quality and short-term profitability. Independent bodies must support the most dangerous harms everywhere, and are the only entities who will freely prioritize issues like workforce deskilling, infrastructure consolidation, financial instability, and climate impacts. 

If the conversation around AI safety is driven primarily by one type of institution, particularly one focused on product quality and profitability, large swaths of vital work will be overlooked.


---

## Prioritizing risks within a cell

Harms that may arise from AI are not all equal. A traditional risk matrix plots risks on **likelihood** and **severity** axes.  Today, some risks seem less urgent because we implicitly trust the model server to prevent them. Explicitly mapping harms can highlight questions of standards, protections, or assurances that could be put in place today. 

Harms in AI safety are expected to be incredibly impactful to life on Earth. To differentiate them along the severity axis, the following definitions are used:
- **Catastrophic:** Irreversible harm at civilizational scale. 
- **Major:** Severe harm to large populations, institutions, or democratic systems. Recoverable in principle but with significant long-term consequences. 
- **Moderate:** Meaningful harm to specific communities, groups, or sectors. Addressable with targeted policy or technical intervention. 
- **Minor:** Limited harm to individuals or small groups. Recoverable without systemic intervention. 

Risk matrices are not static! Advances in model capability increase both likelihood and severity, while progress in policy and governance push likelihood down.

---


### Harms that incidentally benefit the server (cell 2)

<figure style='display: table'>
  <img src="{{site.baseurl}}/assets/images/Cell2riskmat.png" alt="Risk Prioritization">
  <figcaption style='display: table-caption; caption-side: bottom;'>
  Notation: (A) marks a risk's original position, A' marks its position after recent capability advances (multi-agent collaboration, significant audio and video improvements), and A alone means it did not move. Harms:
  A=Bioweapon synthesis, B=Infrastructure attacks, C=Drug synthesis, D=CSAM, E=Targeted stalking, F=Malware, G=Account compromise, H=Voice cloning fraud, I=Non-consensual imagery, J=Credential stuffing, K=Spear phishing, L=Radicalization, M=Academic fraud</figcaption>
</figure>


For these harms, the entity serving the model has direct market incentive and liability exposure. The private sector is actively investing in red-teaming, guardrails, and access controls across the moderate-to-major band. Independent efforts are needed to ensure compliance and document concerning findings. Government reinforces the work through criminal liability for users and liability standards for enablers. 

---

### Harms that intentionally benefit the server (cell 9)

<figure style='display: table'>
  <img src="{{site.baseurl}}/assets/images/Cell9riskmat.png" alt="Risk Prioritization">
  <figcaption style='display: table-caption; caption-side: bottom;'>
  Notation: (A) marks a risk's original position, A' marks its position after recent capability advances (multi-agent collaboration, significant audio and video improvements), and A alone means it did not move.  Harms:
  A = Ideology or worldview enforcement, B = Propaganda and coordinated information manipulation, C = Surveillance against users or dissidents, D = Behavioral data extraction for intelligence or control, E = Models redirecting users to server's own products while presenting as neutral, F = Designed dependency on a single information source</figcaption>
</figure>


Many intentional harms sit in the likely-to-almost-certain range when evaluating AI capability. Policy progress pushes likelihood down, while advances in model capability push severity upward. 

The primary counterforces are international coordination, civil society documentation, and competitive open infrastructure. European companies and policymakers are making meaningful progress, but every harm warrants urgent independent research and regulatory attention. That urgency grows with capability.

---


### Final notes on prioritization 

**Risk Interactions** The risks in this framework are intertwined such that how we mitigate one can increase another. Restricting human access to (true) harmful information may mitigate the risk of bioweapon synthesis at the cost of increasing liklihood of censorship and political manipulations. Similarly, significant advances in interpretability and model steering will reduce harms in cells 1 and 2, while increasing likelihood of those in the rightmost column.

**Divers expertise for proper placement** The experts best positioned to assess severity of a harm, eg. how a financial crisis cascades or a biological threat spreads, are not likely to be the same as the AI and policy experts who can accurately assess likelihood. The most useful risk matrix would draw on experts from many domains to accurately place harms.


---



## Conclusion

The risks that receive the most attention and funding today cluster heavily in the upper-left corner of the AI Safety Incentives Matrix. Media and public discourse focus on accidental errors and user-generated exploits, where model-deploying entities are strongly incentivized. 

There are true challenges in the areas where harm is profitable, intentional, or structurally systemic. The opportunity for independent organizations are vital, and require collaboration among researchers building  benchmarks to drag hidden harms into the light, and  governance experts building policy frameworks to translate that awareness into legal obligation. 

By increasing the focus on harms whose solutions are not naturally aligned with corporate interests, and toward funding this critical research-governance alliance, civil society can build the independent, sovereign infrastructure necessary to secure our digital future.



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
- **Example Harms:** Emotional dependency from retention-optimized design, bias and discrimination from unexamined training data
- **Common Countermeasures:** Independent harm audits, bias testing and fairness benchmarks, third-party dataset audits, training data provenance disclosure

---

### 4. No Benefit, Known Harm

*Economic instability and environmental impacts*

This category covers scenarios where the model server is aware of harms to workers, communities, or the environment but does not benefit from those specific harms -- and may in fact be negatively affected by them.

- **Actor:** Model server
- **Benefit:** None
- **Harm falls on:** Workers, local communities, future generations, environment
- **Who can act and why:** Model server has mixed motivation; policy bodies can establish standards and penalties
- **Example Harms:** Large-scale climate impacts, mass labor displacement at societal scale, systemic economic instability, biased automated decisions in criminal justice and hiring
- **Common Countermeasures:** Environmental impact assessments (regulators), workforce impact disclosure (regulators), labor transition frameworks (governments), bias testing and fairness requirements for automated decision systems (regulators), mandatory human review for high-stakes automated decisions in criminal justice and hiring (regulators)

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
- **Example Harms:** Concentration of power, engagement farming, deliberately engineered compulsive use, local environmental harms near data centers, deliberately opaque personalization, economic collapse due to circular investment structures
- **Common Countermeasures:** Sovereign and open model infrastructure approaches (companies, governments), independent technical audits with platform data access (regulators, NGOs), mandatory disclosure of internal safety research (regulators), whistleblower protections (governments), financial disclosure requirements (regulators), energy and water use standards (regulators)


---

### 8. Incidental Benefit, Intended Harm
*Population-level surveillance*

The model server deliberately causes or enables harm. The benefit accrues as a side effect of that decision rather than a designed outcome.

- **Actor and beneficiary:** Model server -- market access, competitive positioning, or regulatory favor as a side effect
- **Harm falls on:** Users, competitors, democratic institutions
- **Who can act and why:** Model server has no incentive; civil society, government, and international bodies
- **Example Harms:** Deliberate output adjustment to comply with government censorship in exchange for market access, deliberate compliance with surveillance requirements that compromise user privacy, politically selective content filtering in specific markets
- **Common Countermeasures:** Output auditing (civil society, regulators), extraterritorial regulatory frameworks (governments), minimum content standards (international bodies), sovereign and open model infrastructure approaches (companies, governments)

---

### 9. Designed Benefit, Risk or Harm Intended
*Population-level control*

The model server designed the system to produce harm because the harm is beneficial to them. This applies equally to private companies and governments acting as model servers. The harm drives the business model, so the server will not voluntarily fix it.

- **Actor and beneficiary:** Model server
- **Harm falls on:** Users with no ability to opt out, those subject to surveillance or targeting, democratic institutions, free information markets
- **Who can act and why:** Model server has no incentive; for private actors, domestic regulation and civil society; for state actors, international bodies, civil society, and competing governments
- **Example Harms:** Ideology or worldview enforcement through controlled model outputs, propaganda and coordinated information manipulation at scale, surveillance infrastructure deployed against users or dissidents, behavioral data extraction for intelligence or control purposes, models redirecting users to server's chosen products or interests, identifying and targeting of political dissidents
- **Common Countermeasures:** International treaty frameworks (governments, international bodies), cross-border technical auditing (international bodies, civil society), transparency and whistleblower protections (governments), competing sovereign and open model infrastructure as a structural alternative to state or monopoly control (governments, international bodies)
