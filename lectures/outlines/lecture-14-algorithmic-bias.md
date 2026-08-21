# Algorithmic Bias, Lecture 14

**Week:** 6 (Wednesday, Oct 14, Monday Oct 12 is Thanksgiving, no class)
**Length:** 50 min
**Unit:** Digital Adolescence

## Learning Goals

By the end of this lecture, students should be able to:

- Given a documented algorithmic system, identify its inputs, decision logic, and outcome/impact.
- Classify a real-world case using at least one of Ruha Benjamin's four categories (engineered inequity, default discrimination, coded exposure, technological benevolence), justify the choice, and name a plausible alternative classification.
- Identify the stakeholders in an algorithmic system and at least one positive and one negative effect (reusing the Week 3 Stakeholders + Effects framework).
- Name which course mechanism (decision tree, weighted scoring and thresholds, feedback loop, training-data gap, proxy variable) a system's harm turns on, or recognize when none apply cleanly and something else, like consent, is doing the work instead.
- Construct one argument for and one against a company changing its algorithm in response to a fairness critique, grounded in a real trade-off.

## Big Idea

This is not a new-content lecture, it's the analytical layer on top of content students already have. They know how algorithms get built (decision trees, sequencing, selection) and they've seen biased data raised in passing. This lecture's job is the move Project 1C asks them to do independently two weeks later: given a real system, identify what went in, how it decided, who it affected, name the mechanism, and argue why. Two real cases, same analytical structure both times, so the structure becomes portable.

**BIG IDEA** Algorithms are not neutral, and how we talk about algorithms shapes how society reacts to them.

**Connection from last class:**
Week 5 built the toolkit: Lecture 12's surge-pricing feedback loop and neighbourhood problem (explicitly promised a full treatment "next week"), and Lecture 13's loan-approval decision tree (inputs, logic, outcome). Week 3's Data Privacy supplied the Stakeholders + Effects framework.

**Where we're going next:**
Project 1 Part C, the written bias case study, is due Week 7, and this lecture is the rehearsal for it.

## References

- Ruha Benjamin, *Race After Technology*, the four categories
- Meredith Broussard, *Artificial Unintelligence*, technochauvinism; "computers can only calculate mathematical fairness, not social fairness"
- Office of the Privacy Commissioner of Canada, joint investigation report on Clearview AI (Feb 3, 2021)
  - https://www.priv.gc.ca/en/opc-news/news-and-announcements/2021/nr-c_210203/
- OPC statement on the RCMP investigation (June 10, 2021)
  - https://www.priv.gc.ca/en/opc-news/news-and-announcements/2021/nr-c_210610/
- CCLA summary of the Clearview AI findings
  - https://ccla.org/privacy/surveillance-technology/clearview-ai-engaged-in-mass-surveillance/
- Business Daily Africa coverage of Worldcoin's data deletion, confirmed by Kenya's ODPC (Jan 2026)
  - https://www.businessdailyafrica.com/bd/corporate/technology/worldcoin-deletes-kenyans-biometric-data-after-court-order-5333600
- ICT Journal Africa coverage of the Kenyan High Court order (May 2025)
  - https://www.ictjournal.africa/post/worldcoin-iris-data-wiped-as-kenya-tightens-grip-on-biometric-tech
- Rest of World, on the broader pattern of biometric collection across countries
  - https://restofworld.org/2026/sam-altman-worldcoin-zoom-tinder-partnerships/
- New: confirmation of the Tinder, Zoom, and Docusign World ID partnerships (April 2026), resolving the uncertainty flagged in an earlier draft
  - https://www.gncrypto.news/news/world-upgrades-world-id-tinder-zoom-docusign/

---

## Lecture Flow

### 0. Pre-Class Preparation

Two short case briefs, each written in **Input / Decision logic / Outcome** format, the same structure used in the in-class recap slides, deliberately, so students see one framing not two.
_I keep on going back and forth on this, should we give them the articles, or should we give them shorts on the articles_

- Clearview AI & the RCMP (Canada)
- Worldcoin / Tools for Humanity (Kenya)

Distributed with the **Friday Oct 9** materials, since Thanksgiving means there's no Week 6 Monday lecture to attach them to.

No pre-read accountability quiz. Thinner discussion from students who skip the reading is an accepted tradeoff, not a bug to fix.

### 1. Welcome, Agenda, Callback, ~3 min

**0:00-0:03.** Frame the lecture as a repeat of a familiar move, not new material:

> "Remember tracing the loan-approval decision tree on Friday, inputs, logic, outcome? Today, same move, pointed at two real systems, with a bias lens on top."

**Point:** Lowers the perceived novelty. Students already own the analytical tool; today they aim it at something real.

### 2. Benjamin's Four Categories, ~9 min

**0:03-0:12.** One-liner plus one quick example each:

| Category | One-liner |
|---|---|
| **Engineered inequity** | The system produces unequal outcomes by design or by deliberate targeting |
| **Default discrimination** | Nobody intended harm; the harm follows from indifference and unexamined defaults |
| **Coded exposure** | Being made visible, surveilled, or legible to a system without consent |
| **Technological benevolence** | Marketed as helping the disadvantaged; the help is the framing, the extraction is the substance |

For **engineered inequity**, recap the Week 5 surge-pricing neighbourhood loop rather than introducing a new case, it costs 30 seconds instead of 3 minutes and pays off the "we'll come back to this" promise from Lecture 12.

**Point:** Four labels, deliberately overlapping. The categories are argumentative tools, not a taxonomy with correct answers, which is why every clicker below asks "and where would you push back?"

### 3. Case 1, Clearview AI & the RCMP (Canada), ~14 min

**0:12-0:14, Recap slide.** Give both readings **equal visual weight**:

- **Input:** billions of photos scraped from the open internet without consent; the RCMP became a paying customer, with 48 accounts created across Canadian law enforcement and other organizations
- **Decision logic:** a submitted photo is matched against the scraped database to identify a person
- **Outcome:** Clearview withdrew its service from the Canadian market in July 2020, while the investigations were still underway; a joint federal/provincial privacy commissioner investigation then found the collection had constituted unlawful mass surveillance (Feb 2021); a second investigation found the RCMP itself violated the Privacy Act because it never verified Clearview's data was lawfully collected (June 2021)

**0:14-0:19, Pair discussion (5 min).** Prompt: *"Using the inputs, logic, and outcome you just saw: which category fits, and where would you push back? Then pick one stakeholder and name one positive and one negative effect."*

**0:19-0:21, CLICKER (forced single choice, no "more than one applies"):**

> Clearview AI scraped billions of photos and sold facial-recognition access to Canadian police, including the RCMP, without consent. Which of Benjamin's four categories best fits, and where would you push back on that label?

- A) Engineered inequity
- B) Default discrimination
- C) Coded exposure
- D) Technological benevolence

**0:21-0:26, Share-out**, anchored on the vote split. Leave room in this window to also hear one or two stakeholder answers, not just the category vote, that's the new material this draft adds and it needs airtime, not just a line in the prompt.

**Point:** Two defensible readings. Coded exposure is the obvious one; default discrimination, the RCMP simply never checking whether the data was legal, is the harder and more interesting one.

### 4. Case 2, Worldcoin / Tools for Humanity (Kenya), ~14 min

**0:26-0:28, Recap slide:**

- **Input:** iris scans via "Orb" devices, incentivized with cryptocurrency tokens, collected from economically vulnerable Kenyans; consent forms available only in English despite varying literacy and language backgrounds
- **Decision logic:** iris scan, unique biometric identifier, "World ID" / "proof of humanity" digital identity
- **Outcome:** Kenya's data protection regulator found consent inadequate; the High Court ordered deletion of all Kenyan biometric data (May 2025); deletion confirmed complete (Jan 2026); the company has since pivoted toward partnerships (Tinder, Zoom, Docusign, all now confirmed, see References)

**0:28-0:33, Pair discussion (5 min).** Same prompt structure as Case 1, minus the stakeholders add-on, that's deliberately scoped to Case 1 only so this discussion stays focused on category and pushback.

**0:33-0:35, CLICKER:**

> Worldcoin offered Kenyans cryptocurrency in exchange for iris scans, marketed as bringing digital identity and financial inclusion to the unbanked. A Kenyan court ordered all the data deleted. Which category best fits, and where would you push back?

- A) Engineered inequity
- B) Default discrimination
- C) Coded exposure
- D) Technological benevolence

**0:35-0:40, Share-out → LO4 debate.** Pivot with Broussard: *computers can only calculate mathematical fairness, not social fairness.* Then run the argument: should Worldcoin have to change its practices, and what would that cost the company versus the people who signed up?

**Point:** Genuine, live tension between technological benevolence (financial inclusion for the unbanked) and engineered inequity (targeting jurisdictions with weaker data-protection regimes). Expect a real vote split, this case has no dominant reading, which is exactly why it's second.

### 5. Naming the Mechanism, ~5 min

**0:40-0:45.** New section. This is where LO4 (mechanism-naming) actually gets rehearsed, it didn't exist in the previous draft at all, and it's worth more of Project 1C's grade (20%, template section 7) than the stakeholders addition above (15%). Placed after both cases rather than folded into either one, because the exercise below needs students to already know both cases.

**Fast recap, not new teaching, ~1 min:** "Project 1C section 7 asks you to name which course mechanism your case turns on. You already know four of the five: decision tree (Friday's loan approval), weighted scoring and thresholds (surge pricing), feedback loop (surge pricing's neighbourhood problem), proxy variable (what counts as 'demand'). One new one: **training-data gap**, when the data a system learned from doesn't represent everyone it's used on equally."

**Say explicitly, this is the point the earlier draft didn't make:** a case can turn on more than one of these, or on none of them cleanly. If neither Clearview nor Worldcoin maps onto one of the five without forcing it, that's a legitimate finding, not a failure to find the right box. Sometimes the honest answer is "this is really about consent, not one of our five patterns," and recognizing that is the more sophisticated move, not a lesser one.

**Pick-a-case pair discussion, ~3 min:** "In your pairs, pick *one* of today's two cases, Clearview or Worldcoin, not both. Spend three minutes: which mechanism does it turn on, if any? If none fit, say what's doing the work instead."

**Rapid share-out, ~1 min:** Cold-call one pair who picked Clearview, one pair who picked Worldcoin, so the whole room hears a reading of both, even though no individual student worked both. Don't chase consensus, there may not be one, and that's fine, it's the same "argumentative tool, not taxonomy" framing from Section 2.

### 6. Buffer / Contingency, ~2 min

**0:45-0:47.** This slot shrank from 6 minutes to 2 to make room for Section 5. That's a real trade-off, not an oversight, see Notes for Development. Use it for overrunning share-outs. The contingency case below now realistically needs the lecture to be running ahead of schedule to trigger at all, treat it as a bonus, not a safety net.

### 7. Wrap-Up, ~3 min

**0:47-0:50.**

- Every algorithmic system can be read as inputs → decision logic → outcome. That reading is the whole analytical move.
- Benjamin's categories are arguments, not answers, the justification matters more than the label.
- A case can turn on more than one mechanism, or none of the five cleanly. Naming that honestly is the skill, forcing a fit isn't.
- "Unintentional" is not the same as "not responsible." The RCMP wrote no biased rule; it simply never asked.

**Bridge to next class:** Friday we go back to Snap and build the abstractions you'll need for Project 2, and Part C of Project 1, due next week, is exactly what you just did twice, done once on your own with a country of your choosing.

---

## Contingency: Backup Case 3, Dutch Childcare Benefits Algorithm

**Trigger only if** Case 2's discussion collapses (under ~3 minutes of real talk), *or* you reach Section 6 with real time still on the clock, which is a narrower window than it used to be now that Section 5 exists. Keep it to a **60-90 second reveal**, not a third full case treatment.

- **Input:** a risk-scoring algorithm that used dual nationality and "foreign-sounding names" as literal input variables to flag childcare-benefit fraud
- **Decision logic:** risk score above a threshold → benefits discontinued, full repayment demanded, no hardship clause
- **Outcome:** roughly 26,000 families wrongly accused, disproportionately of Moroccan, Turkish, Surinamese, and Caribbean Dutch background; over 1,600 cases of children removed by youth-protection services; the entire Dutch cabinet resigned in January 2021

**Why it's the strongest debate case in the set:** nationality wasn't a proxy the algorithm stumbled into, it was coded in directly. That pushes past "was this intentional" into "does 'unintentional' even mean anything once you've written someone's nationality into the risk formula," a harder question than either main case poses. Doesn't fit this year's Canada/Global South scoping and isn't recent, but flag it for next year's rotation or as a possible Week 7 lab case if that slot survives.

---

## Quick Reference: Timing Summary

| Time | Segment | Interaction |
|---|---|---|
| 0:00-0:03 | Welcome, agenda, callback to Lecture 13 | (none) |
| 0:03-0:12 | Benjamin's four categories | (none) |
| 0:12-0:14 | Case 1 recap: Clearview / Canada | (none) |
| 0:14-0:19 | Pair discussion (category + stakeholders) | **Pair** |
| 0:19-0:21 | Clicker vote | **Clicker Q1** |
| 0:21-0:26 | Share-out | Cold-call |
| 0:26-0:28 | Case 2 recap: Worldcoin / Kenya | (none) |
| 0:28-0:33 | Pair discussion (category only) | **Pair** |
| 0:33-0:35 | Clicker vote | **Clicker Q2** |
| 0:35-0:40 | Share-out → for/against debate | Whole class |
| 0:40-0:45 | Naming the mechanism | **Pair + share-out** |
| 0:45-0:47 | Buffer / contingency case | (none) |
| 0:47-0:50 | Wrap, point to Project 1C | (none) |

**Constraint check:** 2 clicker questions (target 2-5, at the floor, see Notes) · 3 peer-interaction activities (up from 2, see Notes) · 50 min with 2 min buffer (down from 6, see Notes, this is the real cost of adding Section 5).

---

## Notes for Development

- Two design choices worth flagging as **decisions needed**, both documented here so you can pick without re-deriving the trade-off:
  - **Option A (scripted above): one case, in depth, student's choice.** Pairs pick either Clearview or Worldcoin and spend the full 3 minutes on just that one; the instructor cold-calls from both sides during share-out so the class hears both readings even though no individual student produced both. Lower time cost (5 min total), genuine choice, but any one student only rehearses retrieval once, not twice.
  - **Option B (alternative, not scripted): both cases, lightly.** Instead of a separate Section 5, fold a quick "does this turn on one of the five mechanisms?" line into *both* Case 1's and Case 2's existing pair-discussion prompts, on top of category (and stakeholders, for Case 1). Removes the need for a dedicated segment, which would restore most of the buffer Section 5 currently costs, but each pair gets maybe 30 extra seconds per case instead of a focused 3-minute dive, so the practice is shallower and it's asking each pair to juggle three dimensions instead of two.
  - Option A is what's written into the flow above. Switching to Option B means deleting Section 5, adding one clause to each case's existing prompt, and reclaiming roughly 3-4 minutes of buffer.
- **This also touches how "it's not just feedback loop" gets taught, deliberately.** Section 5 says out loud that a case can implicate more than one mechanism or none cleanly, and that neither Clearview nor Worldcoin has been forced into one of the five. This is a real position, not a hedge, don't let it get cut for time even if Section 5 itself gets trimmed.
- **Use the lab's variable names deliberately.** Write `demand` and `supply` on the board in Section 2's Lecture 12 recap. Students meet those exact identifiers in lab a day later.
- **Open item:** decide whether the pre-read goes out as a standalone document or folds into the existing Friday Oct 9 materials.
- **Don't reintroduce Stakeholders + Effects as new material.** It's from Week 3. Reference it by name during the Case 1 share-out and move on.
- **Misconception to address:** students often read "bias" as "someone was racist on purpose." Default discrimination exists in the category set precisely to break that. The RCMP never wrote a biased rule, it never asked a question. Say that explicitly during Case 1's share-out.
- **Clicker count is still at the minimum (2).** Section 5 deliberately doesn't add a third, there wasn't time to both add a clicker and give the pick-a-case discussion real room. If a third clicker matters more than Section 5's depth, that's Option B territory again.

## Here are additional notes
_on Ruha Benjamin's categorization, I don't expect you to read the book in the next 3 weeks._
I also don't know if the Input, Decision, Outcome part of it needs to be shared with students.
It is just a useful way of framing that I think might help

**Engineered inequity**
This is the most overt category: systems that explicitly encode or reproduce existing racial, gender, or class hierarchies, often carrying forward older discriminatory patterns (redlining, biased underwriting) into new technical form. One thread worth naming for this category: many of the real examples Benjamin and others point to (redlining-derived credit scoring, for instance) involve institutions that were warned the system caused disparate harm and kept using it anyway. That persistence is part of why this category tends to read as the hardest to explain away as accidental, though that specific comparative framing is this guide's own gloss, not a direct quote from Benjamin.
- *Input*: often already skewed, built from historically discriminatory records (arrest data, lending histories) or explicit demographic proxies like zip code.
- *Decision logic*: the rule visibly weights those proxies or identity categories, so the mechanism of harm is traceable.
- *Outcome*: disparities track and often amplify existing hierarchies. Because the logic is legible, this is the category most susceptible to being caught and challenged, if anyone chooses to look.

**Default discrimination**
Here the harm isn't intentional. It emerges from designing for an unmarked "default" user (typically white, male, able-bodied) without considering how that choice excludes everyone else. This can be harder to catch than engineered inequity precisely because no one is straightforwardly accountable for it: the people building it can sincerely believe they're neutral, since indifference to context, not malice, is doing the work. (This comparative framing is this guide's own reading of Benjamin's broader argument, not a direct claim she makes in these terms.)
- *Input*: reflects whoever was already dominant in the data or the design process; the exclusion is an absence, not a flag.
- *Decision logic*: built around "the average case" using whatever data was convenient, so it's context blind rather than identity aware.
- *Outcome*: uneven performance or access for anyone outside the default. The system just quietly works worse for them, with no single line of code anyone can point to as the cause.

**Coded exposure**
This category captures a double bind: the same group can be simultaneously under recognized and over monitored by technology. Facial recognition that fails to detect darker skin is invisible in a technical sense, but the communities that failure comes from are often hyper-visible to surveillance and policing systems built on that same technology. Benjamin's point is that visibility itself isn't inherently protective. Being seen by an extractive system can do as much harm as not being seen by a beneficial one.
- *Input*: underrepresents certain groups in training data, even as those same groups disproportionately generate the "input" surveillance systems feed on (more arrests, more contact, more records, because they're already over-policed).
- *Decision logic*: performs worse technically on underrepresented input, while separate deployment logic directs more scrutiny toward the same population.
- *Outcome*: harm lands twice: individual technical failure (misidentification, denial of service) plus population-level overexposure (more surveillance, more law-enforcement contact) for the very same group.

**Technological benevolence**
This is the "fix" that isn't one: a product or reform explicitly marketed as solving bias that ends up reproducing it, usually because fairness was defined too narrowly (optimizing one statistical metric while ignoring the structural context that produced the input data in the first place). Benjamin treats this as especially hard to challenge because it wears the language of progress, so critique reads as attacking a solution rather than exposing a problem.
- *Input*: frequently the same historically biased data the "reform" was meant to move away from, since the fix touches the model, not data collection.
- *Decision logic*: explicitly tuned to satisfy a narrow fairness criterion, which can be technically true while the outcome stays skewed.
- *Outcome*: disparity persists but is harder to contest, because it now carries institutional legitimacy as an anti-bias fix.

One thread worth naming across all four: the input/decision logic/outcome breakdown shows that where the harm sits shifts by category. Engineered inequity and default discrimination locate it in the decision logic itself (explicit versus careless), coded exposure splits it across input and downstream social deployment, and technological benevolence hides it by leaving input untouched while polishing the logic layer. That's useful if you want a follow-up clicker question that tests whether students can locate which layer the bias lives in, rather than just naming the category.
