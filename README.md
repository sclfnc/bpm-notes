# Business Process Modeling: Lecture Notes

Typeset lecture notes for **Business Process Modeling** (BPM), University of Pisa,
academic year 2025/26, taught by Roberto Bruni and Andrea Vandin. The notes cover
BPMN and EPC visual notation, Petri nets and workflow nets, occurrence graphs,
liveness and boundedness, soundness and structural analysis (invariants,
free-choice nets, S/T-systems), process mining, conformance checking, and
quantitative analysis. The official course page with the full slide set is on
[didawiki](https://didawiki.di.unipi.it/doku.php/magistraleinformaticaeconomia/mpb/start).

> ⚠️ **Disclaimer.** Derived from the *Business Process Modeling* course
> materials (Academic Year 2025/2026), MSc in Data Science & Business
> Informatics, University of Pisa.
>
> These notes are open educational content created by a student. They are **not
> an academic source** and may contain inaccuracies. You may freely share,
> modify, and reuse this material for educational and non-commercial purposes
> with appropriate attribution. The content is my personal interpretation of the
> professor's course materials and should not replace official teaching
> resources. I assume no responsibility for any errors or misinterpretations.
>
> These notes were produced with an **AI-in-the-middle** workflow: a first human
> pass, then **Claude Code** to support formulation, understanding, and
> rewriting, followed by a final human review.
>
> If you find errors, have suggestions, or spot unintentionally included
> copyrighted material (which I will promptly remove on notification), contact me
> at `sclfnc@proton.me`.

This course is part of the [MSc Data Science lecture notes](https://github.com/sclfnc/unipi-ds-notes) collection (University of Pisa), one repository per course. Clone the whole set with `git clone --recursive`.

## Layout

- `main.tex`: entry point, in the folder root; identical across the whole
  notes collection (it only loads the shared preamble and the course file).
- `src/housestyle.tex`, shared house style: geometry, colors, section and ToC
  formatting, running heads, and the math environments (theorem, definition, …).
- `src/common-preamble.tex`: the shared package set, identical across courses.
- `src/course.tex`, everything specific to this course: title metadata, math
  macros, the box-free `definition`/`note`/`example` callouts, the TikZ BPMN
  element styles (`bpmn task`/`gateway`/`event`/`flow`), the `listings` style,
  and `hyperref`/`cleveref`, plus the `\input{sec/...}` list.
- `sec/NN-*.tex`: section files (the body of the notes), pulled in by
  `course.tex` via `\coursebody`.
- `img/`: a handful of raster figures (the BPM wheel, the Königsberg bridges,
  a BPMN thesis example) used in the introduction; all other diagrams are native
  TikZ, no slide screenshots.
- `bpm-notes.pdf`: the compiled notes, in the folder root.
- No bibliography: the notes carry no `.bib` file and use no `\cite`; sources are
  listed inline in the introduction's References subsection.

Suspected errors in the official slides are corrected in place and documented in
`%`-comments at the relevant spot.

## Build

Build from the folder root:

```bash
latexmk main.tex
```

`latexmk` runs pdflatex as many times as needed. The compiled PDF is named
`bpm-notes.pdf`; the LaTeX auxiliaries (`.aux`, `.log`, `.toc`, `.bcf`, `.bbl`, …)
land in the folder root alongside it and are git-ignored (listed in
`.gitignore`). A `.latexmkrc` in the folder sets this up. To do it by hand
instead:

```bash
pdflatex -jobname=bpm-notes main && pdflatex -jobname=bpm-notes main
```

The second pass resolves the table of contents and cross-references. Requires a
standard TeX Live installation. Alternatively, upload the folder to
[Overleaf](https://www.overleaf.com) (New Project → Upload Project), set
`main.tex` as the main document, and compile.

## Credits

Written by **Francesco Secoli**, revised with the help of
[Claude Code](https://claude.com/claude-code): the slide decks were transcribed
and refined into LaTeX, then reworked into standalone notes and verified
slide-by-slide against the official PDFs. Based on the *Business Process
Modeling* course (a.y. 2025/26) taught by Roberto Bruni and Andrea Vandin,
University of Pisa. Contributions welcome: open an issue or a pull request.

## Contents

The notes are twenty-five sections plus three appendices, in reading order:

| # | Section | Topics |
|---|---------|--------|
| 1 | Introduction | What business processes and BPM are, modelling, tastes of BPMN and process mining, and why formal proofs matter (Euler's theorem) |
| 2 | Business Processes | Terminology, products and specialization, process orientation, organizational structures, actors/principals/contractors, cases and procedures |
| 3 | Visual notation | Modelling objectives, the BPM lifecycle, BPMN vs `.bpmn`, tasks and links, control-flow patterns, ambiguity and disambiguation, an insurance-claim example |
| 4 | Petri nets basics | Places, transitions, tokens, arcs, the token game, workflow nets, WoPeD, syntactic sugar for split/join, subprocesses, control-flow patterns, triggers |
| 5 | Process Mining | The mining framework; cases, events, attributes; discovery, conformance, enhancement; quality criteria; the α-algorithm (ordering relations, footprint matrix); noise and limitations |
| 6 | Why process mining: purpose, goals, and requirements | Functional goals, from question to insight, prerequisites in data/tools/knowledge, when process mining makes sense |
| 7 | Orchestration and collaboration | Event-driven process chains (EPC), `.epml`, orchestration, collaboration, choreography, compatibility |
| 8 | EPC and BPMN | EPC requirements, guidelines, sample diagrams and semantics, decorated EPC, BPMN swimlanes/flow objects/connecting objects, typical patterns, lanes and sub-processes |
| 9 | Other BPMN features | Artefacts, task types and activity markers, typed catching/throwing events, message passing, deferred choice, data objects and stores, call activities, error events, choreographies |
| 10 | From Automata to Nets | Finite automata and DFAs, reshaping automata into nets, multisets, the formal definition of Petri nets, firing sequences |
| 11 | Occurrence graphs | Reachability graphs, boundedness, coverability |
| 12 | Liveness | Live and dead nodes, deadlock-freedom, the lattice of implications, the four-property checklist |
| 13 | Incidence matrices | Vectors and matrices for nets, the incidence matrix, Parikh vectors, the marking equation, monotonicity |
| 14 | Analysis of Workflow Nets | Workflow nets structurally, behavioural pathologies, the language of a net, soundness, the auxiliary net N*, strong connectedness, a worked repair-service example |
| 15 | Sound by construction | Composition by refinement, building blocks, refinement and abstraction, generalised substitution |
| 16 | Invariants | S-invariants and T-invariants and the system properties they certify, strong connectedness via invariants |
| 17 | S-systems and T-systems | S-systems and T-systems: definitions and their liveness/boundedness properties |
| 18 | EPC analysis | The translation pipeline, straight translation with relaxed soundness, simplified EPCs and free-choice nets, decorated EPCs |
| 19 | BPMN analysis | The Dijkman–Dumas–Ouyang translation and its preprocessing macros |
| 20 | Free-choice nets | Stable sets of markings, siphons, traps, NP-completeness of liveness, the Rank Theorem for liveness and boundedness |
| 21 | P and NP problems | P vs NP and NP-completeness, the SAT decision problem |
| 22 | Workflow modules | Workflow modules, workflow systems, weak soundness |
| 23 | Conformance checking | Four models with naïve fitness, token replay (missing and remaining tokens), diagnostics and drill-down, comparing footprints |
| 24 | Quantitative analysis | Cycle-time analysis, theoretical cycle time and efficiency, Little's law, cost analysis |
| 25 | Diagnosis for workflow nets | S-coverability, well-structuredness, error / non-live / unbounded sequences, practice with WoPeD |
| A | BPM Cheat Sheets | Definitions, properties, general results, and an analysis summary table |
| B | Process Mining hands-on with Disco | Guided walkthrough of process mining with the Disco tool |
| C | Worked figures | Nets to draw at the exam: soundness, liveness/boundedness, PT/TP handles, S/T-nets and invariants, siphons and traps, the short-circuit N* |
