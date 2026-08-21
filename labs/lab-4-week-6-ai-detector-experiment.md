# Lab 4 (Week 6): Does It Actually Work?

### Running your dataset against the tools that claim to know

**Week 6 · 50 minutes · Wednesday/Thursday**

---

## Learning Goals

By the end of today, you should be able to:

- Run a documented image dataset through a detection tool and record results in a form your group can compare across tools
- Tell the difference between a false positive and a false negative, and say who bears the cost of each
- Say something specific about *where* a tool failed, not just how often
- Report your individual contribution clearly enough in writing that someone who wasn't watching can tell what you did

---

## This Week

You've spent weeks building an image dataset. Today you start finding out what the tools do with it.

The claim these products make is a strong one: hand us an image and we'll tell you whether a machine made it. Today you start testing that claim with images your group collected yourselves. **You don't have to finish today.** You just have to make a real, visible start, and know what you're doing next.

**Counts toward:** Lab completion, and this is **Project 1 Part B**. Progress today is recorded through your ongoing results table and an individual postcard from each of you.

---

## Before Lab

- [ ] **Your dataset is finished.** It was due at the end of last week.
- [ ] **Your tools are chosen, and you have working access to each one.** Accounts made, free-tier limits checked, logins tested. Your group's tool count follows the rule from the project guide: one tool per person, three minimum: a pair tests three (split two-and-one), a trio tests three, a group of four tests four.
- [ ] **Bring laptops**, ideally more than one per group, so you can run tools in parallel.
- [ ] Have your dataset somewhere the whole group can reach it.

> ### If you arrive without tool access
>
> You'll spend the lab making accounts instead of testing images, and you'll be finishing Part B on your own time. Sort it out beforehand.

---

## Working Together

Today is **project group work** throughout. Each person tests their assigned tool against the shared dataset. This is the one part of the project where dividing the work by tool, rather than by task, is straightforwardly the right move.

---

## How Today Runs

| Part | What you're doing | About how long |
|---|---|---|
| Setup | Confirm access, finalize who's testing which tool, take a postcard | 5 min |
| Run the Experiment | Your dataset through your assigned tool(s), ongoing, no finish line | 35 min |
| Clicker question | One question | 4 min |
| Wrap | Postcards finished and handed in, deep-dive tool named | 6 min |

*These are estimates, not a schedule. Nobody is watching a clock for a single "checkoff moment" today. See below.*

---

## Setup

1. Get your dataset open where everyone can see it.
2. Confirm every tool loads and you can actually submit something. Use a throwaway test image for this, **not** one from your real dataset, especially if your tool has a tight daily scan limit.
3. Confirm who's testing which tool, following your group's assignment from the project guide.
4. Agree on how you're recording results *before* anyone starts: one shared table, one row per image, one column per tool. If everyone records differently you'll spend Week 7 reconciling it.
5. Each person takes a postcard. Fill in your name and group number now. You'll fill in the rest as you go.

---

## Run the Experiment

> ### You're starting this today, not finishing it
>
> Most groups won't get through their whole dataset in 35 minutes, and that's fine. What matters is that you make a real start, your recording is honest and specific, and you know your plan for the rest.
>
> Your TAs will be circulating throughout this block, not arriving at one fixed minute for a formal checkoff. If a TA stops by your table, that's the check happening. There's nothing separate to prepare for.

6. Run images from your dataset through your assigned tool.
7. For each image, record: what the tool said, how confident it claimed to be (if it gives a number), and **what the image actually was**.
8. Flag anything strange as you go: a tool that refuses a file, a confidence score that doesn't match the verdict, an image that breaks it entirely. Write it down in the moment. You will not remember it later.
9. On your postcard, jot one line: what you tested today, and what's next for you specifically.

> ### Record what it said, not whether it was right
>
> Log the raw verdict. Work out correctness afterwards, from the table.
>
> If you record "correct / incorrect" as you go, you'll lose the information about *which way* it was wrong, and that direction is most of what makes your results interesting.

### If You Finish Your Assigned Images Early

Run a few images through a second time to see whether the tool gives the same answer twice, worth recording either way. Or help a groupmate who's still working through their share.

---

## Clicker Question

**One question, about four minutes.** On your own.

A group tests a detector on **100 items: 90 human-made, 10 AI-generated.** The tool labels everything "human." It is right 90 times out of 100.

**🔵 Clicker: What's the most useful thing to say about this tool?**

- A) It's 90% accurate, which is reasonably good
- B) It's 90% accurate, but it caught none of the AI content: the accuracy comes entirely from the dataset being mostly human ✅
- C) It's broken and the results should be discarded
- D) There's not enough information to say anything

---

## Wrap

10. Finish your postcard: what you did today, what's next for you, and (**one card per group only**) which tool you're going to investigate in depth for the write-up, and why. Choose the one that behaved most interestingly, not the one that scored best.
11. Hand your postcard to a TA before you leave.

> #### What the postcard is for
>
> It's a dated, individual record that you were here and did specific work: the same thing an in-person contribution round would give us, without needing a TA to run a formal round with a room full of groups. It isn't a monitoring tool, and nobody is reading it looking for something to fix.
>
> Something off in your group? Talk to your TA this week. See the project guide for what happens next.

---

## Think It Over

**Nobody collects this and no TA checks it, but write your answers down anyway.** These feed straight into your Part B write-up and come back on the final. Two or three minutes, in your notebook.

- Look at your table so far. When your tool was wrong, was it wrong in a consistent *direction*: over-calling AI, or under-calling it?
- Take one wrong answer. Who would be harmed if that verdict were used to make a real decision about a real person: a student, a job applicant, an artist?
- **No right answer:** you'll be reading what these tools do with your uploads for the terms-of-service part of Part B. Would you run something you actually cared about through one of them?

---

## You're Done!

Good work. You've started collecting real data on a claim a lot of people take at face value.

**Nothing to hand in today beyond your postcard.** Finishing your results table and reading the terms of service can happen before or after lab. See the project guide for what's still needed for Part B.

**Where this goes:** everything today feeds Part B of the project. Next week's lab is your assembly session: Parts A, B, and C get combined and the project is due at the end of it. Your Part C case study should be underway by then; if your group hasn't picked a case yet, do that this week.

---

## Still Stuck?

- **"The tool won't accept our file format."** Note it in your results as a failure mode (that's a real finding) and convert a copy to test with.
- **"We've hit the free-tier limit."** Record how many images you got through and note it. That's fine: pick up the rest outside lab, or later, once any daily limit resets.
- **"The tool gives a percentage, not a verdict."** Record the percentage. Decide as a group where your cut-off is, write down what you chose, and apply it consistently.
- **Actually stuck, not just slow?** Flag a TA: don't just sit quietly waiting for one to notice. Circulation is continuous, but it isn't psychic.

---

<!-- ============================================================
     NOT STUDENT-FACING. Delete before distributing.
     ============================================================ -->

## Notes for Development: REMOVE BEFORE DISTRIBUTING

### Tool-count formula

One tool per group member, floor of three, worked out so a smaller group never does *more* total work than a larger one:

| Group size | Tools tested | Split    |
|------------|--------------|----------|
| 4          | 4            | 1 each   |
| 3          | 3            | 1 each   |
| 2          | 3            | 2 + 1    |

### TA prep required

- Try three or four tools from the class's curated image-tool list yourself (see project guide, Part B) so you know the failure modes: file size limits, daily/monthly scan caps, percentage-vs-verdict outputs.
- Bring postcards: one stack per group, enough for every student, plus spares.
- Circulate from early in the Run block, not from a fixed minute. With 2 TAs and roughly 10 groups, aim to have visited every group at least once by minute 30.
- You are not running a formal checkoff conversation with each group. A glance at a filling-in results table and a tool visibly returning a verdict is the check.

### Where this is likely to break

- **Groups arriving without tool access** is still the big one: completion being optional doesn't help a group that can't even log in.
- **Ambient circulation can miss a genuinely stuck, quiet group.** Unlike a scheduled checkoff, nobody is guaranteed a visit. The "flag a TA" line in Still Stuck exists for exactly this: worth a TA saying it out loud once near the start of the block.
- **Postcards filled out entirely at the end** lose the "as you go" honesty a progressive card is supposed to have. Worth a TA reminder partway through the Run block.
- **Free-tier exhaustion** is still a real event, just lower-stakes now that finishing isn't required: treat it as a finding, not a failure, same as before.

### Clicker answer key

B. The point is that accuracy on an imbalanced dataset is nearly uninformative: a tool that always says "human" scores 90% here while catching zero AI content.

Distractors: A is the naive read and will be popular. C over-corrects: the result is informative, just not in the way the number suggests. D is for students who suspect a trick.

This question also seeds the false positive / false negative distinction that Think It Over Q1 and Q2 then use.

### Think It Over: assessment link

- Q1 (direction of error) → directly feeds the Part B results write-up; this is the "notice something" that separates a 1 from a 2 in the project grading
- Q2 (who is harmed) → the Part B reflection deliverable asks exactly this
- Q3 (would you upload something you cared about) → open; ties back to Data Privacy in Week 3 and forward to Consent in Week 12; rephrased this cycle so it doesn't presume ToS reading already happened by end of lab

### Open questions

- Is there a floor on dataset size? Still open in the project guide. Lower-urgency for lab timing now that completion isn't required, but still worth resolving for consistency of the overall Part B deliverable across groups.
- Should the class track which tools have already been claimed, to actually guarantee spread across the curated list rather than just nudging for it? Worth revisiting after the first run if convergence turns out to be a real problem in practice.

### Assets to produce

- `assets/lab4/results-table-template.xlsx` or `.csv`: still recommended, unaffected by this revision
- `assets/lab4/contribution-postcard-template`: new; a simple print layout with five fields (name/group, tool tested, what I did today, what's next, deep-dive pick, last field needed only once per group)
- ToS scaffolding (keyword list, privacy-policy-vs-ToS note) has moved into the project guide's Part B section: no longer a lab-specific asset
