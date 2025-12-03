# TM Logic System Integration Implementation Plan

## Metadata
- **Date**: 2025-12-02
- **Feature**: Integrate TM bimodal logic with task semantics and proof system into LogicNotes
- **Scope**: Add TM logic system (syntax, axiomatic proof system, task semantics, soundness/completeness metatheory) to LogicNotes.tex following existing pedagogical style and notation conventions
- **Estimated Phases**: 6
- **Estimated Hours**: 18-24 hours
- **Complexity Score**: 142 (10 base + 30 tasks/2 + 15 files*3 + 7 integrations*5)
- **Structure Level**: 0 (single file, may expand with /expand if needed)
- **Standards File**: /home/benjamin/Documents/Philosophy/Teaching/LogicNotes/CLAUDE.md
- **Status**: [COMPLETE]
- **Research Reports**:
  - [Task Semantics and TM Proof System Research](../reports/001-task-semantics-tm-system-research.md)

## Overview

This plan integrates the TM (Logic of Tense and Modality) bimodal logic system from possible_worlds.tex into LogicNotes.tex. TM combines S5 modal logic with tense logic, featuring an innovative "task semantics" framework that constructs possible worlds from world states, tasks, and times. The integration requires:

1. Defining new LaTeX commands in notation.sty for TM system notation
2. Creating new sections in LogicNotes.tex following existing pedagogical structure (definition → theorem → problem set pattern)
3. Adapting proof presentation style to match existing Hilbert and Fitch proof systems
4. Including complete syntax, axiomatic proof system, task semantics, and metatheory (soundness/completeness)

The source material (possible_worlds.tex lines 1018-2684) provides comprehensive treatment including axioms (MP, MK, MT, M4, MB, MF, TD, TK, TL, T4, TA, TF), perpetuity principles (P1-P22), task semantic framework (frames, world histories, models, truth conditions), and complete soundness/completeness proofs.

## Research Summary

Key findings from the research report:

**TM Logic Structure**: Bimodal language BL = ⟨SL, ⊥, →, □, Past, Future⟩ with 12 axioms/rules combining S5 modal logic (MK, MT, M4, MB) with tense logic (TD, TK, TL, T4, TA) and bimodal interaction axioms (MF, TF) that ensure perpetuity principles P1-P6.

**Task Semantics Innovation**: Evaluates formulas at world histories τ (functions from times to world states) constrained by parameterized task relation ⇒ satisfying nullity and compositionality, rather than primitive possible worlds. Temporal operators quantify over times within same history; modal operators quantify over all histories at fixed time.

**LogicNotes Style**: Sections use {\sc Topic: Subtopic} format with enumerate environments (leftmargin=1.2in), bold labels [\bf Term:], Hilbert proof environment with \from{Justification}{Formula}, and Problem Set sections with [\bf Category:] labels.

**Command Integration**: notation.sty already has tense operators (\past, \Past, \future, \Future, \always, \sometimes) and modal logic commands (\ML, \MLproves, etc.). Need to add TM-specific commands following existing pattern (\TML, \TMproves, \TMmodels, etc.) and task semantics notation (\taskrel, \worldhist, etc.).

**Pedagogical Adaptation**: Full completeness proofs too advanced for introductory notes; present soundness with representative cases, state completeness without canonical model construction, focus on examples and intuitions, create graduated problem sets (basic syntax → intermediate derivations → advanced metalogic).

## Success Criteria

- [ ] All TM command definitions added to notation.sty with no namespace conflicts
- [ ] TM logic sections compile successfully within LogicNotes.tex
- [ ] Six new sections added following existing {\sc Topic: Subtopic} format
- [ ] All 12 TM axioms/rules documented with clear explanations
- [ ] Perpetuity principles P1-P6 included with complete proofs
- [ ] Task semantics framework (frames, histories, models, truth) fully defined
- [ ] At least 3 complete Hilbert-style proof examples in \begin{hilbert} environment
- [ ] Problem sets created for each section with graduated difficulty
- [ ] Soundness theorem stated with proof sketch for representative cases
- [ ] Completeness theorem stated with significance discussion (no full proof)
- [ ] All mathematical notation renders correctly matching source paper
- [ ] Cross-references to existing modal logic sections work properly
- [ ] No compilation errors or warnings in full LogicNotes.tex document

## Technical Design

### Architecture Overview

**File Structure**:
```
LogicNotes/
├── LogicNotes.tex (main document - add 6 new sections ~15-20 pages)
└── assets/
    └── notation.sty (add ~25 new TM commands)
```

**Section Organization** (to be added to LogicNotes.tex after existing modal logic sections ~line 658):

1. **Bimodal Logic: Motivation** (~1 page): Natural language perpetuity intuitions, limitations of separate temporal/modal systems
2. **TM Logic: Syntax** (~2 pages): Language definition, well-formedness, abbreviations (△, ▽), problem set
3. **TM Logic: Axiomatic System** (~4 pages): 12 axioms/rules with explanations, P1-P6 derivations, problem set
4. **TM Logic: Task Semantics** (~5 pages): Frames, world histories, models, truth conditions, validity examples, problem set
5. **TM Logic: Metatheory** (~2-3 pages): Soundness theorem (proof sketch), completeness theorem (statement only), problem set
6. **TM Logic: Extensions** (~2 pages): Frame constraints (density, discreteness), TM^D system, Next/Previous operators, problem set

**Command Namespace Strategy**:
- Use `\TML` for TM language (avoid conflict with `\TL` = tensed language)
- Use `\Tor` for temporal order structure (avoid conflict with `\T` = modal system T)
- Follow existing pattern: `\TMproves`, `\TMmodels`, `\TMequiv`, `\TMAxioms`, `\TMRules`, `\TMSystem`, `\TMLogic`
- Add task semantics: `\taskrel` (⇒), `\worldhist` (τ), `\worldhistset` (H), `\worldstateset` (W)

**Integration Points**:
1. **With existing modal logic** (lines 403-658): Cross-reference TM modal fragment to S5 system
2. **With Hilbert proof system** (lines 323-361): Use same \begin{hilbert} environment and \from{} command
3. **With proof_styles.sty**: Verify \aref{} command exists for axiom references (or add if missing)
4. **With notation.sty tense operators**: Verify \always, \sometimes, \past, \Past, \future, \Future render correctly

### Key Technical Decisions

**Decision 1: Single File vs Multi-File Structure**
- Choice: Start with single file (Level 0 structure)
- Rationale: Complexity score 142 is borderline (50-200 suggests Tier 2), but pedagogical content benefits from integrated presentation; can expand later with /expand if sections become unwieldy
- Risk: May need to split if any section exceeds 3-4 pages of dense content

**Decision 2: Proof Depth**
- Choice: Complete proofs for P1-P6, proof sketches for soundness, statement-only for completeness
- Rationale: Introductory notes should focus on understanding perpetuity principles (P1-P6 proofs manageable); soundness demonstrates technique; completeness too technical for target audience
- Alternative considered: Full completeness proof → rejected as pedagogically excessive

**Decision 3: Task Semantics Presentation**
- Choice: Frame definition → World history concept → Models → Truth conditions → Examples
- Rationale: Builds from familiar Kripke semantics (frames) to novel task relation, then shows how histories constrain modal/temporal evaluation
- Add: Diagrams showing world histories at different times (ASCII art or TikZ if time permits)

**Decision 4: Problem Set Scope**
- Choice: 3-5 problems per section, graduated difficulty (basic → intermediate → advanced)
- Rationale: Matches existing problem set density in LogicNotes; ensures students practice each concept level
- Examples: Syntax (well-formedness), Derivation (prove P9-P13), Semantics (evaluate in models), Metatheory (simple properties)

## Implementation Phases

### Phase 1: Command Definitions and Testing [COMPLETE]
dependencies: []

**Objective**: Add all TM system commands to notation.sty and verify they compile without conflicts or rendering errors.

**Complexity**: Medium

**Tasks**:
- [x] Add core TM system commands to notation.sty after line 178 (file: /home/benjamin/Documents/Philosophy/Teaching/LogicNotes/assets/notation.sty)
  - [x] Define `\TML`, `\TMproves`, `\TMmodels`, `\TMequiv`, `\TMAxioms`, `\TMRules`, `\TMSystem`, `\TMLogic`
  - [x] Define `\TMD` for TM with density axiom
- [x] Add task semantics commands after modal systems section
  - [x] Define `\taskrel` (⇒), `\Tor` (temporal order), `\taskframe`, `\taskmodel`
  - [x] Define `\worldhist` (τ), `\worldhistset` (H), `\worldstateset` (W)
- [x] Verify existing tense operators render correctly
  - [x] Test `\always` and `\sometimes` with triangle symbols
  - [x] Test `\past`, `\Past`, `\future`, `\Future` with superscript P/F
- [x] Check for namespace conflicts
  - [x] Verify `\TML` doesn't conflict with `\TL` (tensed language)
  - [x] Verify `\Tor` doesn't conflict with `\T` (modal system T)
  - [x] Grep for all new command names in existing notation.sty
- [x] Create minimal test document to verify all commands compile
  - [x] Include all new TM commands in test equations
  - [x] Compile and check for LaTeX errors or warnings
  - [x] Verify symbols render as expected (no missing glyphs)
- [x] Check if `\aref{}` command exists in proof_styles.sty for axiom references
  - [x] If missing, add simple definition: `\newcommand{\aref}[1]{\textsc{#1}}`

**Testing**:
```bash
# Test compilation of notation.sty with new commands
cd /home/benjamin/Documents/Philosophy/Teaching/LogicNotes
pdflatex -interaction=nonstopmode LogicNotes.tex 2>&1 | grep -i "error\|warning"

# Check for undefined commands
grep "Undefined control sequence" LogicNotes.log

# Verify no namespace conflicts
cd assets
grep -E "\\\\(TML|TMproves|TMmodels|Tor|taskrel|worldhist)" notation.sty
```

**Expected Duration**: 2-3 hours

### Phase 2: Motivation and Syntax Sections [COMPLETE]
dependencies: [1]

**Objective**: Create first two TM sections (Motivation and Syntax) following LogicNotes.tex pedagogical structure.

**Complexity**: Low-Medium

**Tasks**:
- [x] Add "Bimodal Logic: Motivation" section after line 658 in LogicNotes.tex
  - [x] Create section heading: `\section*{\sc Bimodal Logic: Tense and Modality}`
  - [x] Write motivation (~1 page) explaining need to combine tense and modal operators
  - [x] Introduce perpetuity intuitions informally (necessity implies always, sometimes implies possibility)
  - [x] Show inadequacy of separate temporal and modal logics with examples
- [x] Add "TM Logic: Syntax" section
  - [x] Create section heading: `\section*{\sc TM Logic: Syntax}`
  - [x] Define TM language using `\begin{enumerate}[leftmargin=1.2in]` environment
  - [x] Item `[\bf Language:]` Define BL = ⟨SL, ⊥, →, □, Past, Future⟩
  - [x] Item `[\bf Sentence Letters:]` Define SL = {p_i | i∈ℕ}
  - [x] Item `[\bf Well-Formed Sentences:]` φ ::= p_i | ⊥ | φ → φ | □φ | Past φ | Future φ
  - [x] Item `[\bf Abbreviations:]` Define △φ := Past φ ∧ φ ∧ Future φ (always), ▽φ := past φ ∨ φ ∨ future φ (sometimes)
  - [x] Item `[\bf Abbreviations:]` Define ◇φ := ¬□¬φ (possibility), ¬φ, φ ∨ ψ, φ ∧ ψ, φ ↔ ψ (standard)
- [x] Add "Problem Set: TM Syntax" section
  - [x] Create section heading: `\section*{\it Problem Set: TM Syntax}`
  - [x] Use `\begin{enumerate}[leftmargin=1.2in,itemsep=2pt]\small` environment
  - [x] 5-6 problems on well-formedness, abbreviation expansion, syntactic properties
  - [x] Item `[\bf Well-Formedness:]` Show which strings are/aren't well-formed
  - [x] Item `[\bf Abbreviations:]` Expand abbreviated formulas to primitive language
  - [x] Item `[\bf Complexity:]` Define and compute formula complexity function

**Testing**:
```bash
# Verify sections compile
cd /home/benjamin/Documents/Philosophy/Teaching/LogicNotes
pdflatex -interaction=nonstopmode LogicNotes.tex

# Check page count increase (should be +2-3 pages)
pdfinfo LogicNotes.pdf | grep Pages

# Verify all TM commands used in sections render correctly
grep -o "\\\\TML\|\\\\always\|\\\\sometimes" LogicNotes.tex | wc -l
```

**Expected Duration**: 3-4 hours

### Phase 3: Axiomatic System and Perpetuity Principles [COMPLETE]
dependencies: [2]

**Objective**: Add TM axiomatic proof system with all 12 axioms/rules and complete proofs of perpetuity principles P1-P6.

**Complexity**: High

**Tasks**:
- [x] Add "TM Logic: Axiomatic System" section to LogicNotes.tex
  - [x] Create section heading: `\section*{\sc TM Logic: Axiomatic System}`
  - [x] Define TM proof system using `\begin{enumerate}[leftmargin=1.2in]` environment
  - [x] Item `[\bf TM System:]` Introduce as smallest extension of PL closed under axiom/rule schemata
- [x] Document all 12 axioms and rules with explanations
  - [x] Modal axioms/rules: MP, MK, MT, M4, MB (with S5 explanation)
  - [x] Temporal axioms/rules: TD, TK, TL, T4, TA (with linearity/transitivity explanation)
  - [x] Bimodal interaction: MF, TF (with perpetuity connection explanation)
  - [x] Use `\begin{enumerate}[leftmargin=.5in,labelsep=.15in,itemsep=.075in]` with `\begin{multicols}{2}` for compact layout
  - [x] Use `\aitem{MK}` labels (or `\item[\bf MK]` if \aitem unavailable)
- [x] State perpetuity principles P1-P6
  - [x] P1: □φ → △φ (necessity implies always)
  - [x] P2: ▽φ → ◇φ (sometimes implies possibility)
  - [x] P3: □φ → □△φ (necessity implies necessary always)
  - [x] P4: ◇▽φ → ◇φ (possible sometimes implies possible)
  - [x] P5: ◇▽φ → △◇φ (possible sometimes implies always possible)
  - [x] P6: ▽□φ → □△φ (sometimes necessary implies necessary always)
- [x] Provide complete Hilbert-style proofs for P1 and P2
  - [x] Use `\begin{hilbert}` environment with `\from{Justification}{Formula}` format
  - [x] P1 proof: MF → MT → TK → classical reasoning → P1
  - [x] P2 proof: Equivalent to P1 by classical logic and duality
- [x] Provide derivation sketches for P3-P6
  - [x] Show key steps and axiom applications
  - [x] Reference P1/P2 where applicable
  - [x] Leave some steps as exercises
- [x] Item `[\bf TM-Proof:]` Define TM-proof as finite sequence from premises/axioms/rules
- [x] Item `[\bf TM-Derivable:]` Define Γ ⊢_TM φ notation
- [x] Add "Problem Set: TM Derivations" section
  - [x] Create section heading: `\section*{\it Problem Set: TM Derivations}`
  - [x] 6-8 problems on proving theorems in TM system
  - [x] Item `[\bf Basic Derivations:]` Prove simple modal/temporal theorems
  - [x] Item `[\bf Perpetuity Theorems:]` Prove selected P9-P13 theorems from research report
  - [x] Item `[\bf Interaction Principles:]` Prove theorems involving both modal and temporal operators

**Testing**:
```bash
# Verify Hilbert proofs compile
cd /home/benjamin/Documents/Philosophy/Teaching/LogicNotes
pdflatex -interaction=nonstopmode LogicNotes.tex 2>&1 | grep -A5 "hilbert"

# Check that all 12 axiom labels appear
grep -c "\\\\aitem{M\|\\\\aitem{T" LogicNotes.tex  # Should be ≥12

# Verify P1-P6 all referenced
grep -c "\\\\aitem{P[1-6]}" LogicNotes.tex  # Should be ≥6
```

**Expected Duration**: 5-6 hours

### Phase 4: Task Semantics Framework [COMPLETE]
dependencies: [3]

**Objective**: Add complete task semantics section including frames, world histories, models, truth conditions, and validity examples.

**Complexity**: High

**Tasks**:
- [x] Add "TM Logic: Task Semantics" section to LogicNotes.tex
  - [x] Create section heading: `\section*{\sc TM Logic: Task Semantics}`
  - [x] Use `\begin{enumerate}[leftmargin=1.2in]` environment for definitions
- [x] Define task semantic frames
  - [x] Item `[\bf Frame:]` Define F = ⟨W, T, ⇒⟩ where W = world states, T = temporal order, ⇒ = task relation
  - [x] Item `[\it Nullity:]` Constraint w ⇒_0 w (every state can do null task to itself)
  - [x] Item `[\it Compositionality:]` Constraint if w ⇒_x u and u ⇒_y v, then w ⇒_{x+y} v
  - [x] Add intuitive explanation: task relation encodes possible transitions over time durations
  - [x] Use chess game or state machine as concrete example
- [x] Define world histories
  - [x] Item `[\bf World History:]` Define τ: X → W where X ⊆ T convex (no gaps)
  - [x] Item `[\it Task Consistency:]` Constraint τ(x) ⇒_y τ(x+y) for all x, y with x, x+y ∈ X
  - [x] Add intuitive explanation: history is temporally connected sequence of states respecting task constraints
  - [x] Contrast with primitive possible worlds in Kripke semantics
- [x] Define task semantic models
  - [x] Item `[\bf Model:]` Define M = ⟨W, T, ⇒, |·|⟩ where |p_i| ⊆ W for each sentence letter
  - [x] Item `[\bf Valuation:]` Interpretation function assigns truth-values to atoms at world states
- [x] Define truth conditions at model M, history τ, time x
  - [x] Atomic: M,τ,x ⊨ p_i iff x ∈ dom(τ) and τ(x) ∈ |p_i|
  - [x] Bottom: M,τ,x ⊭ ⊥
  - [x] Conditional: M,τ,x ⊨ φ → ψ iff M,τ,x ⊭ φ or M,τ,x ⊨ ψ
  - [x] Necessity: M,τ,x ⊨ □φ iff M,σ,x ⊨ φ for all histories σ
  - [x] Past: M,τ,x ⊨ Past φ iff M,τ,y ⊨ φ for all y < x
  - [x] Future: M,τ,x ⊨ Future φ iff M,τ,y ⊨ φ for all y > x
- [x] Define validity and logical consequence
  - [x] Item `[\bf Validity:]` φ valid iff M,τ,x ⊨ φ for all models M, histories τ, times x
  - [x] Item `[\bf Logical Consequence:]` Γ ⊨_TM φ iff for all M, τ, x, if M,τ,x ⊨ γ for all γ ∈ Γ, then M,τ,x ⊨ φ
- [x] Provide 2-3 worked examples
  - [x] Example 1: Simple frame with 2 world states, linear time, show truth evaluation
  - [x] Example 2: Frame validating P1 (□φ → △φ)
  - [x] Example 3: Show formula true at one history but false at another (modal evaluation)
- [x] Add "Problem Set: Task Semantics" section
  - [x] Create section heading: `\section*{\it Problem Set: Task Semantics}`
  - [x] 5-7 problems on model construction and formula evaluation
  - [x] Item `[\bf Frame Properties:]` Show frame satisfies nullity/compositionality
  - [x] Item `[\bf Truth Evaluation:]` Evaluate formulas at specific model/history/time
  - [x] Item `[\bf Validity:]` Prove or disprove validity of formulas over all task frames
  - [x] Item `[\bf Countermodels:]` Construct countermodels showing invalidity

**Testing**:
```bash
# Verify task semantics commands used correctly
cd /home/benjamin/Documents/Philosophy/Teaching/LogicNotes
grep -o "\\\\taskrel\|\\\\worldhist\|\\\\taskframe" LogicNotes.tex | wc -l  # Should be >10

# Check truth conditions all defined
grep "M,τ,x ⊨" LogicNotes.tex | wc -l  # Should be ≥6 (one per connective/operator)

# Verify compilation with semantic notation
pdflatex -interaction=nonstopmode LogicNotes.tex
```

**Expected Duration**: 5-6 hours

### Phase 5: Metatheory (Soundness and Completeness) [COMPLETE]
dependencies: [4]

**Objective**: Add metatheory section with soundness theorem (proof sketch) and completeness theorem (statement only), discussing significance.

**Complexity**: Medium

**Tasks**:
- [x] Add "TM Logic: Metatheory" section to LogicNotes.tex
  - [x] Create section heading: `\section*{\sc TM Logic: Metatheory}`
  - [x] Use `\begin{enumerate}[leftmargin=1.2in]` environment
- [x] State soundness theorem
  - [x] Item `[\bf Soundness:]` If Γ ⊢_TM φ, then Γ ⊨_TM φ
  - [x] Add intuitive explanation: every TM-derivable formula is valid over task frames
  - [x] Explain significance: TM proofs guarantee semantic truth
- [x] Provide soundness proof sketch
  - [x] Show propositional base case (PL axioms valid)
  - [x] Show S5 modal axioms valid over all task frames
  - [x] Show temporal axioms valid given linearity/transitivity/symmetry
  - [x] Show MF valid: necessity persists into future
  - [x] Show TF valid: necessity and future commute
  - [x] Show rules preserve validity (MP, MK, TK, TD)
  - [x] Use 1-2 representative cases with complete proofs, sketch others
- [x] State completeness theorem
  - [x] Item `[\bf Completeness:]` If Γ ⊨_TM φ, then Γ ⊢_TM φ
  - [x] Add intuitive explanation: every valid formula over task frames is TM-derivable
  - [x] Explain significance: TM proof system is adequate for task semantics
  - [x] Note proof strategy: canonical model construction (maximal consistent sets as world states, accessibility via consistency)
  - [x] Reference source paper (possible_worlds.tex lines 2382-2684) for full proof
  - [x] Justify omitting full proof: too technical for introductory notes, requires advanced set theory
- [x] Discuss metalogical significance
  - [x] Connection to S5 modal logic (TM modal fragment is S5)
  - [x] Connection to tense logic (TM temporal fragment extends standard tense logic)
  - [x] Decidability (inherited from S5 and tense logic decidability)
  - [x] Expressiveness (can capture perpetuity principles not derivable in separate systems)
- [x] Add "Problem Set: TM Metatheory" section
  - [x] Create section heading: `\section*{\it Problem Set: TM Metatheory}`
  - [x] 4-5 problems on simple metalogical properties
  - [x] Item `[\bf Axiom Validity:]` Show specific axiom valid over all task frames
  - [x] Item `[\bf Rule Soundness:]` Show specific rule preserves validity
  - [x] Item `[\bf Consistency:]` Prove or disprove consistency of formula sets
  - [x] Item `[\bf Decidability:]` Discuss implications of decidability result

**Testing**:
```bash
# Verify metatheory section compiles
cd /home/benjamin/Documents/Philosophy/Teaching/LogicNotes
pdflatex -interaction=nonstopmode LogicNotes.tex

# Check soundness and completeness theorems stated
grep -i "soundness\|completeness" LogicNotes.tex | wc -l  # Should be ≥4

# Verify page count (should be +2-3 pages)
pdfinfo LogicNotes.pdf | grep Pages
```

**Expected Duration**: 3-4 hours

### Phase 6: Extensions and Final Integration [COMPLETE]
dependencies: [5]

**Objective**: Add TM extensions section (density, discreteness, TM^D, Next/Previous), create final problem set, verify complete integration with existing LogicNotes material.

**Complexity**: Medium

**Tasks**:
- [x] Add "TM Logic: Extensions" section to LogicNotes.tex
  - [x] Create section heading: `\section*{\sc TM Logic: Extensions}`
  - [x] Use `\begin{enumerate}[leftmargin=1.2in]` environment
- [x] Discuss frame constraints
  - [x] Item `[\bf Dense Time:]` Axiom DN: Future φ → Future Future φ (between any two times, another time)
  - [x] Item `[\bf Discrete Time:]` Axiom Next φ → φ ∨ Next Next φ (time has immediate successors)
  - [x] Item `[\bf Complete Time:]` Convergence properties for infinite sequences
  - [x] Show how each constraint adds theorems not derivable in base TM
- [x] Define TM^D system with density
  - [x] Item `[\bf TM^D:]` TM + DN axiom
  - [x] Show TM^D theorems using density
  - [x] Discuss frame correspondence (DN ↔ dense temporal order)
- [x] Introduce additional temporal operators
  - [x] Item `[\bf Next:]` Next φ := ¬Future ¬(φ ∨ Future ⊥) (next time point)
  - [x] Item `[\bf Previous:]` Previous φ := ¬Past ¬(φ ∨ Past ⊥) (previous time point)
  - [x] Item `[\bf Since:]` φ Since ψ := Past(ψ ∧ Future φ) (φ held since ψ)
  - [x] Item `[\bf Until:]` φ Until ψ := Future(ψ ∧ Past φ) (φ holds until ψ)
  - [x] Show axiomatization for each operator
- [x] Add "Problem Set: TM Extensions" section
  - [x] Create section heading: `\section*{\it Problem Set: TM Extensions}`
  - [x] 4-6 problems on extended systems
  - [x] Item `[\bf Density:]` Prove theorems in TM^D using DN axiom
  - [x] Item `[\bf Discreteness:]` Show discrete time models and properties
  - [x] Item `[\bf Operator Definitions:]` Prove equivalences for Since/Until
  - [x] Item `[\bf Frame Correspondence:]` Show axiom-constraint correspondences
- [x] Verify integration with existing LogicNotes sections
  - [x] Check cross-references to S5 modal logic section (lines 403-658) work
  - [x] Verify Hilbert proof environment consistent throughout
  - [x] Ensure section numbering and formatting consistent
  - [x] Test all internal hyperlinks (if using hyperref package)
- [x] Final compilation and validation
  - [x] Full document compile with all 6 new TM sections
  - [x] Check for LaTeX errors, warnings, overfull/underfull boxes
  - [x] Verify total page count increase (~15-20 pages)
  - [x] Spot-check mathematical notation rendering
  - [x] Verify all new commands defined in notation.sty are used
  - [x] Confirm no undefined command errors

**Testing**:
```bash
# Full document compilation
cd /home/benjamin/Documents/Philosophy/Teaching/LogicNotes
pdflatex -interaction=nonstopmode LogicNotes.tex

# Check for errors in log
grep -i "error\|undefined" LogicNotes.log

# Verify all 6 TM sections present
grep "\\\\section\*{\\\\sc.*TM\|\\\\section\*{\\\\sc.*Bimodal" LogicNotes.tex | wc -l  # Should be ≥6

# Verify all TM commands used (none orphaned in notation.sty)
for cmd in TML TMproves TMmodels taskrel worldhist Tor; do
  echo -n "$cmd: "
  grep -c "\\\\$cmd" LogicNotes.tex
done

# Check page count increase
pdfinfo LogicNotes.pdf | grep Pages
# Should be ~15-20 pages more than before integration

# Final validation: no LaTeX errors
pdflatex -interaction=nonstopmode LogicNotes.tex
echo "Exit code: $?"  # Should be 0
```

**Expected Duration**: 2-3 hours

## Testing Strategy

### Unit Testing (Per Phase)

Each phase includes specific testing:
- **Phase 1**: Command compilation, namespace conflict checking, symbol rendering verification
- **Phase 2**: Section compilation, TM language commands usage, formatting consistency
- **Phase 3**: Hilbert proof environment, axiom labeling, perpetuity principle references
- **Phase 4**: Task semantics notation, truth condition definitions, example models
- **Phase 5**: Metatheory theorem statements, proof sketch formatting
- **Phase 6**: Extensions compilation, cross-reference checking, full integration validation

### Integration Testing

After Phase 6 completion:

```bash
# Full document compilation test
cd /home/benjamin/Documents/Philosophy/Teaching/LogicNotes
rm -f LogicNotes.aux LogicNotes.log LogicNotes.pdf  # Clean build
pdflatex -interaction=nonstopmode LogicNotes.tex
pdflatex -interaction=nonstopmode LogicNotes.tex  # Second pass for refs

# Error checking
if [ $? -eq 0 ]; then
  echo "✓ Compilation successful"
else
  echo "✗ Compilation failed"
  grep -A3 "^!" LogicNotes.log  # Show errors
  exit 1
fi

# Warning checking
WARNINGS=$(grep -c "Warning" LogicNotes.log)
echo "Warnings: $WARNINGS"
if [ $WARNINGS -gt 10 ]; then
  echo "⚠ High warning count, review log"
fi

# Command usage verification (all notation.sty TM commands used)
echo "Checking TM command usage..."
for cmd in TML TMproves TMmodels TMequiv TMAxioms TMRules TMSystem TMLogic TMD taskrel Tor worldhist; do
  COUNT=$(grep -c "\\\\$cmd" LogicNotes.tex)
  if [ $COUNT -eq 0 ]; then
    echo "⚠ Command \\$cmd defined but never used"
  else
    echo "✓ \\$cmd used $COUNT times"
  fi
done

# Cross-reference verification
echo "Checking cross-references..."
grep "Undefined control sequence" LogicNotes.log && echo "✗ Undefined commands found" || echo "✓ No undefined commands"
grep "Reference.*undefined" LogicNotes.log && echo "⚠ Undefined references" || echo "✓ All references resolved"

# Section count verification
SECTION_COUNT=$(grep -c "\\\\section\*{" LogicNotes.tex)
echo "Total sections: $SECTION_COUNT"

# Page count verification
PAGE_COUNT=$(pdfinfo LogicNotes.pdf | grep "Pages:" | awk '{print $2}')
echo "Total pages: $PAGE_COUNT"
```

### Visual Inspection Checklist

After compilation, manually verify:
- [ ] All TM symbols render correctly (□, ◇, Past, Future, △, ▽, ⇒, τ)
- [ ] Hilbert proofs are properly formatted with line numbers and justifications
- [ ] Problem sets have consistent formatting (small font, leftmargin, itemsep)
- [ ] Section headers use correct font ({\sc} or {\it} as appropriate)
- [ ] Mathematical notation is consistent with existing LogicNotes style
- [ ] No orphaned section headers (section followed immediately by new section)
- [ ] Page breaks are reasonable (no single lines orphaned)

### Correctness Validation

Mathematical content validation:
- [ ] All 12 TM axioms match source paper (possible_worlds.tex lines 1029-1044)
- [ ] Perpetuity principles P1-P6 stated correctly
- [ ] Hilbert proofs for P1-P2 are logically valid
- [ ] Task semantics definitions match research report
- [ ] Truth conditions cover all language constructs
- [ ] Soundness theorem statement is accurate
- [ ] Completeness theorem statement is accurate

## Documentation Requirements

### Internal Documentation

**notation.sty comments**: Add explanatory comments for all new TM commands
```latex
% TM Logic System Commands (added 2025-12-02)
% TM = Logic of Tense and Modality (bimodal logic combining S5 + tense logic)
% Source: possible_worlds.tex section 3.3
\newcommand{\TML}{\mathcal{L}^{\textsc{tm}}}  % TM Language
\newcommand{\TMproves}{\vdash_{\textsc{tm}}}  % TM provability
% ... (continue for all commands)

% Task Semantics Commands (added 2025-12-02)
% Task semantics evaluates formulas at world histories (functions from times to world states)
% rather than primitive possible worlds
\newcommand{\taskrel}{\Rightarrow}  % Task relation (parameterized accessibility)
\newcommand{\worldhist}{\tau}       % World history symbol
% ... (continue for all commands)
```

**LogicNotes.tex section comments**: Add comments marking new TM sections
```latex
%----------------------------------------------------------------------------------------
%   TM LOGIC SYSTEM (BIMODAL LOGIC)
%   Added: 2025-12-02
%   Source: possible_worlds.tex lines 1018-2684
%----------------------------------------------------------------------------------------

\section*{\sc Bimodal Logic: Tense and Modality}
% ... content ...
```

### Bibliography (if applicable)

If LogicNotes.tex has bibliography section, add relevant citations:
- Source paper citation (possible_worlds.tex author and venue)
- Prior, A.N. (1967). *Past, Present and Future*. Oxford University Press. (tense logic foundation)
- Montague, R. (1974). "Pragmatics". In *Formal Philosophy*. (modal temporal interaction)
- Kaplan, D. (1989). "Demonstratives". In *Themes from Kaplan*. (indexical temporal logic)

### README or Usage Notes

If LogicNotes directory has README, add note:
```markdown
## Recent Additions

### TM Logic System (2025-12-02)
Added six new sections covering TM (Logic of Tense and Modality), a bimodal logic
system combining S5 modal logic with tense logic. Includes complete syntax, axiomatic
proof system, task semantics framework, and metatheory (soundness/completeness).

- Sections: Motivation, Syntax, Axiomatic System, Task Semantics, Metatheory, Extensions
- New commands: ~25 TM-specific commands in assets/notation.sty
- Problem sets: 6 new problem set sections with graduated difficulty
- Pages added: ~15-20 pages of pedagogical content
```

## Dependencies

### External Dependencies

**LaTeX Packages** (already imported in LogicNotes.tex):
- amsmath, amssymb, mathtools (mathematical notation)
- mathabx, stmaryrd (extended math symbols)
- amsthm (theorem environments)
- lplfitch (Fitch-style proofs, not used for TM but present)
- tikz, tikz-cd (diagrams - may be used for world history visualization)

**Style Files**:
- assets/formatting.sty (imported in LogicNotes.tex)
- assets/proof_styles.sty (Hilbert environment, verify \aref command)
- assets/notation.sty (target for new TM commands)

### Internal Dependencies

**Prerequisite Sections** (must exist before TM sections):
- Propositional Logic section (lines 27-115) - defines basic logical notation
- Hilbert System section (lines 323-361) - defines Hilbert proof environment
- Modal Logic sections (lines 403-658) - provides S5 background for TM modal fragment

**Command Dependencies**:
- \tuple, \set, \corner (defined in notation.sty) - used in TM definitions
- \M, \F (defined in notation.sty as model and frame) - may conflict, check usage
- \always, \sometimes (defined in notation.sty) - used extensively in TM
- \past, \Past, \future, \Future (defined in notation.sty) - TM language primitives
- Hilbert proof commands: \from{}{} (defined in proof_styles.sty)

### Phase Dependencies

Phases must execute in order due to dependencies:
1. Phase 1 → no dependencies (command definitions independent)
2. Phase 2 → depends on Phase 1 (needs TM commands to compile syntax section)
3. Phase 3 → depends on Phase 2 (needs syntax section for axiom definitions)
4. Phase 4 → depends on Phase 3 (needs axioms for semantic validation examples)
5. Phase 5 → depends on Phase 4 (needs semantics for soundness/completeness statements)
6. Phase 6 → depends on Phase 5 (needs metatheory before extensions)

**Note**: Phases with same dependencies can run in parallel (not applicable here - linear dependency chain).

## Risk Management

### Technical Risks

**Risk 1: Namespace Conflicts**
- **Probability**: Medium
- **Impact**: High (compilation failure)
- **Mitigation**: Phase 1 includes explicit conflict checking; use \TML instead of \TL, \Tor instead of \T
- **Rollback**: Remove conflicting command, rename with different suffix

**Risk 2: Symbol Rendering Issues**
- **Probability**: Low-Medium
- **Impact**: Medium (visual quality degraded)
- **Mitigation**: Test all tense operators in Phase 1; verify \always and \sometimes triangles render correctly
- **Fallback**: Redefine symbols using simpler LaTeX constructs (e.g., \triangle instead of rotated triangle)

**Risk 3: Proof Complexity Excessive**
- **Probability**: Medium
- **Impact**: Medium (pedagogical clarity reduced)
- **Mitigation**: Limit P1-P6 proofs to 10-15 lines each; sketch P3-P6 with key steps only
- **Adjustment**: If proofs too long, move detailed steps to appendix and provide outline in main text

**Risk 4: Page Count Exceeds Estimate**
- **Probability**: Medium
- **Impact**: Low (document longer than planned but functional)
- **Mitigation**: Monitor page count after each phase; condense if approaching 25 pages
- **Alternative**: Use /expand command to split sections if any exceeds 4 pages

**Risk 5: Cross-Reference Errors**
- **Probability**: Low
- **Impact**: Medium (broken links, undefined references)
- **Mitigation**: Use explicit \label{} and \ref{} for all theorem references; test with two pdflatex passes
- **Validation**: Phase 6 includes cross-reference checking in testing script

### Content Risks

**Risk 1: Mathematical Errors in Proofs**
- **Probability**: Low
- **Impact**: High (incorrect mathematical content)
- **Mitigation**: Follow source paper (possible_worlds.tex) exactly for axioms and P1-P6 proofs; no original derivations
- **Validation**: Cross-check each proof step against source paper lines 1057-1093

**Risk 2: Inconsistent Notation**
- **Probability**: Medium
- **Impact**: Medium (student confusion)
- **Mitigation**: Use research report's notation mapping (section 10-12); follow existing LogicNotes conventions
- **Check**: Ensure △ and ▽ definitions match always/sometimes commands exactly

**Risk 3: Pedagogical Level Mismatch**
- **Probability**: Low
- **Impact**: Medium (too advanced or too simple for target audience)
- **Mitigation**: Match existing LogicNotes difficulty level; include graduated problem sets; omit canonical model construction
- **Adjustment**: Add more intuitive explanations if task semantics too abstract

### Rollback Strategies

**Per-Phase Rollback**:
- Phase 1: Remove new commands from notation.sty (lines added after 178), restore backup
- Phase 2: Remove syntax sections from LogicNotes.tex, restore to post-Phase-1 state
- Phase 3: Remove axiomatic system section, keep syntax sections
- Phase 4: Remove task semantics section, keep axioms
- Phase 5: Remove metatheory section, keep semantics
- Phase 6: Remove extensions section, keep metatheory

**Git Strategy** (if using version control):
```bash
# Commit after each phase
git add LogicNotes.tex assets/notation.sty
git commit -m "Phase N: [description]"

# Rollback if needed
git revert HEAD  # Undo last phase
```

**Backup Strategy** (if not using git):
```bash
# Before each phase
cp LogicNotes.tex LogicNotes.tex.backup.phase$(date +%Y%m%d_%H%M%S)
cp assets/notation.sty assets/notation.sty.backup.phase$(date +%Y%m%d_%H%M%S)

# Restore if needed
cp LogicNotes.tex.backup.phase20251202_140000 LogicNotes.tex
```

## Notes

### Complexity Calculation Details

```
Score = Base(feature type) + Tasks/2 + Files*3 + Integrations*5

Where:
- Base: new=10 (new TM system, not enhancing existing)
- Tasks: 30 (counted from all phase task checkboxes)
- Files: 2 (LogicNotes.tex, notation.sty)
- Integrations: 7 (S5 modal logic, Hilbert proofs, tense operators, proof_styles.sty,
                   formatting.sty, existing problem sets, notation.sty commands)

Score = 10 + 30/2 + 2*3 + 7*5
      = 10 + 15 + 6 + 35
      = 66

Tier Selection: Score 66 falls in 50-200 range → Tier 2 (phase directory)
Decision: Use Tier 1 (single file) initially with Structure Level 0
Rationale: Pedagogical content benefits from integrated presentation;
           TM sections naturally flow from motivation → syntax → semantics → metatheory
           Can expand later with /expand if sections become unwieldy (>4 pages each)
```

### Research Report Integration

This plan fully incorporates findings from research report `/home/benjamin/Documents/Philosophy/Teaching/LogicNotes/.claude/specs/000_semantics_proof_tm_integration/reports/001-task-semantics-tm-system-research.md`:

- **Section 1 (TM Logic Structure)**: Implemented in Phase 3 (axiomatic system)
- **Section 2 (Task Semantics Framework)**: Implemented in Phase 4 (task semantics)
- **Section 3 (Proof Theory)**: Implemented in Phase 5 (metatheory)
- **Section 4 (LogicNotes Structure)**: Followed throughout all phases (formatting, enumerate environments, section headers)
- **Section 5 (Notation.sty Commands)**: Implemented in Phase 1 (command definitions)
- **Section 6 (Commands Needed)**: All recommended commands added in Phase 1
- **Section 7 (Integration Strategy)**: Followed exactly (6 phases matching 6 content phases in report)
- **Section 8 (Stylistic Considerations)**: Applied to all Hilbert proofs and definitions
- **Section 9 (Technical Challenges)**: Addressed in risk management and phase task breakdowns
- **Section 10-12 (Command Compatibility)**: Verified in Phase 1 namespace checking

### Implementation Notes

**Key Insight from Research**: Task semantics innovation is that formulas are evaluated at (world history, time) pairs rather than primitive possible worlds. This allows temporal operators to quantify over times within the same history while modal operators quantify over all histories at a fixed time. This should be emphasized in Phase 4 task semantics section.

**Proof Strategy**: Following research report recommendation (Section 9, Challenge 2), complete proofs only for P1-P6 perpetuity principles. Soundness gets proof sketches for representative cases. Completeness stated without full canonical model construction (too advanced for introductory notes).

**Diagram Consideration**: Research report Section 9 Challenge 5 suggests adding diagrams for world histories. If time permits in Phase 4, create simple ASCII art or TikZ diagrams showing:
- World history τ as function from times to world states
- Multiple histories diverging at time x (modal branching)
- Single history evaluated at different times (temporal progression)

**Extension to Phase 6**: Research report Section 7 Phase 6 suggests extensions including density, discreteness, Next/Previous, Since/Until operators. Implemented in final phase for completeness, but can be considered optional if time constraints arise.

### Standards Alignment

**Code Standards**: Not applicable (LaTeX content, not code)

**Documentation Standards**:
- Add comments to notation.sty for all new commands (Phase 1)
- Add section comments to LogicNotes.tex marking TM sections (Phases 2-6)
- Update bibliography if present (Phase 6)

**Testing Standards**:
- Each phase includes specific testing commands
- Phase 6 includes comprehensive integration testing script
- Visual inspection checklist for final validation

**No Standards Divergence**: This plan aligns with existing LogicNotes structure and does not require CLAUDE.md changes. All new content follows established patterns (enumerate definitions, Hilbert proofs, problem sets).
