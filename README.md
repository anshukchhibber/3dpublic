# PrintCraft: lightning-talk pack

> A public summary of PrintCraft, a personal tool that turns a description or a photo into a checked, printable 3D model. The app itself lives in a private repository; this page and its pictures are what can be shared.

Each section below is one candidate slide: a title, one to three bullets and
a picture. Pictures are in [img/](img/) and linked relative to this file, so
they show on GitHub and can be dragged straight into slides. Numbers come
from this repo as of 2026-11-16; where a number could drift, the source is
named so it can be recounted.

---

## 1. What PrintCraft is

**A layer for 3D modeling for dummies.**

- You describe a thing (or photograph it). PrintCraft builds it as a
  parametric OpenSCAD model for a Bambu P2S 3D printer.
- The problem: a 3D model file has no memory of how it was made, so changing
  "a bit wider" means starting over, and nobody can tell if it will print
  until the print fails. PrintCraft keeps the recipe (the parameters) and
  checks every result before it reaches the printer.

*The home screen: a box to type an idea, and the catalogue of projects by category.*

![The PrintCraft home screen](img/app-home.png)

---

## 2. How it works

- Describe or photograph, a short interview writes a brief, code builds
  concepts, one "Build this" button opens the workshop.
- In the workshop every edit (a slider, or the AI chat) changes parameters.
  The model is rebuilt from them and checked again.
- Out come a print file and a print guide.

Picture: [img/flow.svg](img/flow.svg), a hand-written SVG (1280 x 520, no
fonts to install; PowerPoint and Keynote accept SVG directly).

![Flow from idea to print file](img/flow.svg)

### 2a. The gate (what is checked)

- Every model is rebuilt and tested for: watertight mesh, the right number of
  parts, fits the print plate, prints without supports (or says where it
  needs them), and holds the volume it claims.
- The result reads PRINT-READY, or says in words what is wrong.

### 2b. Why there is no free-form mesh editing

- A model file has no feature history, so pushing and pulling its surface
  cannot be undone, re-proved or re-sized later.
- So every edit is a change of parameters and the model regenerates. That
  limit is the product: everything stays checked.

---

## 3. How it was built with Claude

- Claude Code writes the OpenSCAD models and the app itself.
- A playbook of lessons grows after every project: a short core file
  (`CLAUDE.md`) plus 45 topic files in `docs/playbook/`, each read only when
  its topic is touched.
- Work is split into small fresh helper chats, each on the cheapest model
  that fits (Haiku for searching and checks, Sonnet for most building, Opus
  for design calls and review). The reason is cost: a measurement in
  the project's plan (docs/v10.md, in the private repository) found about 97% of the tokens went to long build
  chats, not to the app.
- Nothing lands unproved: 92 test files in `tests/`, a full check chain
  (`py src/proof.py`), and the gate above for every model.
- 511 commits on the current branch.

No picture needed. Option: the model table from the project's plan (docs/v10.md, in the private repository)
("Which model does what"), or the flow diagram with "Claude writes" over
steps 3 and 5.

---

## 4. What I've made

**40 projects, 160 designs** (counted from `src/customize.json`, test pieces
not counted), in four categories: Exercise & rehab (19 projects), Home &
bathroom (5), Component library (12 families of joints, clips, hinges,
springs, gears, mounts, threads), Decor & display (4).

**Honest status:** every design is checked in CAD by the gate. Only one
design (the watering jug, twisted style) carries a recorded print result,
and that result is marked as an earlier version of the shape. The rest are
checked in CAD only, nothing printed yet, and PrintCraft's own rule is not to
call a model tested without a print. Two designs (the grip trainer's bars and
dome) are marked "not for use yet" because they print but would not do their
job as modelled. Pictures below are renders, not photos.

### Exercise & rehab: one-hand and weak-grip aids

| Picture | Project, one line |
|---|---|
| ![Peg board](img/peg-board.png) | **Peg board**: a nine-hole peg board you can time yourself on, with a rack for the pegs. |
| ![Marble maze](img/marble-maze.png) | **Marble maze**: a tabletop tilt maze worked with the palms, nothing gripped. |
| ![7-day tracker](img/week-tracker.png) | **7-day tracker**: a week on the wall; push a day's pad up until it clicks. |
| ![Dominoes](img/dominoes.png) | **Dominoes**: a double-six set with racks that show every dot. |
| ![Token box](img/token-box.png) | **Token box**: post a token in the slot and it slides back out to you. |
| ![Putty tools](img/putty-station.png) | **Putty tools**: a one-hand station for exercise putty. |
| ![Plate guard](img/plate-guard.png) | **Plate guard**: a wall that clips to a plate rim so food can be pushed onto a fork one-handed. |
| ![Card holder](img/card-holder.png) | **Card holder**: holds a hand of cards for one-hand play. |
| ![ADL aids](img/adl-aids.png) | **ADL aids**: key turner, button hook and zip rings (the key turner is shown). |
| ![Jar wrench](img/jar-wrench.png) | **Jar wrench**: opens jars and bottles with one hand (the popper is shown). |
| ![Phone stand](img/phone-stand.png) | **Phone stand**: a one-hand stand for bed or table. |
| ![Crutch caddy](img/crutch-caddy.png) | **Crutch caddy**: clamps on a crutch and carries a bottle, phone and keys. |

Also in this category: big-grip checkers, nut and bolt, dice tower, desk
caddy, nail clipper board, finger trainer, grip trainer (on hold).

### Home & bathroom

| Picture | Project, one line |
|---|---|
| ![Watering jug](img/watering-jug.png) | **Watering jug**: a 2 L indoor jug in five surface styles (spiral shown). The one design with a recorded print result. |
| ![Sponge holder](img/sponge-holder.png) | **Sponge holder**: a draining sponge saddle for the sink divider. |
| ![Lily pad coaster plant](img/lily-coaster-plant.png) | **Lily pad coaster plant**: a lily whose pads lift off as coasters. |

Also: washroom shelf (stacking trays).

### Decor & display

| Picture | Project, one line |
|---|---|
| ![Facet luminary](img/facet-luminary.png) | **Facet luminary**: a faceted shade over a battery tea light. |
| ![Om wall art](img/om-wall-art.png) | **Om wall art**: a large Om that stands off the wall and glows from an LED strip behind it (one piece shown). |

Also: symbol wall art (seven symbols), and the MainChick PopSocket topper and
charm (puffy two-colour wordmark letters; MainChick is a brand I made).

### Component library

Twelve families of parts checked in CAD, to build from rather than finished
products: joinery, clips, hinges, springs, gears and ratchets, slides,
mounts, vents, threads, fit and form test plates, grid storage.

---

## 5. What it looks like

Slide-ready screenshots. Captions say only what each one shows.

**Project page.** One project open: its pieces, the print plan with the test
piece first, and the 3D view.

![A project open](img/app-project.png)

**Print guide.** Time, filament and cost, size, then the pieces in print
order.

![A print guide](img/app-guide.png)

**Concept board.** One checked concept marked PRINT-READY with a "Build this"
button, and quick sketches below. Taken in a test run with a stand-in AI, not
a real one.

![The concept board](img/app-concepts.png)

**After "Build this".** The workshop opens at once with four named steps (the
model, the print check, the test piece, the guide). Stand-in AI run.

![Workshop with build steps](img/app-build-steps.png)

**A slider edit.** Changing a wall-height slider shows a live preview and a
"1 change not kept yet" card with Keep and Discard.

![A slider edit with Keep and Discard](img/app-sliders.png)

**Print menu.** The Print button's menu: slicer choices, and the material
advised with a reason.

![The print menu with material advice](img/app-print-menu.png)

**Test piece first.** A dialog before printing: this project's test piece
has not been marked printed yet.

![Test piece dialog](img/app-test-piece-dialog.png)

(The home screen from section 1 makes eight.)

---

## 6. What's next

From the project's plan (docs/v10.md, in the private repository):

- **Checks that follow the job:** the rules should depend on what a piece is
  for and where it is loaded, while staying deterministic.
- **Side-by-side colours:** two-colour printing as stacked layers exists;
  colours printed next to each other is not built.
- **Sharing with friends:** a friend's changes stay in their own folder, and
  the repo is cleaned of anything personal before it is pushed.
- **Cheaper to run:** far fewer tokens in the app's own AI steps.
- **Blender for changing a generated model:** planned, not started.

---

## Notes for the slide builder

- Suggested order: 1, 2 (with the diagram), 4 (one slide per category, 3-4
  pictures each), 5 (pick three), 3, 6.
- All pictures are under 300 KB. Gallery renders come from the repo's own
  docs; the small ones are upscaled thumbnails, so use them at about a
  quarter of the slide width.
- Do not say "tested" or "proven" about a model; say "checked in CAD".
