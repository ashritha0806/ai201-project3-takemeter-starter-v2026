# TakeMeter

> ### 👋 Start here
>
> **New to this repo? Read [RUNNING.md](RUNNING.md) first** — setup, the
> notebook, the baseline, and what to do when something breaks.
>
> Once `python test.py` passes:
>
> ```bash
> head -5 data/practice_labels.csv     # the shape your labels.csv needs
> ```
>
> Then open `takemeter.ipynb` **in this folder** — in VS Code, or with
> `jupyter notebook` if you prefer. Pick the kernel: the `.venv` inside this
> project. Run section 1, which reports the hardware you'll be training on.
> Everything else waits until you have data.
>
> Nothing to upload, nothing to connect, no accounts and no keys. The notebook
> runs on your machine and writes next to your code.
>
> **The rest of this file is your submission.** Fill it in as you go.

---

<!-- ─────────────────────────────────────────────────────────────────────────
     HOW TO USE THIS FILE

     Unit 5 asks for the first five sections. Unit 6 adds the five below them.

     Everything is pasted as TEXT. No screenshots, no images.

     ⚠️ The confusion matrix especially. The notebook prints one as a markdown
     table, ready to copy. A screenshot of a matrix earns nothing. Paste the
     table.
     ───────────────────────────────────────────────────────────────────────── -->

<!-- ═══════════════════════ UNIT 5 — THE BUILD ═══════════════════════ -->

## What This Does

<!-- Your community, and what your classifier sorts posts into. Three or four
     sentences. -->

Community: Boardgame
Source: https://www.reddit.com/r/boardgames

Distinctions from my readings:

1. Question vs statement: Many posts ask for something (rules clarification, “what game is this?”, “which game for a group of 5-6?”, “games similar to X?”). Others make a claim or share an experience (“I played X with my group and it was great”).

2. Reasoned opinion vs bare reaction: Some reviews or buy/don't buy discussions say why (mention mechanics, player count, playtime, comparison to another game). Others just say “great game” or “should I buy it?” with no detail.

3. Creation vs discussion: Some posts show something the person made (3D-printed copies, custom expansions, original game designs, art) rather than discussing a game. These don't give much to evaluate as a take.

4. News vs opinion: Some posts relay information (Kickstarter/GameFound/Backerkit funding lists, new Exploding Kittens holiday edition, expansion announcements) with no personal stance.

---

## Label Taxonomy

<!-- Each label: a one-sentence definition and two real examples from your
     reading. Then your decision rule for the hardest boundary.

     The decision rule is worth a point on its own and it's the thing most
     people leave out. Every taxonomy has a hardest boundary. Name yours. -->

### `question`

**Definition:**
The poster needs an answer from the community: a game's rules, whether a game is available or worth buying, whether a seller is legitimate, or which game to play or find.

**Example 1:** This War of Mine: What is the second edition?

> Hello there,

I am relatively new to the board game scene and experimenting with different games, and having a ton of fun. I don't understand the availablity sometimes, but thought that was fine.

I was looking for This War of Mine because I adore the videogame and heard good things about the board game. But when reading into it, I saw that there was a gamefound campaign for the second edition.

My question now: Is this second edition coming to retail? If so, when exactly? And is that one making the base game you can currently buy in stores kinda obsolete? I tried to read their FAQ but didn't understand anything.

**Example 2:**Is Hive Interactive legit or this pledge still active?

> Hey there,

I need your help because this seems waaay too opaque for me. At the moment, Keep the Heroes Out expansions seem to be out of stock everywhere, but this pledge manager(?) seems to be active:
https://www.hiveinteractive.net/projects/keep-the-heroes-out-dungeons-below-2nd-wave-488

Does anyone have prior experience with this?

Is the website legit?

Is this pledge still "pledgeable"? I don't see any deadline here and the matching Kickstarter campaign seems to be finished already.

I think this pledge has a low chance of failing to fulfill the requests (because it's mostly a reprint of already existing stuff) but still, there seem to be a lot of uncertain parts here.

### `statement`

**Definition:**
The poster shares information, an announcement, or a list about games or the industry, and takes no personal stance on a game and asks nothing of the reader

**Example 1:** GAMA, the tabletop industry's trade association, told the FTC to ban surveillance pricing

> GAMA, the tabletop industry's trade association, told the FTC to ban surveillance pricing

In August, the U.S. Federal Trade Commission (FTC) proposed an enforcement policy on personalized pricing — sometimes called "surveillance pricing" — and invited public comment. Nearly 4,600 responses came in, including a lengthy one from GAMA: The Tabletop Game Association, which represents both publishers and retailers (along with designers, manufacturers, and other groups).

Personalized pricing is when a store shows different customers different prices for the same product based on their browsing history, purchase data, location, and so on. If the algorithm decides you would pay $70 for a game, you see $70. Someone else might see $60. The FTC's proposal would merely require businesses to disclose the practice — and GAMA's position is that disclosure is not enough. The practice should be prohibited outright because it's anti-consumer, whether or not anyone discloses that they use it.

The part of GAMA's comment I found most interesting is that personalized pricing would put its members in conflict with one another, undermining trust between consumers and retailers and between consumers and publishers who sell direct, while tilting the field further toward large online sellers (e.g., Amazon). An industry association choosing to publicly support an individual human's side of a fight rather than its biggest members' side is not something you see every day.

I went through GAMA's full statement and the surrounding context here: https://www.wericmartin.com/gama-opposes-personalized-pricing/

Retailers in this hobby already operate on thin margins, and the tooling for this kind of pricing is getting cheaper every year. Whether the FTC's disclosure-only approach holds or whether more U.S. states will ban the practice (as three already have to some degree) matters to anyone who buys games — which is to say, everyone here.

**Example 2:**Finally! First Kingdom Come full playthrough

> For those who are into mediaval board game adventure…

Paul Grogan is doing live playthrough on his YouTube of this highly anticipated Spiel Essen release Kingdom Come: Deliverance by Vlaada Chvatil and Tomas Holek

https://www.youtube.com/watch?v=zQco0XqZwps

### `experience`

**Definition:**
The poster describes their own experience of a game they have actually played and how they felt about it.

**Example 1:**My first boardgame, Covenant!

> I was already interested in starting the hobby and was thinking about buying a simpler game, but then I discovered this dwarf themed game with exactly the type of artwork I love, and as someone who really loves fantasy dwarfs I couldn't resist.

As I never played any boardgame and my friends only had experience with monopoly I was worried about whether I would be able to explain the rules properly and whether they would actually enjoy the game, but to my surprise all of us had a really fun night! Playing the game solo for a bit on tabletop simulator really helped me to explain it to everyone.

That said, I probably shouldn't have bought a 3.74 complexity weight game to our first boardgame experience, so I'm thinking about bringing The crew or Azul to the table as our next game.

Also, we ended up ignoring the rule about gate positioning because I only remembered about it halfway through the game and we were a bit too drunk to care.

**Example 2:** Bag of Dungeon 2 The Cursed Forest

> Played BOD2 it is extremely fun and

brutal game 😁. Good for Solo or multiplayer game, i recommend buying this game. 🔥🔥

https://www.gunpowderstudios.co.uk/bod3d/?fbclid=IwdGRjcAVC1d1jbGNrBULVqGV4dG4DYWVtAjExAHBkb2YBc3J0YwZhcHBfaWQMMzUwNjg1NTMxNzI4AAEe\_c2xngDxAh\_qCcZKl4RQYKqmCXrrjpgCb4y\_eFVUTIe6xTFPAQG8J0meAvw\_aem\_yhlLCqc\_Hgiqor1jpRTtUg

### The hardest boundary

**Which two labels:** `question` and `experience`

**The decision rule I used every time:**

<!-- e.g. "If the post names a specific checkable fact, it's `analysis`, even
     if the tone is heated." -->

If a post is mainly about the poster's own experience of a game they have played, label it `experience`, even when it ends with a question to the community (If the post still makes sense with the question deleted, it is `experience`).

---

## The Dataset

<!-- Where you collected from, how you labelled, your counts, and three hard
     cases. -->

**Where the posts came from:**
All 200 posts were collected from r/boardgames (https://www.reddit.com/r/boardgames/), browsed through the /new feed and the top posts of the past week. Each post was pasted in full (title plus body) into `labels.csv`

**How I labelled them:** <!-- Cold first? Pre-labelled with AI and corrected? Say so plainly — the disclosure is required, not penalised. -->
I labelled the first 20 posts cold, by hand, using only my definitions. The remaining 180 were pre-labelled by an AI tool that I gave my label definitions and my decision rule, and I then read them and corrected the ones I disagreed with. In `labels.csv`, the cold rows are marked `cold` and the pre-labelled rows are marked `pre-labeled` in the note column. My rule while labelling: if a post was the poster's own review or experience of a game, I labelled it `experience` even if it ended with a question, as long as removing the question still left the review making sense. If the poster was simply asking for information, game rules, or what game to play, I labelled it `question`. Anything that fit neither news and information posts, like someone announcing a new project or a game they built, something they painted for a game, or a fundraising event I labelled them as `statement`.

**Counts per label:**

| Label      | Count | Share |
| ---------- | ----- | ----- |
| question   | 122   | 61 %  |
| statement  | 36    | 18%   |
| experience | 42    | 21%   |
| **Total**  | 200   | 100%  |

**Three hard cases**

<!-- Any post that made you pause: what it was, which two labels it could have
     been, and what you chose. These are worth more than the easy 190. -->

**1.**

> _The post:_
> "Twilight Imperium on BGA!
> I’m not sure how I feel about it. For a game that hits the table mostly at conventions, this seems cool to be able to get through a game faster. But, for me, the table interaction, voting on decrees, making verbal deals, and opportunities for roleplay are part of what make it epic.

That gets lost online"

> _Could have been:_ `experience` or `statement`
>
> _I chose, because:_ I chose `statement`, because it is a generalised statement and it doesn't speak about a particular game the poster played or review anything they played.

**2.**

> _The post:_
> "What's your favorite game with a theme that you don't really enjoy?

I personally really love Bullet's theme because I just so happen to be the core audience the game is looking for, an anime fan that likes Touhou and Board Games. I think the game translates the theme extremely well. Between all the modes it supports (Boss Battles, Team Battles, Competitive, and Score Attack) which are standard features of the video games it emulates and how the game plays to act like a Bullet Hell with how it makes you think on the spot, I think Bullet is actually a game that deserves a spot on the BGG Top 100. However I'm using it as my example because I know that it's a theme that the general board game audience don't really like. Turns out the people that are into Board Games tend to look for either the more "immersive" games like The LoTR and Dune games, or are looking for more "friendly" themes to play with family and friends like Fliptoons, Flip 7, and just the usual Catan/Monopoly. Really, just looking at Fernet in the second pic should give you an idea why. the core audience that Bullet wants to attract just aren't in the space as much so it usually just kinda gets tossed away to the side by most people.

Fitting my actual question though I just could not get into Dune Imperium thematically because I hate the book but it tends to be the game I think of first when going into my LGS for Board Game Sunday."

> _Could have been:_ `question` or `experience`

> _I chose, because:_ I chose `experience`, because even though the headline feels like a question, the post itself is mainly the person sharing their experience and how it felt.

**3.**

> _The post:_
> "Pillars of Fate vs. Zenith comparison
> I love board games and play a wide range of genres and complexities. My wife likes games like Azul, Duel for Middle Earth, Spooktacular, Sea Salt and Paper, Patchwork, etc. so nothing too long or thinky.

One of our favorite games is Schottentotten, we love to travel with it as well and our copy has traveled the world :). A small box and play area are important factors as well, which is why it is probably our most played game. Not a huge deal if it doesn’t travel well but wanted to mention it. These two games (Pillars of Fate and Zenith) caught my attention because they seem to share a similar concept and build out the tug of war over a central area/card/lane. I have not played either but I think both seem like a nice step up in terms of strategy/mechanics with a similar concept/goal but not too much added complexity. Do you think either of these would be a good fit or maybe a different in general? She also didn’t like Radlands."

> _Could have been:_ `question` or `experience`
>
> _I chose, because:_ I chose `experience`, because without the question the post still makes sense, it is mainly the poster's experience and it passes my delete the question test to figure out between question and an experience.

---

## The Training Run

<!-- Your starting model, your settings, and anything you changed and why. -->

**Base model:**
distilbert-base-uncased
device: mps (Apple Silicon GPU (MPS))
torch: 2.14.1

**Settings:** <!-- epochs, learning rate, batch size, seed -->
3 labels: question, statement, experience
seed 42, 3 epochs, lr 2e-05, batch 16

**Anything I changed from the defaults, and why:**
only one edit is section2 fill-ins.

**Split sizes:** <!-- train / val / test, and per-label counts in the testsplit. If a label had fewer than about 8 in test, say so — it explains a lot of next unit's variance. -->

Train 139, validation 31, test 30. In the test split: question 18, statement 6, experience 6. Statement and experience have only 6 each in test, fewer than about 8, so their per-label scores will move around between seeds.

## How I Used AI

<!-- Two specific moments — what you asked, what came back, what you changed.

     ⚠️ Plus disclosure of any pre-labelling. If you had a model pre-label a
     batch and then read and corrected every one, say that. It's an allowed
     workflow and disclosing it costs you nothing. Not disclosing it is the
     problem. -->

**Moment 1**

- _What I asked for:_ I asked the AI to pre-label the 180 posts I had collected, using my own label definitions and my delete the question decision rule.

- _What came back:_ It returned a label for every post, in four batches, flagging the borderline rows and giving a reason for each one it hesitated on.

- _What I changed:_ I read the pre-labelled posts and corrected the ones I disagreed with. I changed the Twilight Imperium on BGA post to `statement`, and the "favorite game theme" post and the Pillars of Fate vs. Zenith post to `experience`, and I kept the two playtest announcements as `statement`.

**Moment 2**

- _What I asked for:_ I gave my label distinctions, my definitions, and acceptance criteria written by me, and asked the AI to pressure-test them: to argue against each one and find where labels overlapped or a target was too easy or too hard.

- _What came back:_ It showed that my original `opinion` and `reaction` labels overlapped too much to stay separate, and it challenged each of my criteria targets with the strongest case for and against it.

- _What I changed:_ I merged `opinion` and `reaction` into a single `experience` label and wrote the delete the question rule for the question/experience boundary.

**Pre-labelling disclosure:**
Out of my 200 posts, I labelled the first 20 cold, by hand. The remaining 180 were pre-labelled by an AI tool that I gave my label definitions and decision rule, and I read them and corrected the ones I disagreed with. In labels.csv, the cold rows are marked cold and the pre-labelled rows are marked pre-labeled in the note column.

<!-- ═══════════════════════ UNIT 6 — THE TEST ═══════════════════════

     Don't fill these in during unit 5.
     ═══════════════════════════════════════════════════════════════════ -->

---

## Baseline vs. Trained

<!-- Both models on the same posts. `python baseline.py --trained results.json`
     prints this table for you. -->

| Measure           | Baseline |
| ----------------- | -------- |
| Overall accuracy  | 0.300    |
| Macro F1          | 0.223    |
| F1 — `experience` | 0.323    |
| F1 — `question`   | 0.348    |
| F1 — `statement`  | 0.000    |

| Measure           | Baseline | Trained | Difference |
| ----------------- | -------- | ------- | ---------- |
| Overall accuracy  | 0.300    | 0.600   | +0.300     |
| Macro F1          | 0.223    | 0.250   | +0.027     |
| F1 — `experience` | 0.323    | 0.000   | -0.323     |
| F1 — `question`   | 0.348    | 0.750   | +0.402     |
| F1 — `statement`  | 0.000    | 0.000   | +0.000     |

**What I predicted before I looked:**

<!-- Milestone 1 asks you to write this BEFORE seeing the trained numbers. A
     prediction made afterwards isn't one. -->

I think my trained model will beat the baseline on statement(F1 of 0.000). The baseline only had one line definition and it couldn’t pick out a single statement post. After training on my 200 labeled posts, the model should have seen enough examples for statement.

**What the gap actually means:**

<!-- If the baseline matched your trained model, your fine-tuning added
     nothing — and that is a real finding, not a failure. Say it plainly. -->

---

## Run Log — Before

<!-- Five criteria across three seeds. The notebook's section 6 prints the
     spread table; the Target and Verdict columns are yours. -->

| Criterion | Target | Seed 42 | Seed 7 | Seed 2024 | Verdict |
| --------- | ------ | ------- | ------ | --------- | ------- |
| 1.        |        |         |        |           |         |
| 2.        |        |         |        |           |         |
| 3.        |        |         |        |           |         |
| 4.        |        |         |        |           |         |
| 5.        |        |         |        |           |         |

### Confusion matrix

<!-- ⚠️ TYPED AS A MARKDOWN TABLE. The notebook prints one ready to paste.
     An image of a matrix earns nothing. -->

| true \ predicted |     |     |     |
| ---------------- | --- | --- | --- |
| \*\*\*\*         |     |     |     |
| \*\*\*\*         |     |     |     |
| \*\*\*\*         |     |     |     |

**My biggest off-diagonal number, and what it means:**

<!-- Not "the model made mistakes" — WHICH boundary it didn't learn, and which
     direction. "7 real analysis posts were called hot_take and only 3 went the
     other way" is a direction, not just an error rate. -->

---

## Verdicts and Diagnoses

<!-- MET or MISSED against LAST UNIT's target. The target has to hold across
     all three seeds, not turn up sometimes. -->

| #   | Criterion | Target | Verdict | How I decided |
| --- | --------- | ------ | ------- | ------------- |
| 1   |           |        |         |               |
| 2   |           |        |         |               |
| 3   |           |        |         |               |
| 4   |           |        |         |               |
| 5   |           |        |         |               |

**Diagnoses**

<!-- For each miss: the cause, and how you know. The four common causes are:
     too few examples for a label, a boundary you applied inconsistently, a
     genuinely hard label pair, and a task the model can't reach from this
     much data.

     ⚠️ Use your agreement report as evidence. It is the only instrument you
     have that can tell a LABELLING problem from a MODEL problem, and this
     section is graded on whether you used it that way. -->

---

## Agreement Report

<!-- Your rate against the staff set, and every disagreement adjudicated.

     Remember you labelled these 30 under the STAFF taxonomy in
     data/staff_taxonomy.md, not your own — so every argument below is made
     from those definitions and those decision rules. -->

**Agreement rate:** **_ / 30 = _**%

<!-- Nobody grades this number. A 60% who argues every disagreement from the
     stated rules beats a 95% who wrote "staff was right" nine times. Several
     of the 30 were chosen because they're genuinely ambiguous — you should be
     winning some of these. -->

**Disagreements**

<!-- Three lines each: the post, both labels, and who you think is right and
     why — grounded in the staff definitions you were both applying.

     Then sort each into one of three piles:
       (a) the rule covered it and I applied it loosely → a consistency problem
       (b) the rule genuinely doesn't say               → a gap in the definitions
       (c) the rule is ambiguous here and my reading is defensible → argue it.
           This is a legitimate win.

     Pile (a) is the one that matters most for your diagnosis: if you applied a
     written rule two different ways on 30 posts, that is direct evidence about
     what you did across your own 200. -->

**1.**

> _The post:_
>
> _Staff said / I said:_
>
> _My call, and why:_
>
> _Which pile:_

**2.**

> _The post:_
>
> _Staff said / I said:_
>
> _My call, and why:_
>
> _Which pile:_

**What the pattern in my disagreements tells me:**

---

## The Improvement

**What I changed:**

**Which diagnosis pointed at it:**

### Run Log — After

| Criterion | Target | Seed 42 | Seed 7 | Seed 2024 | Verdict |
| --------- | ------ | ------- | ------ | --------- | ------- |
| 1.        |        |         |        |           |         |
| 2.        |        |         |        |           |         |
| 3.        |        |         |        |           |         |
| 4.        |        |         |        |           |         |
| 5.        |        |         |        |           |         |

**Did it help, and how do I know:**

<!-- If it didn't, say so. Relabelling that didn't help is a genuinely
     interesting result and earns full credit. -->

---

## What's Still Broken

<!-- For each criterion still missed: what you'd do, and why you stopped. -->

**The gap between what I meant my labels to capture and what the model
learned:**

<!-- Two sentences. Your confusion matrix is the evidence. -->

<!-- ═════════════════════════════════════════════════════════════════════

     SUBMISSION CHECKLIST — unit 5

       [ ] criteria.md has five numbered criteria, each naming a NUMBER
       [ ] Each has a reason underneath tied to your data or taxonomy
       [ ] labels.csv: at least 150 rows, text/label/note, ONE file not split
       [ ] No label above 70%
       [ ] All five unit 5 sections have real content
       [ ] Label Taxonomy includes the decision rule for your hardest boundary
       [ ] The Dataset includes three hard cases
       [ ] results.json and test_split.csv committed (the notebook does this)
       [ ] At least four new commits
       [ ] Repository URL submitted — WRITE IT DOWN

     SUBMISSION CHECKLIST — unit 6

       [ ] Baseline vs. Trained table, with your prediction written beforehand
       [ ] Run Log — Before, five criteria across three seeds
       [ ] Confusion matrix TYPED AS A MARKDOWN TABLE
       [ ] A verdict on every criterion
       [ ] A diagnosis for every miss, using the agreement report as evidence
       [ ] Agreement Report with every disagreement adjudicated
       [ ] One improvement, with Run Log — After
       [ ] What's Still Broken
       [ ] results_three_seeds_before.json, results_three_seeds_after.json,
           baseline_results.json and
           agreement_results.json committed
       [ ] At least four new commits
       [ ] The SAME repository URL as last unit

     Do not delete and recreate this repository.
     ═════════════════════════════════════════════════════════════════════ -->

---

📖 **How to run this project: [RUNNING.md](RUNNING.md)**
