# Lab 3 (Week 5): How Exposed Are You?

### Somebody picked those _numbers._ Today it's you.

**Week 5 · 50 minutes · Wednesday/Thursday**

---

## Learning Goals

By the end of today, you should be able to:

- Read someone else's Snap script and explain, in your own words, what a chunk of it does
- Explain how a weighted scoring algorithm turns a pile of answers into a single number
- Change the weights in a scoring algorithm and predict how that changes the result
- Say what a scoring algorithm like this one *fails* to measure, and why that matters

---

## This Week

On Wednesday we asked what data an algorithm needs, and what changes when somebody picks one input over another. Today we point that question at you.

You're going to run a scoring algorithm on your own digital life and get a number out of it. Then you're going to look at how that number was calculated, argue as a class about which factors should count for more, change the weights to match what the class decided, and run it again.

Your answers won't change between the two rounds. Only the weights will. Watch what happens to your number anyway.

**Counts toward:** Lab completion, and this is **Project 1 Part A** — the work you do here feeds the write-up later. Nothing is handed in today.

---

## Before Lab

- **Bring your laptop.**
- **Fill out the Digital Exposure Answer Sheet** and bring it with you. You'll type these same answers into Snap twice today — having them written down first means Round 2 is a copy of Round 1, not a second guess.
- **Files you'll need:** your TA hands out the link to the **Exposure App**
at the beginning of lab. You are **not** building this from scratch — it uses blocks you haven't met yet, and that's fine. 
Today you're reading someone else's code, not writing your own.
---

## Ground Rules for Today

Some of today's questions touch on genuinely personal things — photos of you online

**Here's the rule for the whole lab: you share the number, never the answers.**

When you compare with a partner later, you're comparing your Exposure Index and *which factors moved it most*. "My photo content factor was a big driver" is a complete answer. You never have to say what the actual content was, and nobody should ask.

Answer honestly on your own screen — the number is only useful if you do — and share only what you want to.
Your answer sheet is exactly as private as your screen — nobody collects it, nobody sees it but you. Same rule as everything else today: the number gets shared, nothing else does.
---

## Working Together

You'll work **on your own machine** the whole time. There's a partner comparison near the end, and one class-wide vote in the middle, but the calculator is yours and nobody else needs to see your screen.

---

## How Today Runs

| Part               | What you're doing                                  | About how long |
|--------------------|----------------------------------------------------|----------------|
| Setup              | Getting the link open                              | 5 min          |
| Round 1            | Running it with neutral weights                    | 8 min          |
| Annotate           | Working out how it actually calculates             | 12 min         |
| Clicker + vote     | One question, then the class picks the weights     | 8 min          |
| Round 2            | Same answers, new weights                          | 7 min          |
| Compare + checkoff | Talking it through with a partner, TA comes to you | 7 min          |
| Think it over      | Writing a few things down                          | 3 min          |

*These are estimates, not a schedule.*

---

## Setup
0. Have your answer sheet out and next to your keyboard. If you didn't get to it beforehand, take two minutes now — just make sure whatever you write is what you'll type both times.
1. Open the link your TA shares — it loads straight into Snap, nothing to download. Don't use Save or Save As on this project at any point during lab — if you save your own copy, you'll stop getting the Round 2 update when it goes live.
2. Click the green flag once to check it runs. **Don't enter anything yet.**
3. The weights for each factor live inside a block called factorTier — you'll see it get called throughout the script, 
but don't open it yet. Right now every factor is already set to Medium, because nobody's decided what matters more than what.
That block stays closed until we get to it together, as a class — that's on purpose, not a restriction we forgot to lift.
---

## Round 1: Your Number, Unweighted

Every factor currently counts the same. This is the "before" number.

4. Click the green flag and type in the answers from your sheet, in order. Don't reconsider or improve on anything as you go — the sheet is the sheet.
5. **Write down your Exposure Index.** Paper, notes app, wherever — you'll need it in about twenty-five minutes.

Don't overthink your answers. First instinct is fine.

> ### What's an "Exposure Index"?
>
> It's a made-up number. It doesn't mean anything on its own — there's no scale, no safe range, no comparison to a national average, because none of that exists.
>
> What it *is* good for is comparison: your Round 1 number against your Round 2 number, and the shape of your answers against someone else's. Hold onto the fact that it's invented. It matters later.

### If You Finish Early

Read ahead to the annotation task and pick which aggregate factor you want to take.

---

## 6. Annotate the Script

Now look at how that number got built.

You're not going to annotate the whole thing — there are six factors and you have twelve minutes. Take three representative pieces.

> ### Annotating code
>
> **Annotating** means explaining what a piece of code does in ordinary language — not translating it block by block, but saying what it's *for*. This matters more than usual for the weighted-sum step: you genuinely can't translate it block by block, because part of it is intentionally hidden from you. You can still say what it's for.
>
> You'll be graded on this skill in Project 2, on a program you wrote yourself. Today is the low-stakes version: someone else's code, no marks attached.

**Annotate these three properly — one sentence each, in your own words:**

- **One aggregate factor of your choice** (`numPlatforms`, `oldestAccountYears`, or `publicProfiles`). What is it measuring, and why would more of it mean more exposure?
- **The photos branch.** Trace both levels: what does the first question decide, what does the second one add, and why does "shows your face" cost more than "photos exist"?
- **The final weighted-sum step.** Each factor's contribution comes from a call like `tierWeight("numPlatforms")` or `tierBonus("photos", "deep")` — not a number sitting in the script. What does that call actually determine, and what does it deliberately not show you?
**NOTE:** Light is 1, Medium is 3, Heavy is 5
**Skim the rest** — content type, the remaining aggregate factors. You don't need to write anything for these, but you should be able to say in one sentence what each is trying to capture.

Your answer sheet already has the branching arrows for the photos question — hold it next to the actual blocks and check: does the code branch the same way you branched on paper?
### If You Finish Early

Annotate a fourth factor, or find the place in the script where a branch could produce the same score two different ways.

---

## 7. Clicker Question

**One question, about two minutes.** On your own.

Look at the photos branch in your script.

**🔵 Clicker — A student answers "yes, there are public photos of me" and "no, none show my face." What gets added to their Exposure Index?**

- A) tierBonus("photos", "deep")
- B) tierBonus("photos", "shallow") ✅
- C) Both, added together
- D) Nothing — the second answer was "no"

---

## 8. The Class Vote

Now the part where you get to be the person who picks the numbers.

- Your TA will put all sox factors on screen.
- **Show of hands — vote for the two or three that worry you most**, exposure-wise.
- Your TA tallies the votes live and sorts the factors into three tiers:

| Vote rank        | Tier assigned | Weight |
|------------------|---------------|--------|
| Top 2 factors    | **Heavy**     | 5      |
| Middle 2 factors | **Medium**    | 3      |
| Bottom 2 factors | **Light**     | 1      |

Your TA updates the `factorTier` block on their end while the vote is being tallied — 
you don't touch anything on your screen for this part. When you hear "refresh now," reload your page 
and the new weights will be there
---

## Round 2: Same Answers, New Weights
9. When your TA says the update is live, refresh your browser tab.
10. Click the green flag and run the calculator again — pull out your answer sheet and type in exactly what's written, same order, no re-deciding.
11. **Write down your new Exposure Index.**

Nothing about you changed in the last half hour. The number probably did.

---

## 12. Compare With a Partner

- Find a partner. **Remember the ground rule: compare the number and which factors moved it, not your raw answers.**
- Talk through:
    - How much did your Exposure Index change between Round 1 and Round 2?
    - Which factor's weight change moved your score the most?
    - Did the class's weighting match your own instinct? Where did you disagree?

> #### Deliverables
>
> Your TA will come round during the comparison — you don't need to queue. When they reach you, between the two of you:
>
> 1. **Show them your two numbers** — Round 1 and Round 2 — and say which factor moved yours most.
> 2. **Show them your three annotations** and talk through the photos branch in your own words.
> 3. **Tell them one thing this calculator should have asked about but didn't**, and why it belongs.

### If You Finish Early
Your real numbers are already recorded — you're clear to open `factorTier` and play from here.
Set every tier to Heavy and run it once more. Then set every tier to Light. How far apart are those two numbers, for the same person, on the same day?

---

## Think It Over

**Nobody collects this and no TA checks it — but write your answers down anyway.** These are the questions this lab exists to produce, and they come back on the quiz and in Project 1 Part A. Two or three minutes, in your notebook.

- Your answers didn't change between rounds, but your number did. In one sentence: what does that tell you about what the Exposure Index actually measures?
- Which factor did *you* think should be Heavy? Did the class agree? What would you say to convince them?
- **No right answer:** this calculator doesn't ask about everything that could count as exposure. Name one thing it should have asked but didn't — and explain why it belongs.

---

## You're Done!

That's it. You ran an algorithm on yourself, took it apart, changed the numbers behind it, and watched your own result move.

Before you go, make sure your TA has checked off:

- [ ] Your two Exposure Index numbers and your annotations, discussed with your partner

And for yourself: the *Think It Over* questions, written somewhere you'll find them again — especially the last one.

Hang onto that "what's missing" answer. It's exactly the kind of gap we come back to when we ask where algorithms get their data from, and who decides what counts.

**Next up:** Friday's lecture builds the other kind of decision-maker — decision trees. And next week we come back to the neighbourhood problem from Wednesday's lecture and give it a full hour.

---

## Still Stuck?

- **"The script won't run."** Make sure you clicked the link your TA shared and let it fully load. If the page still looks blank, try reloading the link.
- **"The link isn't loading."** Check your wifi first, then ask your TA to re-send it.
- **"My Round 2 number is the same as Round 1."** "You probably didn't refresh after your TA said the update was live — reload the page and try again."
- **"I don't want to answer one of these questions."** Answer it however you like — the number is for you and nobody else sees it. You can still do every other part of the lab.
- "I forgot to fill out my answer sheet." Take a couple of minutes now, before you run Round 1 — just make sure you actually write it down somewhere so Round 2 matches. Don't try to remember it from memory later; that's the thing we're trying to avoid.
- **Still stuck?** Flag your TA.
---
## Digital Exposure Answer Sheet
### Fill this out before lab. Bring it with you. It's yours — nobody collects it.

You'll type these exact answers into Snap twice today, so write down what's
true, not what you think sounds better the second time.

1. How many platforms/apps do you actively use? (Enter a numeric value, e.g. 5) _______

2. How many years ago did you create your first account? (Enter a numeric value, e.g. 5) _______

3. How many of your profiles are public rather than private?  (Enter a numeric value, e.g. 5) _______

4. For any of your apps, how many of these personal identifying info (PII) do you show publicly — name, birthdate, location,
   phone number? (Enter the number of PII you share i.e., 0,1,2,3,4,) _______

5. Are there public photos of you online? (yes/no) _______
   → If yes: Do any clearly show your face? (yes/no) _______

6. Is your most-used platform mostly text/opinions, or mostly photos/
   video of you? (Enter TO for text/opinions or PV for photos/videos) _______
   → If text/opinions: Do you post opinions or arguments publicly more than once a month? (yes/no) (yes/no) _______
   → If photos/video: Do you appear on camera — face or voice?
     (yes/no) _______

---
<!-- ============================================================
     NOT STUDENT-FACING — delete before distributing.
     ============================================================ -->

## Notes for Development — REMOVE BEFORE DISTRIBUTING

**Learning outcomes covered**

From `100 Learning Outcomes UPDATED` → Using Algorithm Specifics ("Happens in Lab for that week"):

- Modify the weighting or thresholds in a program and explain how those changes affect the outcome for different simulated scenarios → the two-round structure, which *is* the LO
- Plus Project 1 Part A: trace your own online presence and calculate a personal exposure index
- Plus first rehearsal of **code annotation**, graded later in Project 2 Stage 1

**What students walk in knowing**

Lectures 8 (Snap 2: If/Else), 10 (Snap 3: other loops), 11 (Evaluating Algorithms), 12 (Using Algorithms — surge pricing, *Wednesday of this week*). They have variables, `repeat`, `for`, if/else, booleans.

The script uses nested branching beyond what they've built themselves — hence pre-built. This is intentional and should be said out loud: reading code you couldn't yet write is a real skill.

**TA prep required**

- Announce the answer-sheet prep in the class before this lab (or post it wherever pre-lab tasks normally go) — it only works as time-saved if most students actually show up with it filled out.
- Have a few blank answer sheets on hand for stragglers who forgot — better than letting them wing it from memory between rounds.
- Run the calculator yourself end to end before lab
- **Rehearse editing the tier variables live in front of the room** — this is the one moment where a fumble costs real time and visibly undermines the "the weights are easy to change" point
- Have the tier conversion table ready to project
- **Say the ground rules out loud at the top of lab**, before anyone enters anything. It's also a live demonstration of the consent principles the course teaches — worth naming as such. 
- Test the save → refresh flow once beforehand, ideally on a second device, so you're confident it propagates before relying on it live. 
- When editing between rounds, use File → Save, not Save As — Save As creates a new project under a new link, which breaks the one everyone already has open. 
- Consider sharing the link in #present: mode (Snap's presentation view) — it doesn't lock the blocks, but it keeps the editing interface out of sight by default, which quietly discourages poking around factorTier early.

**Where this is likely to break**
- Students who skip the prep. Expect a handful to show up without it. The Setup step and Still Stuck entry both cover the fallback (fill it out live, first few minutes), but if more than a couple of students need this, it'll eat into Round 1's window — worth having TAs flag it early rather than let it surface at 13:00 when annotation is supposed to start.
- **Timing: annotation.** Twelve minutes for three chunks is tight, and students will try to annotate all six. Say "three, not six" out loud at the start of the block.
- **The vote can stall** if students want to debate individual factors. It's a fast ranking pass, not a discussion — show of hands or clicker, tally, move.
- **Round 2 with different answers.** Some students will re-answer honestly-but-differently the second time, which breaks the whole comparison. Step 14 says "exactly the same answers"; TAs should reinforce it verbally.
- **Checkoff queue at the end.** Deliverables land at roughly 0:47 for everyone at once, and there are three items. Mitigation: check off *pairs* together (as written), and start circulating during the partner comparison rather than waiting for hands.
- **A student who genuinely doesn't want to engage** with the photos questions. The Still Stuck entry covers it, but TAs should know they can say "answer anything, the number is yours" without making it a negotiation. 
- Network dependency. This design trades "a student might edit their own file" for "the whole room depends on wifi and the Snap server being responsive at the same moment." If your classroom connectivity is unreliable, have a fallback — export the updated project as an XML file to a shared drive so students can reload manually if the live refresh stalls. 
- A student saves out of habit. If someone's Round 2 number doesn't move at all, the first thing to check is whether they hit Save or Save As at some point — that silently detaches them from the shared copy.

**Clicker answer key**

B — `tierBonus("photos", "shallow")`. The outer branch fired (photos exist), the inner one didn't (no face), so the shallow value is added.

Distractors: A targets students who don't notice the nesting. C targets students who think both branches accumulate. D targets students who think a "no" anywhere means nothing is added — the most instructive wrong answer, because it's really a question about which `if` the second answer belongs to.

**Think It Over — assessment link**

- Q1 (what the index actually measures) → Quiz 3; also the conceptual core of Project 1 Part A's write-up
- Q2 (which factor should be Heavy) → rehearses the multi-perspective evaluation LO from Lecture 12
- Q3 (what's missing) → open. **This is the most valuable question in the lab.** Expect: tagged photos posted by others, search-engine indexing, deleted-but-cached content, group chats and DMs, biometric data, data brokers. It sets up Data Mining, Digital Traces (Week 13), and the AI unit.

**Open questions**

- ✅ **Resolved: the class vote is a show of hands**, not clickers. Using clickers would give a cleaner tally but would mean two clicker events in one lab, against the one-per-lab convention. Step 10 now says show of hands explicitly.
- The reference tables (tier values, six factors) from the original docx aren't reproduced here — decide whether they're a student-facing appendix or a TA-only sheet.

**Assets to produce**

- `assets/lab3/digital_exposure_calculator` — needs to live under a TA/course Snap account so the link is stable and reusable across sections; consider a short link or QR code for fast distribution at the top of lab.
- `assets/lab3/tier-reference.pdf` — tier values and the six factors, for projecting during the vote
- `assets/lab3/photos-branch.png` — the photos branch as a Snap screenshot, for the clicker question
