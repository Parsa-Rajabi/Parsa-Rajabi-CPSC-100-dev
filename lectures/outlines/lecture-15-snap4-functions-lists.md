# Snap 4: Functions and Lists, Lecture 15

**Week:** 6 (Friday, Oct 16)
**Length:** 50 min
**Unit:** Digital Adolescence, Friday programming day

## Learning Goals

By the end of this lecture, students should be able to:

- Explain why a `repeat` loop cannot solve a problem that requires the *same action with different values*, and identify when a custom block is the right tool instead.
- Define a custom block in Snap that takes inputs and performs a sequence of actions.
- Distinguish an input a block genuinely needs from a value that can be *derived* inside the block.
- Distinguish a **command block** (performs an action, hands back nothing) from a **reporter block** (computes and hands back a value, including a yes/no answer), and identify real examples of each from blocks they've already used.
- Use list blocks in Snap (`list`, `add`, `item (n) of`, `length of`) to store and retrieve multiple related pieces of data.

## Big Idea

Students already have variables, math operators, `repeat`, `for`, and `if/else`, and without necessarily knowing it, they've already been *using* custom blocks. The digital exposure calculator's Exposure Index was built entirely out of calls to blocks like `tierWeight()` and `tierBonus()` that somebody else wrote, and that they never had to open. Today's lecture opens that black box, shows what the same logic looks like without it, and only then has students build one of their own. The motivating problem for the build is the one from Lab 2: three shapes, square, octagon, circle, that a `repeat` loop genuinely cannot produce on its own, because a loop repeats the *same* action and can't vary anything between repetitions. Custom blocks are repetition *with variation*. Lists get their own, separate treatment today; combining lists with custom blocks is a Week 8 problem, not a today problem.

**Connection from last class:**
Students arrive with: variables, `set` vs. `change`, and a fixed-count `repeat` (Snap 1, Week 2); the actual square/octagon/circle scripts, built by hand (Lab 2, the Week 3 shapes lab); `for` loops over a range (Snap 3, Week 4); and, most relevant to today, a full lab spent *calling* pre-built custom blocks without ever writing one themselves (Lab 3, the Week 5 digital exposure calculator). This lecture is the first time they open one of those blocks to see what's inside, and the first time they write one themselves.

**Where we're going next:**
Week 8 begins the Snap to Python translation. Today deliberately stays inside Snap's own vocabulary, command block, reporter block, custom block, so that when Python's `def` and `return` show up in Week 8, students already have working, non-Python names for both ideas.

## References

- Lab 2 (Week 3) shapes lab: the square, octagon, and 72-sided "circle" scripts, reused verbatim in the cold open and the block-building section
- Lab 3 (Week 5) digital exposure calculator: `tierWeight()` / `tierBonus()` definitions, referenced in Sections 1, 2, and 6. **The block internals shown below are a reconstruction from the lab's written description (Light=1/Medium=3/Heavy=5), not pulled from the actual saved project. Swap in the real definitions before class.**
- Snap Reference Manual: custom blocks, command vs. reporter vs. predicate blocks, and list primitives

---

## Lecture Flow

### 0. Pre-Class Preparation

Instructor should have the Week 5 exposure calculator Snap project open and ready to project, with the `tierWeight` and `tierBonus` block definitions easy to pull up, plus the static comparison image for Section 2 (see Assets, below) ready to display. Students need Snap open and able to log in at the start of class.

### 1. Open the Black Box, Revisiting Lab 3's Custom Blocks, ~4 min

**0:00-0:04.**

**DO:** Project the Week 5 exposure calculator. Find `tierWeight` and `tierBonus` in the palette and open their definitions.

```
tierWeight (factor) [reports a number]:
    if (factorTier of (factor) = "Light")   -> report (1)
    if (factorTier of (factor) = "Medium")  -> report (3)
    if (factorTier of (factor) = "Heavy")   -> report (5)

tierBonus (category) (depth) [reports a number]:
    if (depth = "shallow") -> report (tierWeight of (category))
    if (depth = "deep")    -> report (tierWeight of (category) x 2)
```

**Emphasize:**
- Students ran this three weeks ago and never had to see what's inside it
- Every Exposure Index change traced back to a call like `tierWeight("numPlatforms")` or `tierBonus("photos", "deep")`
- The point of a custom block: write it once, name it, and after that anyone can call it without knowing how it works inside

**Point:** Students already have a working intuition for "a named block with something complicated hidden inside it," they just didn't have the vocabulary for it yet. Today they get the vocabulary and then build one themselves.

### 2. The Same Logic, Unblocked, ~4 min

**0:04-0:08.**

**Emphasize:** frame the image as the same weighted-sum logic, if nobody had ever wrapped it in a block.

**DO:** Show a static image (see Assets) contrasting the two versions side by side: the six short calls the calculator actually uses versus the same six factors with the full `if/else` chain pasted in at each call site instead. **No need to run either version live or prove they produce the same score, that costs time the section doesn't have. The visual contrast alone makes the point.**

**Emphasize:**
- Six calls versus a wall of duplicated logic; changing how "Heavy" converts to a number would mean six manual edits on the right, by hand
- Code isn't just for the person who wrote it, it's for whoever reads it next, including future-you
- Clean code, not the cleverest, not the trickiest, just the *cleanest*, is what's actually useful to somebody else
- Google's production codebase: over two billion lines, one shared repository, something like 25,000 engineers committing at any given moment
- At that scale nobody can hold the whole thing in their head; encapsulation (hiding complexity inside something you just call) isn't a nice-to-have, past a certain size it's the only way the thing survives

**Point:** Encapsulation is fundamentally for *other people* (and future-you), and it scales. That's the "why" underneath everything that follows today.

### 3. Cold Open, the Polygon Problem, ~3 min

**0:08-0:11.**

**DO:** Put three **visibly different** polygons on screen, square, octagon, and the many-sided "circle", side by side. These are the exact three shapes from the Week 3 shapes lab. Then reveal the code that drew them: three copy-pasted scripts, differing only in the number of sides and the angle that follows from it.

```
repeat (4)               repeat (8)               repeat (72)
  move (60) steps          move (60) steps          move (60) steps
  turn (90) degrees        turn (45) degrees        turn (5) degrees
```

**Emphasize:**
- Students built all three of these themselves, by hand, three weeks ago; this is their own code
- Prompt: if we wanted all three in red and 80 steps instead of 60, how many places need editing? Let them count out loud: six edits across nine lines, three opportunities to typo.

**CLICKER Q1, Can you replace these three scripts with a single `repeat 3` loop?**

- A) Yes, that's exactly what `repeat` is for
- B) Yes, but only if you also add a variable
- C) No, `repeat 3` would draw the same shape three times (correct)
- D) No, Snap can't nest a `repeat` inside a `repeat`

*Facilitation: expect a real split between A and C. Reveal C and explain it verbally: `repeat 3` would draw the same square three times on top of itself, since nothing changes between repetitions. No need to run it live here; the reasoning does the work, and Section 5 has the lecture's real live-coding budget.*

**Point:** Students leave this segment with a named gap in their toolkit. Everything after this is filling it.

### 4. Custom Blocks, Inputs vs. Derived Values, ~5 min

**0:11-0:16.**

**Emphasize:** students already opened one custom block ten minutes ago; now they write one. Goal: one block, `draw polygon`, that can produce any of these three shapes.

**CLICKER Q2, We want one block that can draw any of these three shapes. What inputs does it need?**

- A) Number of sides only
- B) Number of sides and the turn angle
- C) Number of sides and the side length (correct)
- D) Number of sides, the turn angle, and the side length

*Facilitation: B and D are the interesting wrong answers, and probably the popular ones. Draw the numbers out on the board: 4 sides gives 90 degrees, 8 gives 45, 72 gives 5. Ask what those have in common. Someone will land on 360.*

```
turn angle = 360 / sides
```

**Emphasize (the conceptual payoff):**
- The turn angle isn't *chosen*, it's *worked out* from what's already known; that's the input vs. derived-value distinction
- Every extra input is one more thing the person calling the block can get wrong
- Put the arithmetic inside the block, not on the caller

**Point:** Deciding what a block takes as input is a *design decision*, not a mechanical step; there's a wrong answer here even though B and D would both technically work.

### 5. Building `draw polygon` Live, ~9 min

**0:16-0:25.**

**DO:** Build it live in Snap, narrating each step. Keep it slow, this is the mechanical part and students need to see the UI, not just the result.

1. Right-click the palette, **Make a block**
2. Name it `draw polygon`, choose the **Pen** category
3. Add input `sides`, then input `size`, show the `+` between title-text segments
4. Fill the body:

```
draw polygon (sides) (size):
    repeat (sides)
        move (size) steps
        turn (360 / sides) degrees
```

5. Show it appearing in the palette
6. Call it three times, `draw polygon (4)(60)`, `(8)(60)`, `(72)(60)`, to reproduce the opening image in three lines instead of nine
7. **Change one thing to prove the point:** inside the block, edit `move (size) steps` to `move (size x 1.5) steps`; one edit, in one place, and all three shapes grow together

**CLICKER Q3, The block is defined as `draw polygon (sides) (size)`. A student writes `draw polygon (40) (5)`. What appears?**

- A) A shape with sides 40 steps long
- B) A 40-sided shape with sides 5 steps long, a tiny near-circle (correct)
- C) Nothing, Snap reports an error
- D) 40 copies of the same shape

*Facilitation: A is the trap and it will be popular, because it's what the student **meant**. Run it live, and note that this uses a different side count from the 72-sided circle in the cold open: any sufficiently large number of sides reads as a circle to the eye, it isn't one special number. The lesson: Snap does exactly what you wrote, in the order you wrote it; arguments are positional, and the block has no idea what you intended.*

**Point:** A custom block is a named, reusable procedure with parameters. One definition, many behaviours. Fix it in one place, fix it everywhere.

### 6. Command Blocks vs. Reporter Blocks, ~4 min

**0:25-0:29.**

**Emphasize:**
- Open `draw polygon` back up: it moves and draws, but hands nothing back when it's done
- Open `tierBonus` again: it doesn't move or draw anything, it computes a number and hands it back to whoever called it
- Two different kinds of blocks, and Snap actually draws them differently

**DO:** Point at the palette. Command blocks (`move`, `turn`, `draw polygon`) are jigsaw-puzzle shaped, they're steps in a script. Reporter blocks (`tierWeight`, `tierBonus`, `item (n) of`, `length of`, the math operators) are oval-shaped, they compute and **report** a value, which means they can be plugged directly into another block's input slot.

**Emphasize:**
- One more wrinkle: some reporters are hexagon-shaped instead of oval, those report a yes-or-no answer instead of a number or word, and are usually called predicates. Still reporters underneath, they hand back a value, so they still snap into an input slot the same way.
- This is why `say (item (1) of (shapes))` works, but `move (10) steps` could never plug into that same slot; `move` has nothing to hand back
- Forward pointer: we'll come back to this exact split when we move to Python, command blocks become functions with no return, reporter blocks become functions with a `return`

**Point:** This is a real, visually marked distinction in Snap, the block's shape, not just a naming convention, and it previews something students will formalize in Python.

### 7. Clicker Check, Command vs. Reporter, ~3 min

**0:29-0:32.**

**CLICKER Q4, MULTI-SELECT, Select every reporter block below, including any predicates.**

- A) `move (10) steps`
- B) `pick random (1) to (10)` (correct, reporter)
- C) `turn (90) degrees`
- D) `(shapes) contains (item)` (correct, predicate, still a reporter)
- E) `length of (shapes)` (correct, reporter)

*Facilitation: D is the nuance this question exists for. It's hexagonal, not oval, because it's a predicate, and students who over-learned "reporter equals oval" will miss it. The actual test isn't the shape family, it's whether the block hands anything back at all. A and C are jigsaw-shaped commands and should be easy to rule out; if they aren't, that's a Section 6 gap, not a Section 7 one.*

### 8. Lists, ~15 min

**0:32-0:47.**

**This section is intentionally left light. The worked example, the exact script, and both clickers below are for the instructor delivering this lecture (Parsa) to finalize. What follows is the required shape and the constraints it has to satisfy, not a finished script.**

**Motivating hook, a starting point, not a mandate:**
Section 1 opened `tierWeight` and `tierBonus`, both of which take one factor at a time. But the exposure calculator scored six separate factors using six separate variable names. What happens when a program needs to track fifty things instead of six? Nobody wants fifty variables. This reuses material the lecture has already built rather than introducing a new example cold, and it gives students an actual "why," not just a new box to put things in.

Two other directions, if the exposure-calculator callback doesn't land in the room: a running week of screen-time hours, which ties to the course's digital-life framing, or a small set of quiz scores, which ties to the course's own assessment structure and is already concrete to students.

**Primitives to cover, regardless of which example is chosen:**
- `list`, `add`, `item (n) of`, `length of`
- **The 1-vs-0 indexing point is the single highest-priority item in this section and must survive whatever final example gets built.** Snap counts from 1, Python will count from 0, and that mismatch is a guaranteed Week 8 bug.

**Clickers, 2, exact wording and numbers to be finalized once the example is chosen:**
- One clicker testing `item (n) of` against the chosen list, with a 0-indexed distractor and an off-by-one distractor.
- One clicker testing something beyond simple retrieval, `length of` after an `add`, or a short accumulation pattern, so the two clickers don't test the same skill twice.

**Point:** A list holds many related values in order. That's the one idea this whole section has to land; the specific example and exact clicker numbers are in service of it, not the point themselves.

### 9. Wrap-Up, ~3 min

**0:47-0:50.**

- Encapsulation isn't just neat, it's what lets a codebase (or a course project) survive being touched by more than one person.
- A `repeat` loop repeats the *same* action. A **custom block** gives you the *same procedure* with *different values*.
- **Command blocks** do something. **Reporter blocks** compute and hand something back, including predicates, which hand back yes or no. Look at the shape in the palette, jigsaw vs. oval vs. hexagon, and you'll know which is which before you even read the label.
- A **list** holds many related values in order. Snap indexes from **1**; Python will index from 0.

**Bridge to next class:** Monday we go back to the analysis side with clustering. Hold onto today's vocabulary, command, reporter, predicate, custom block, list, because in Week 8 you'll meet their exact Python equivalents, and none of it will be new, just renamed.

---

## Quick Reference: Timing Summary

| Time | Segment | Interaction |
|---|---|---|
| 0:00-0:04 | Open the black box: Lab 3's custom blocks | (none) |
| 0:04-0:08 | The same logic, unblocked (static image, Google-scale stat) | (none) |
| 0:08-0:11 | Cold open: the polygon problem | **Clicker Q1** |
| 0:11-0:16 | Custom blocks: inputs vs. derived values | **Clicker Q2** |
| 0:16-0:25 | Build `draw polygon` live | **Clicker Q3** |
| 0:25-0:29 | Command blocks vs. reporter blocks | (none) |
| 0:29-0:32 | Clicker check: command vs. reporter | **Clicker Q4** |
| 0:32-0:47 | Lists (Parsa to finalize the example) | **2 clickers, TBD** |
| 0:47-0:50 | Wrap-up + bridge | (none) |

**Constraint check:** 6 clicker questions total, 4 fixed (Q1 to Q4) plus 2 to be written for Lists; still above the course's usual 2 to 5 target but down from the previous draft's 7. Lists reached by 0:32, on target. 50 min total.

---

## Notes for Development

### Decisions needed from instructor

- **Resolved: students don't need to touch Snap themselves today.** Confirmed acceptable given the time budget. Section 5 stays instructor-build-only.
- **The `tierWeight`/`tierBonus` definitions in Sections 1, 2, and 6 are a reconstruction**, built from Lab 3's written description (Light=1/Medium=3/Heavy=5), not pulled from the actual Week 5 Snap project. **Swap in the real block definitions before class**, Section 1's opening depends on students recognizing the actual blocks they called, not a stand-in that merely resembles them.
- **Clicker count: 4 fixed plus 2 pending from Lists equals 6, down from 7 in the previous draft.** The cut was the old command-vs-reporter "why" question; its content is now folded into Q4's multi-select format instead of asked separately. If Lists still feels tight at 15 minutes once Parsa builds the real example, dropping one of its two clickers is the next lever, not shortening an earlier section.

### Content notes

- **Command, reporter, and predicate is now a three-shape system, not two.** Section 6 introduces predicates briefly as hexagonal reporters; Q4 is the only place this gets tested, so don't let Section 6's one sentence on predicates get cut for time, or Q4 becomes unfair.
- **Misconception to address:** "a loop and a custom block are basically the same thing." Q1 exists specifically to separate them.
- **Misconception to address:** argument order. Q3. Snap's visual input slots make students feel the block "knows" what they meant. It doesn't.
- **Misconception to address:** "reporter means oval-shaped, full stop." Q4's predicate option exists specifically to break this: the real test is whether a block hands back a value, not what shape family it belongs to.
- **Do not lose the 1-vs-0 indexing flag.** It's now the single required element of Section 8 regardless of what final example Parsa builds. Forward-reference Week 8 explicitly.
- **Do not lose the encapsulation-at-scale framing from Section 2.** It's the reason this lecture opens with Lab 3 instead of the polygon problem, and it's the strongest available answer to "why not just copy-paste."

### Assets to produce

- `assets/images/lab3-tierWeight-tierBonus-blocks.png`: a real screenshot of the two block definitions, pulled from the actual Week 5 project, not the reconstruction above
- `assets/images/unblocked-vs-blocked-comparison.png`: the six short calls vs. the same logic inlined six times, side by side. **This now carries all of Section 2's evidentiary weight since nothing is run live; worth extra care.**
- `assets/images/square-octagon-circle-nine-lines.png`: the cold open image (the three real Lab 2 shapes plus scripts, side by side)
- `assets/images/command-vs-reporter-shapes.png`: a palette screenshot showing a jigsaw command block, an oval reporter block, and a hexagonal predicate block together, for Section 6
- `assets/snap/draw-polygon-complete.xsnap`: the finished reference program
- Lists section assets (example script, any images): left to Parsa; not specified here

### Note on the week

There is **no Snap lab this week**, Week 6's lab is Project 1 Part B (running the AI-detector experiment, TAs signing off on results). This lecture is the only Snap-related contact time students get this week. Per the confirmed decision above, it doesn't include any hands-on coding of their own, and that's accepted as fine given the time budget.
