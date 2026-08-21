# Using Algorithms (Surge Pricing / TikTok), Lecture 12

**Week:** 5 (Wednesday, Oct 7)
**Length:** 50 min
**Unit:** Digital Adolescence

## Learning Goals

By the end of this lecture, students should be able to:

- Describe how sorting and ranking algorithms let companies determine what is "popular," and how that determination triggers a decision.
- Identify what data a company needs as input for such an algorithm, and explain the consequences of choosing one proxy measure over another.
- Explain what a feedback loop is and trace how an algorithm's own output becomes its next input.
- Give examples of unintended consequences of these algorithms and connect them to the no-free-lunch tradeoff idea from Monday.
- Evaluate an algorithmic design choice from multiple perspectives, e.g., company goals vs. user and social impact.

## Big Idea

Monday asked how to *evaluate* an algorithm that already exists.
Friday will ask how to *create* one.
Today is the question in between: what actually happens when someone takes data and a decision comes out the other end?
We will use surge pricing, which is a simple example that is similar (in structure) to the recommender systems that are in our phone apps.
The big idea is that algorithms may seem simple but they have far and wide implications.

**Connection from last class:**
Monday (Lecture 11, Evaluating Algorithms) established space/time tradeoffs, abstraction, and the idea that different algorithms suit different problems.
Week 3's Data Privacy lectures established what gets collected about you: location, dwell time, clicks.
Today joins those two halves.

**Where we're going next:**
Friday (Lecture 13) focuses on the creation of algorithms, we will use the decision tree technique to help us with the classification task.
Later next week, we will have a dedicated lecture for algorithmic bias in the wild. Today's neighbourhood feedback loop (Section 3) is the mechanism preview for that lecture, not the full treatment, keep that boundary in mind while teaching it.

## References

- Reporting on surge pricing during emergencies, evacuations, and the 2026 World Cup (an In the News slide with links for students to peruse, ungraded, just for the keeners)
  - https://www.cbc.ca/news/canada/british-columbia/ride-hailing-vancouver-world-cup-9.7230941 , CBC, June 2026. 
  - https://time.com/3633469/uber-surge-pricing/ (one of the earlier articles on this phenomenon). This is also the source for Section 5's real emergency-cap reveal: the "fourth-highest price in the preceding two months" detail and the price-gouging-law count both come from this piece.
  - FYI, not required reading, but good if you want a current hook: independent analysis (Obi, a rideshare comparison service) tracked over 15,000 fares across all 8 North American World Cup host cities this summer and found Uber fares averaged 47 to 62 percent above baseline on match days, climbing to 77 percent for the July 19 final, with Lyft consistently surging less (28 to 43 percent). Toronto's BMO Field and Vancouver both saw the same pattern this summer, per CBC and local coverage. This is real, dollar-backed, and something a lot of students plausibly lived through a few weeks before this course started, worth considering as a swap-in or addition to the cold open's concert scenario, entirely optional, not done here.
- TikTok recommendation-system explainers
  - https://medium.com/beyond-localhost/how-tiktok-recommendation-algorithm-works-complete-guide-0c02479be44f , easy read, good for a quick guess-the-signals warm-up.
  - TikTok's own official explanation of the For You feed and its stated diversification safeguards, worth pulling up directly for Section 4's one-line counter-nuance: https://newsroom.tiktok.com/en-us/how-tiktok-recommends-videos-for-you
- On the neighbourhood feedback loop being real, not just illustrative. Caliskan and Pandey (George Washington University) analyzed over 100 million Chicago ride-hailing trips and found systematically higher fares, and by extension worse service, in lower-income and non-white neighbourhoods, tied to demand-forecasting algorithms. Accessible writeup: https://venturebeat.com/ai/researchers-find-racial-discrimination-in-dynamic-pricing-algorithms-used-by-uber-lyft-and-others/ . **Use sparingly in Section 3, one line and a citation. This is not the bias lecture.**

---

## Lecture Flow

### 0. Pre-Class Preparation

None required.

This lecture is self-contained and assumes only Monday's Lecture 11 and the Week 3 privacy content.
_Or if we want we can have them read 1 or 2 articles like the ones I have above._

### 1. Cold Open / Recap Bridge + Hook, ~7 min

**0:00-1:30, Recap bridge.** Three-week arc in 90 seconds: what gets collected about you (Week 3), how to evaluate an algorithm that exists (Monday), what happens when data goes in and a decision comes out (today).
This is narrative work, not content work, keep it tight.

**1:30-7:00, Hook.** The concert scenario: you leave at 11pm, the ride that was 12 dollars, tonights its 31. Nobody typed that number by hand.

**CLICKER Q1, What determines whether surge pricing kicks in?**

- A) The time of day
- B) How many drivers happen to be nearby
- C) The ratio between ride requests and available drivers (correct)
- D) It's basically random

*Facilitation: C is the target, but don't shut down B, it's half-right and useful. Use the split to launch the mechanism: "some of you said drivers, some said requests, turns out it's both, compared to each other."*

**Point:** A price is a decision, and something computed it from inputs. Establishes that the black box has a knowable inside.

### 2. Mechanism Walkthrough, the Spine Example, ~11 min

**7:00-18:00.** Ask students what they'd want to know if they were setting the price by hand. Take 2-3 answers out loud and write **demand** and **supply** on the board, use those exact words, they are the lab's variable names.

Bridge back to sorting explicitly: we're taking unranked raw data and turning it into an ordered decision. Uber's version is a simple threshold; TikTok's stretches the same idea across thousands of videos.

Work the numbers live, base fare $10, 50 requests, 10 drivers:

```
demand / supply = 50 / 10 = 5.0

if demand / supply > 3:      multiplier = 2.5
elif demand / supply > 2:    multiplier = 1.75
elif demand / supply > 1:    multiplier = 1.25
else:                        multiplier = 1.0

final_price = base_fare x multiplier
```

Ratio 5.0, first bracket, 2.5x, **$25**.

**Point:** The algorithm doesn't "know" fairness or "understand" a concert crowd. It contains three numbers, 3, 2, 1, and a person chose them. That is exactly what students become in this week's lab.

**Say out loud that this table is a teaching model, not Uber's real formula.** The real thing runs on proprietary machine learning, evaluated separately for small hyperlocal zones (a few blocks each) rather than one citywide ratio, and factors in historical patterns and signals like weather or event schedules on top of live supply and demand. Worth naming, it's also the answer to "why did my friend a block away see a different price than I did."

**One more distinction worth a beat before moving on:** everything above is *aggregate* pricing, the same price for everyone in the same zone at the same moment, driven by a ratio, not by who's asking. That's a different thing from *personalized* pricing, where two people can be charged two different prices for the identical product based on their own data. Both get called "algorithmic pricing" in the press, and the algorithmic-pricing reading on this week's list is mostly about the personalized kind (grocery loyalty pricing, the Instacart story), not the surge kind. Worth a sentence so students don't walk into that reading expecting it to be about today's mechanism.

### 3. What Counts as "Demand," and the Loop That Follows, ~12 min

**18:00-30:00.** "Demand" is a *proxy*, not an objective quantity. Someone decides what to measure. Take 2-3 student suggestions (app opens, completed requests, GPS density, historical averages for that time slot).

**Quick discussion, not a clicker, ~2-3 min:** Pose it directly: if the algorithm decides where to send drivers based on "which neighbourhoods had the most completed rides last year," what's the biggest risk? Take a few answers, then land the point yourself if nobody gets there: whatever proxy gets chosen, "completed rides last year" isn't measuring demand, it's measuring the algorithm's own past decisions about where it already sent drivers. Feed an algorithm's own output back in as next year's input, and you're not detecting demand anymore, you're detecting yourself.

**Point:** choosing the input is a design decision with consequences, made before a single line of decision logic runs.

**DO:** Put the loop on a slide or a timed animation.

```
   [Algorithm sends fewer drivers to Neighbourhood X]
                |
   [Wait times grow in Neighbourhood X]
                |
   [Fewer people even bother requesting a ride there]
                |
   [Algorithm now has data confirming "low demand" in X]
                |
        (back to the top, even fewer drivers)
```

The line that matters: *it's not broken, it's working exactly as designed.* Nobody wrote code that says "ignore this neighbourhood." The loop wrote it, one cycle at a time.

**CLICKER Q2, Six months after a neighbourhood gets fewer drivers, what does the algorithm "see"?**

- A) Demand rising, riders refresh the app repeatedly hoping for a match during long waits, and those extra opens register as new requests
- B) Demand still low, people who keep getting no match stop opening the app at all, so the drop in requests reads as the neighbourhood just not wanting rides (correct)
- C) No change at all, the model only updates its read on a neighbourhood when a driver is actually nearby to report conditions, and none are
- D) Demand unreadable, so few trips are completing that there's not enough recent data for the model to predict anything with confidence

**Second loop, fast, ~1 min:** a "hot" pickup zone pulls drivers away from ordinary areas, creating artificial scarcity elsewhere, creating a new "hot zone."

**Point:** an algorithm's output becomes tomorrow's input. That's a property of the loop itself, true regardless of who ends up on which side of it.

**This isn't hypothetical.** Real research on ride-hailing pricing has found this exact pattern in live data (see References). Today's point stops at the loop itself; what it means for who's affected, and why that matters, is the whole subject of the Algorithmic Bias lecture coming up. Don't let this section become that lecture early, one sentence and move on.

### 4. Transfer: the Same Shape, Different App, ~6 min

**30:00-36:00.** TikTok isn't ranking rides, it's ranking videos. Let students guess the signals (watch time, rewatches, likes, shares, comments, pause duration, completion rate) and land on **predicted engagement**. Completion rate specifically is worth naming as the single most heavily weighted signal across independent sources; if only one signal survives the guessing game, that's the one.

Small test audience, good engagement, wider distribution, more data, more confidence, wider still. *Hot gets hotter, same loop, new domain.*

Unintended consequence: the more you engage with one *kind* of content, the less of everything else you see, a filter bubble. TikTok's own public position is that it has safeguards against exactly this (it says it avoids back-to-back videos from the same creator or sound, and deliberately mixes in content just outside your usual pattern); independent reporting, the Wall Street Journal's bot investigation is the well-known one, suggests the narrowing still shows up in practice. One sentence either way is enough, this isn't the bias lecture either.

Tie back to Monday explicitly: no free lunch. An algorithm that is very good at giving you more of what you already like is, by the same design, bad at giving you something different. Personalization and diversity of exposure are a tradeoff, not a bug.

**Point:** the structure transfers. Students should be able to see the shape, not just the two examples.

### 5. Application / Activity, Multi-Perspective Evaluation, ~9 min

**36:00-45:00.** Name the unintended consequence *before* the scenario: during floods, evacuations, and transit shutdowns, this exact threshold logic has priced people out of getting home when they most needed to.

Set the scenario: "You're on the product team. Someone proposes capping the surge multiplier at 1.5x during declared emergencies."

**THINK-PAIR-SHARE (2 min discuss, then cold-call 2-3 pairs)**

Turn to the person next to you and come up with:

1. One reason the company might resist this cap.
2. One reason they should do it anyway.

**Debrief:** Write both columns on the board. Target content, *for the company:* more revenue, and high prices genuinely pull more drivers onto the road exactly when they're needed most. *Against:* people evacuating shouldn't be priced by desperation; reputational and regulatory risk (at least 34 US states plus DC have price-gouging laws that make this a legal question, not just a PR one; Canada currently has no federal equivalent, worth a sentence given where we're teaching this).

**The reveal, after the debate, not before, ~1-2 min:** this isn't hypothetical. Uber already caps surge during declared US emergencies, at the area's fourth-highest price over the preceding two months, not a round number like 1.5x, and donates its commission to the Red Cross during those windows. Ask: why a formula tied to the area's own recent history instead of one clean number for every city? (Answer to draw out: a flat 1.5x might be way too low in a normally expensive market and way too high in a cheap one; pegging the cap to each area's own recent pricing keeps it locally calibrated the same way the surge algorithm itself is.) **Do not let this replace the earlier tension.** The point isn't that Uber solved it, it's that a real company weighed the same two columns the class just wrote and landed somewhere in between, not on either pole.

### 6. Wrap-Up, ~5 min

**45:00-50:00.**

- An algorithm is a decision, and someone picked the numbers inside it.
- The choice of what data counts as the input is a design decision with consequences before any logic runs.
- Data comes in, a decision comes out, that decision changes the data that comes in next. **Hold onto that shape.** It's the same shape whether the domain is rides, videos, or something else entirely.

**Bridge to next class:** Friday we build the *other* kind of decision-maker, a decision tree. Next week the neighbourhood feedback loop from today gets its own full lecture: today was the mechanism, that lecture is the impact.

**Lab preview:** In lab you build exactly this calculator, demand, supply, an if/else ladder, and then you change the 3, the 2, and the 1, and watch what happens to different simulated riders. You stop running someone else's decision and start making it.

---

## Notes for Development

- **Bias is a hook here, not a treatment, this is stronger now, not weaker.** The merged Section 3 explicitly says out loud, in the lecture body, not just in these dev notes, that the deeper treatment is coming in the Algorithmic Bias lecture. The one citation added to References is meant to be used as a single line ("this isn't hypothetical, see the reading list") and then moved past, not opened up into a discussion of who is affected and why. If Section 3 is running long, the discussion prompt at the top is the thing to shorten, not the citation line, cutting the citation is what would make this feel less grounded, not what would make it faster.
- **Use the lab's variable names deliberately.** Write `demand` and `supply` on the board in Section 2. Students meet those exact identifiers in lab a day later.
- **Misconception to address:** students commonly believe surge pricing is either arbitrary/random (option D) or purely time-based (option A). Q1 exists to surface that before the mechanism, not after.
- **Misconception to address:** "the algorithm is biased" gets heard as "someone coded a biased rule." The whole point of Section 3's loop is that no such rule exists. Say the words *"it's working exactly as designed"* out loud.
- **Worth double-checking, not changed here:** Section 4 recycles "no free lunch" for the personalization-versus-diversity tradeoff. The actual No Free Lunch theorem is a narrower, specific claim about optimization algorithms averaged across all possible problems, not a general "you can't have both" intuition. If Monday's Lecture 11 introduced the term in that stricter sense, this colloquial reuse could blur rather than reinforce the connection. Worth checking Lecture 11's actual framing before Wednesday; not altered here since that lecture wasn't available to check against.
- **Do not lose:** the closing "hold onto that shape" line. It is a deliberate seed for the Digital Adolescence Consolidation lecture (Week 10 Friday) and for Lecture 17 (recommender systems).
