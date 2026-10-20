# Acceptance criteria — TakeMeter

Five criteria that say what "working" means for this classifier, written in
unit 5 **before** anything was trained.

**All five are yours this time.** None are given. You've had two projects of
practice.

An acceptance criterion names a number. _"The model is accurate"_ is an
opinion. _"Every label has an F1 of at least 0.60 on the held-out set"_ is a
criterion.

Under each, write a sentence or two on **why that number**. A reason that says
something about your data or your taxonomy earns credit — _"I picked 0.60 F1
for `reaction` because it's my smallest label and I only have about 50
examples of it"_. A reason that could be attached to any project does not.

> Missing your own targets next unit costs you nothing. Setting a target so
> easy you can't miss it does.

---

## Pick numbers you can defend

Not numbers that sound impressive. Three labels means a coin-flip guesser gets
about 33%, so a target of 0.40 is barely a target. Your number should sit
somewhere you'd honestly call useful.

**Cover at least three of these five areas.** They're here as prompts, not as a
form to fill in — a criterion that fits none of them is fine if it names a
number.

| Area                  | A question it could answer                                            |
| --------------------- | --------------------------------------------------------------------- |
| Overall accuracy      | How often does it need to be right to be worth using?                 |
| Per-label performance | Is one label allowed to be much worse than the others?                |
| Balance               | How lopsided can your label counts get before it's a problem?         |
| Consistency           | If someone else labelled the same posts, how often should you agree?  |
| Confidence            | Should a confident prediction be right more often than an unsure one? |

Two things worth knowing before you pick numbers, because both will affect
whether you hit them:

- **Your smallest label will have the jumpiest score.** If a label has 50
  examples, about 8 land in the test split. An F1 computed on 8 examples moves
  a lot between seeds. A target for that label should be looser than one for
  your biggest label, and saying so is a good reason.
- **Unit 6 tests across three seeds, and the target has to hold across all
  three.** A target of 0.65 against results of 0.71, 0.62, 0.68 is a **miss**.
  Pick with that in mind — it is stricter than it first sounds.

---

## Criteria 1:

Overall accuracy on the held-out test set is at least 0.70 on every one of the three seeds

**Why this target:**
With three labels, a coin-flip guesser gets about 33%, and always guessing `question` could score 50% or more if /new in boardgame is question heavy. The test split is 15% of 200, about 30 posts, so one post is about 3 points of accuracy. 0.70 is clearly above both baselines, and it allows for the posts on my `question`/`experience` boundary.

---

## Criteria 2:

`question` and `experience` each have an F1 of at least 0.70 on the test set, on every seed.

**Why this target:**
These are my two likely largest labels, so they have the most training examples. They are also the pair my hardest boundary sits between (an opinion post that ends with a question), so most errors should land here. 0.70 means the model gets most of those boundary cases right.

---

## Criteria 3:

`statement` has an F1 of at least 0.55 on the test set, on all three seeds.

**Why this target:**
This is the label I expect to be smallest. With about 40 posts, only about 6 land in the 15% test split, so one wrong prediction moves F1 a lot. That is why this target is looser than criterion 2. I didn't go lower because `statement` posts have clear structure (roundups, announcements, links), so the model should do better than its size suggests.

---

## Criteria 4:

In `labels.csv`, no label is more than 60% of posts, and `statement` has at least 40 posts (20% of 200).

**Why this target:**
The /new page is mostly questions, so I could easily end up with too many of them. If one label takes up more than 60%, the model can score well just by guessing it. I need at least 40 `statement` posts(floor of 40 comes from the 70/15/15 split), so that about 6 land in the test set. With fewer than that, I can't trust the score for that label.

---

## Criteria 5:

On the test set, accuracy on the model's most-confident third of predictions is at least 0.80, on every seed.

**Why this target:**
The notebook scores the most-confident third of the test posts. My test split is about 30 posts, so that third is about 10 posts, and 0.80 means at least 8 of 10 right. A model that is very sure should be more reliable than its overall 0.70, so I set this 10 points higher. Because it's only 10 posts, one or two mistakes can swing the result, will check the other seeds before drawing the conclusion.

---

<!-- ─────────────────────────────────────────────────────────────────────────
     UNIT 6 — read this before you change anything above.

     If a criterion turns out to be BROKEN rather than merely unmet, you can
     revise it, and that earns credit. But never delete or edit the original
     line. Add the revision underneath, like this:

         ## 2. Every label performs acceptably

         The model performs well on all labels.

         **Why this target:** ...

         > **Revised in unit 6:** Every label has an F1 of at least 0.60 on
         > the held-out set.
         >
         > **Why revised:** "performs well" gave me nothing to check. I
         > couldn't produce a verdict from it at all.

     That's a revision because the criterion couldn't be MEASURED.

     Lowering a target because you missed it is not a revision, and it costs
     you the point:

         ✗ "Overall accuracy of at least 0.65" → "at least 0.55", because
            0.65 turned out to be optimistic for 200 examples.

     A number you missed stays where it is, gets diagnosed, and gets a fix
     attempted. That's where the points are.
     ───────────────────────────────────────────────────────────────────────── -->
