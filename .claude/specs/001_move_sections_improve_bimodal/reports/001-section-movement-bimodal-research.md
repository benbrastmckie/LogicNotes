# Section Movement and Bimodal Logic Research Report

## Metadata
- **Date**: 2025-12-02
- **Agent**: research-specialist
- **Topic**: Move sec:Cartesian and sec:Indeterminacy sections to additional.tex and improve sec:Bimodal following app:TaskSemantics construction
- **Report Type**: codebase analysis
- **Complexity**: 3

## Executive Summary

This research analyzes two primary tasks: (1) moving sec:Cartesian (lines 1108-1167) and sec:Indeterminacy (lines 1039-1103) sections from LogicNotes.tex to additional/additional.tex, and (2) improving sec:Bimodal to follow the task semantics construction from app:TaskSemantics in possible_worlds.tex (lines 1826-2019). The current bimodal section uses informal natural language motivation while the target uses rigorous mathematical definitions including frames with task relations, world histories as functions, and formal proofs. Key differences include: parameterized task relations with nullity/compositionality constraints, world histories defined as functions τ: X → W with convexity requirements, and systematic proof construction using time-shift lemmas.

## Findings

### Current State Analysis

#### Sections to Move

**sec:Cartesian** (LogicNotes.tex:1108-1167):
- Title: "Propositional Bimodal Logic: Cartesian Semantics"
- Located at lines 1108-1141 (definitions), 1145-1167 (problem set)
- Defines Cartesian frames as $\C = \tuple{W, R, T, <}$ combining modal frame $\tuple{W, R}$ and temporal frame $\tuple{T, <}$
- Interpretation function: $\I : \SL \to \wp(W \times T)$
- Models evaluated at pairs $\tuple{w, x}$ where $w \in W$ (world) and $x \in T$ (time)
- Includes two modal operators: $\boxtimes$ (universal over $W \times T$) and $\Box$ (universal over $W$ at fixed time)
- Problem set tests understanding of operator interactions and frame constraints

**sec:Indeterminacy** (LogicNotes.tex:1039-1103):
- Title: "Propositional Tense Logic: Indeterminacy"
- Located at lines 1039-1079 (definitions), 1084-1103 (problem set)
- Introduces branching time semantics with histories
- Key concepts: subframes, histories as maximal total subframes, inevitability operator $\Inevitably$
- History set notation: $H_\T$ for all histories, $H_\T^x$ for histories through time $x$
- Models evaluated at $\tuple{\M, \T_i, x}$ where $\T_i$ is a history and $x$ is a time
- Semantic clause: $\M, \T_i, x \vDash \Inevitably \metaA$ iff $\M, \T_j, x \vDash \metaA$ for all $\T_j \in H_\T^x$

**Target File** (additional/additional.tex):
- Currently empty (0 bytes)
- Located at /home/benjamin/Documents/Philosophy/Teaching/LogicNotes/additional/additional.tex
- Ready to receive content

#### Current sec:Bimodal Structure

**sec:Bimodal Overview** (LogicNotes.tex:1527-1619+):
- Current location: Lines 1527+ with sections:
  - "Bimodal Logic: Tense and Modality" (1527-1537): Natural language motivation
  - "TM Logic: Syntax" (1539-1580): Language definition with operators
  - "TM Logic: Axiomatic System" (1582-1619+): Proof system with S5 modal + linear temporal axioms

**Current Approach**:
- Uses informal natural language to motivate bimodal logic (lines 1529-1535)
- Presents axiomatic proof system first (TM system with axioms and rules)
- Modal logic is S5 (reflexive, transitive, symmetric)
- Temporal logic is linear and transitive
- Interaction axioms: MF ($\Box\metaA \rightarrow \Box\Future\metaA$) and TF ($\Box\metaA \rightarrow \Future\Box\metaA$)

### Source Material Analysis

#### Task Semantics Construction (possible_worlds.tex:1826-2019)

**Definition Structure** (formal numbered definitions):

1. **Language Definition** (def:BL-language, line 1831):
   - $\BL \coloneq \tuple{\SL,\bot,\rightarrow,\Box,\Past,\Future}$
   - $\SL \coloneq \set{p_i: i\in \N}$ (sentence letters)

2. **Frame Definition** (def:frame, line 1835):
   - $\F = \tuple{W, \T, \Rightarrow}$ consisting of:
     - $W$: nonempty set of world states
     - $\T = \tuple{T, +, \leq}$: totally ordered abelian group (temporal order)
     - $\Rightarrow$: parameterized task relation satisfying:
       - **Nullity**: $w \Rightarrow_0 w$
       - **Compositionality**: If $w \Rightarrow_x u$ and $u \Rightarrow_y v$, then $w \Rightarrow_{x+y} v$

3. **World History Definition** (def:world-history, line 1849):
   - Function $\tau : X \to W$ where:
     - $X \subseteq T$ is convex
     - $\tau(x) \Rightarrow_y \tau(x+y)$ for all $x, y \in T$ with $x, x+y \in X$
   - $H_{\F}$ denotes all world histories over frame $\F$

4. **Model Definition** (def:BL-model, line 1853):
   - $\M = \tuple{W, \T, \Rightarrow, \vert{\cdot}}$ where:
     - $\F = \tuple{W, \T, \Rightarrow}$ is a frame
     - $\vert{p_i} \subseteq W$ for each sentence letter

5. **Semantics Definition** (def:BL-semantics, line 1857):
   - Truth at $\tuple{\M, \tau, x}$ where $\tau \in H_{\F}$ and $x \in T$:
     - $(p_i)$: $\M,\tau,x \vDash p_i$ iff $x \in \dom{\tau}$ and $\tau(x) \in |p_i|$
     - $(\bot)$: $\M,\tau,x \nvDash \bot$
     - $(\rightarrow)$: $\M,\tau,x \vDash \varphi \rightarrow \psi$ iff $\M,\tau,x \nvDash \varphi$ or $\M,\tau,x \vDash \psi$
     - $(\Box)$: $\M,\tau,x \vDash \Box \varphi$ iff $\M,\sigma,x \vDash \varphi$ for all $\sigma \in H_{\F}$
     - $(\Past)$: $\M,\tau,x \vDash \Past \varphi$ iff $\M,\tau,y \vDash \varphi$ for all $y < x$
     - $(\Future)$: $\M,\tau,x \vDash \Future \varphi$ iff $\M,\tau,y \vDash \varphi$ for all $x < y$

**Advanced Theoretical Development**:

6. **Time-Shift Histories** (def:time-shift-histories, line 1872):
   - $\tau \approx_y^x \sigma$ witnessed by order automorphism $\bar{a} : T \to T$ where:
     - $y = \bar{a}(x)$
     - $\dom{\sigma} = \bar{a}^{-1}(\dom{\tau})$
     - $\sigma(z) = \tau(\bar{a}(z))$ for all $z \in \dom{\sigma}$

7. **Existence Theorem** (app:auto_existence, line 1879):
   - For any frame, history $\tau$, and times $x, y$, there exists $\sigma$ where $\tau \approx_y^x \sigma$ via $\bar{a}(z) = z - x + y$
   - Proof establishes: bijection, order preservation, convexity, task relation preservation

8. **Preservation Theorem** (lem:history-time-shift-preservation, line 1913):
   - $\M,\tau,y \vDash \varphi$ iff $\M,\sigma,x \vDash \varphi$ when $\tau \approx_y^x \sigma$
   - Proof by induction on formula complexity

9. **Validity Theorem** (app:valid, line 1984):
   - Proves $\Box \varphi \rightarrow \always \varphi$ and $\sometimes \varphi \rightarrow \Diamond \varphi$ are valid
   - Uses time-shift lemmas to show necessity implies temporal persistence

### Target Construction Details

#### Key Structural Differences

**Frame Structure**:
- **Current**: Separate modal and temporal frames combined
- **Target**: Unified frame with parameterized task relation $\Rightarrow$ connecting world states across time intervals
- **Significance**: Task relation captures "what can be accomplished in time interval $x$" rather than arbitrary accessibility

**World Histories**:
- **Current**: Implicit (evaluation at world-time pairs)
- **Target**: Explicit functions $\tau : X \to W$ with convexity and task coherence constraints
- **Significance**: World histories are first-class semantic objects, enabling reasoning about entire trajectories

**Modal Operator Semantics**:
- **Current**: $\Box$ ranges over worlds (standard Kripke)
- **Target**: $\Box$ ranges over all possible world histories at a fixed time
- **Significance**: Necessity becomes "true at this time in all possible ways the world could unfold"

**Temporal Domain**:
- **Current**: Generic temporal order $\tuple{T, <}$
- **Target**: Abelian group $\tuple{T, +, \leq}$ with interval arithmetic
- **Significance**: Enables time-shift operations and interval-based reasoning

**Proof Strategy**:
- **Current**: Axiomatic system with inference rules
- **Target**: Semantic proofs using mathematical structures (automorphisms, induction, convexity)
- **Pedagogical**: Target shows *why* principles hold, not just *that* they are provable

#### Mathematical Prerequisites

To implement the target construction, the following concepts must be explained:

1. **Convex Sets**: $X \subseteq T$ is convex if $x_1, x_2 \in X$ and $x_1 \leq z \leq x_2$ implies $z \in X$
2. **Abelian Groups**: $(T, +, \leq)$ with identity, inverses, associativity, commutativity, and order compatibility
3. **Order Automorphisms**: Bijections preserving order relations
4. **Domain of Functions**: $\dom{\tau} = \set{x : \tau(x) \text{ is defined}}$ for partial functions
5. **Structural Induction**: Proof technique on formula complexity

## Recommendations

### 1. Section Movement Strategy

**Approach**: Extract and relocate sections cleanly with proper formatting

**Steps**:
1. Extract sec:Cartesian (LogicNotes.tex:1108-1167) including both definition section and problem set
2. Extract sec:Indeterminacy (LogicNotes.tex:1039-1103) including both definition section and problem set
3. Create proper structure in additional/additional.tex with:
   - Document preamble if needed (or ensure it's included via \input in main file)
   - Proper section breaks and formatting
   - Preserve all LaTeX macros and custom commands used in these sections
4. Remove sections from LogicNotes.tex cleanly without leaving orphaned references
5. Add \input{additional/additional.tex} to LogicNotes.tex if not already present

**Rationale**: These sections represent alternative semantic approaches (Cartesian product semantics, branching time with indeterminacy) that are supplementary to the main narrative. Moving them to additional.tex keeps the main document focused while preserving valuable content.

### 2. Bimodal Section Reconstruction Strategy

**Approach**: Replace current informal+axiomatic presentation with rigorous semantic construction following app:TaskSemantics

**High-Level Plan**:

**Phase 1: Language and Syntax** (minimal changes)
- Keep language definition $\BL = \tuple{\SL,\bot,\rightarrow,\Box,\Past,\Future}$ (currently at lines 1542-1552)
- Keep well-formed sentence inductive definition (currently at lines 1548-1552)
- Keep abbreviations for $\Diamond$, $\past$, $\future$, $\always$, $\sometimes$ (currently at lines 1554-1562)

**Phase 2: Semantic Foundations** (major additions)
- **Replace** natural language motivation (lines 1529-1535) with formal frame definition
- Add Definition: Frame structure $\F = \tuple{W, \T, \Rightarrow}$ with:
  - World states $W$ (explain as "snapshots of what's true at an instant")
  - Temporal order $\T = \tuple{T, +, \leq}$ (explain abelian group structure)
  - Task relation $\Rightarrow$ with Nullity and Compositionality constraints
- Add Definition: World histories as functions $\tau : X \to W$
  - Explain convexity requirement (no temporal gaps)
  - Explain task coherence: $\tau(x) \Rightarrow_y \tau(x+y)$ (world states must be reachable via tasks)
- Add Definition: Models $\M = \tuple{W, \T, \Rightarrow, \vert{\cdot}}$
- Add Definition: Truth conditions (semantic clauses for each operator)
  - Emphasize: $\Box$ quantifies over all world histories at fixed time
  - Emphasize: $\Past/\Future$ stay within a single world history

**Phase 3: Mathematical Development** (new advanced content)
- Add Definition: Time-shift relation $\tau \approx_y^x \sigma$
- Add Theorem: Existence of time-shifted histories (with proof or proof sketch)
- Add Lemma: Truth preservation under time-shifts (with proof or proof sketch)
- Add Theorem: Validity of $\Box \varphi \rightarrow \always \varphi$ (semantic proof)

**Phase 4: Problem Sets** (adapt existing)
- Keep or adapt current problem set questions to test understanding of:
  - Frame properties (nullity, compositionality)
  - World history construction
  - Semantic evaluation at $\tuple{\M, \tau, x}$
  - Validity vs invalidity using countermodels

**Phase 5: Axiomatic System** (move to appendix or later section)
- **Option A**: Keep axiomatic system but reframe as "Proof Theory" section after semantics
- **Option B**: Move axiomatic system to appendix as alternative approach
- **Rationale**: Pedagogy works better when students see *why* principles are true (semantics) before learning *how* to derive them (proof theory)

### 3. Notation and Macro Consistency

**Action Items**:
1. Check that all macros used in app:TaskSemantics are defined in LogicNotes.tex:
   - $\BL$ (bimodal language)
   - $\F$ (frame)
   - $\Rightarrow$ (task relation with subscripts)
   - $H_{\F}$ (world history set)
   - $\dom{\tau}$ (domain of history function)
   - $\vert{p_i}$ (interpretation of sentence letters)
2. Verify proof environments (Ddef, Lthm, Tthm, proof) are available or need to be adapted
3. Ensure tikzpicture package is loaded if including diagrams (possible_worlds.tex:2026-2067 shows countermodel diagram)

### 4. Pedagogical Enhancements

**Additions to Consider**:
1. **Examples**: Add simple concrete examples of frames, world histories, and model evaluation
2. **Intuition**: Explain task relation as "what tasks can accomplish" (e.g., physical constraints, causal processes)
3. **Diagrams**: Include visual representations of world histories (as in possible_worlds.tex:2026-2067)
4. **Worked Problems**: Show step-by-step evaluation of formulas at specific model points
5. **Comparison**: Explicitly contrast with Cartesian semantics to show why world histories are needed

### 5. File Organization

**Recommended Structure**:
```
LogicNotes.tex
├── [existing content through tense logic]
├── Bimodal Logic: Task Semantics (NEW version following app:TaskSemantics)
│   ├── Language and Syntax
│   ├── Semantic Foundations (frames, histories, models)
│   ├── Mathematical Development (time-shifts, theorems)
│   ├── Problem Set: Semantics
│   └── [Optional: Axiomatic System or reference to appendix]
├── [remaining content]
└── [at end] \input{additional/additional.tex}

additional/additional.tex
├── Propositional Bimodal Logic: Cartesian Semantics
│   ├── Definitions
│   └── Problem Set
└── Propositional Tense Logic: Indeterminacy
    ├── Definitions
    └── Problem Set
```

## References

### Primary Source Files

- **LogicNotes.tex**: /home/benjamin/Documents/Philosophy/Teaching/LogicNotes/LogicNotes.tex
  - sec:Indeterminacy: lines 1039-1103
  - sec:Cartesian: lines 1108-1167
  - sec:Bimodal (current): lines 1527-1619+

- **possible_worlds.tex**: /home/benjamin/Documents/Philosophy/Papers/PossibleWorlds/JPL/possible_worlds.tex
  - app:TaskSemantics: lines 1826-2114
  - def:BL-language: line 1831
  - def:frame: line 1835
  - def:world-history: line 1849
  - def:BL-model: line 1853
  - def:BL-semantics: line 1857
  - def:time-shift-histories: line 1872
  - Theorem (app:auto_existence): line 1879
  - Lemma (lem:history-time-shift-preservation): line 1913
  - Theorem (app:valid): line 1984
  - Theorem (app:not-dense): line 2012
  - Theorem (app:dense): line 2083

- **additional.tex**: /home/benjamin/Documents/Philosophy/Teaching/LogicNotes/additional/additional.tex
  - Current status: empty file (0 bytes)
  - Target: receive sec:Cartesian and sec:Indeterminacy content

### Key Structural Elements Analyzed

- Cartesian frame definitions: LogicNotes.tex:1126-1128
- Cartesian semantics: LogicNotes.tex:1129-1139
- Indeterminacy semantics: LogicNotes.tex:1061-1070
- Current bimodal motivation: LogicNotes.tex:1529-1535
- Current TM axioms: LogicNotes.tex:1587-1618
- Task relation constraints: possible_worlds.tex:1843-1845
- World history definition: possible_worlds.tex:1849-1851
- Semantic clauses comparison: LogicNotes.tex:1129-1139 vs possible_worlds.tex:1860-1866
- Time-shift proof technique: possible_worlds.tex:1883-1980

### Mathematical Concepts Required

- Abelian groups with order: possible_worlds.tex:1839
- Convexity of temporal sets: possible_worlds.tex:1850
- Order automorphisms: possible_worlds.tex:1873, 1887-1889
- Structural induction: possible_worlds.tex:1918-1980
- Parameterized relations: possible_worlds.tex:1840-1845
