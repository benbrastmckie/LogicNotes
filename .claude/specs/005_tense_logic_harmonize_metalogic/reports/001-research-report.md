# Tense Logic Harmonization and Metalogic Restructuring Research Report

## Metadata
- **Date**: 2025-12-02
- **Agent**: research-specialist
- **Topic**: Harmonize tense logic definitions with possible_worlds.tex and restructure bimodal metalogic section
- **Report Type**: codebase analysis
- **Complexity**: 3

## Executive Summary

This report documents the current state of tense logic and bimodal metalogic in LogicNotes.tex versus the target state defined in possible_worlds.tex appendix. The main findings are: (1) LogicNotes.tex currently defines TK as an axiom schema (line 969) while possible_worlds.tex defines it as a rule (line 2324), (2) LogicNotes.tex contains three proof sketches in the metalogic section (lines 1304-1314) that should be converted to problem set exercises, and (3) the completeness section (lines 1318-1333) should be removed entirely. These changes will align LogicNotes.tex with the appendix structure of possible_worlds.tex and make the metalogic section more pedagogically appropriate for student problem sets.

## Findings

### 1. Current TK Definition in LogicNotes.tex

**Location**: `/home/benjamin/Documents/Philosophy/Teaching/LogicNotes/LogicNotes.tex:969`

**Current State**:
```latex
\item[\bf TK] $\Future(\metaA\rightarrow \metaB)\rightarrow(\Future \metaA\rightarrow\Future \metaB)$ (future distribution).
```

The TK axiom is listed as an axiom schema within the "Axiom Schemata" enumeration (line 967-975). This section defines TK, TL, T4, TA, and TD as temporal axioms.

**Associated References**:
- Line 983: "The TL proof system for linear tense logic includes all $\TL$ instances of the Hilbert axioms together with axioms \textbf{TK}, \textbf{TL}, \textbf{T4}, and \textbf{TA}..."
- Line 985: "...each $\metaA_i$ is either: (1) a \textit{premise} in $\MetaG$; (2) a propositional \textit{axiom}; (3) a \textbf{TL} \textit{axiom} instance..."

### 2. FN Rule in LogicNotes.tex

**Location**: `/home/benjamin/Documents/Philosophy/Teaching/LogicNotes/LogicNotes.tex:977-981`

**Current State**:
```latex
\item[\bf Future Necessitation Rule:] Consider the following metarule:
      \begin{enumerate}[leftmargin=.5in,labelsep=.15in,itemsep=.075in]
              \item[\bf FN] If $\MetaG \vdash \metaA$, then $\Future\MetaG \vdash \Future\metaA$ (future necessitation).
      \end{enumerate}
      where $\Future\MetaG = \set{\Future\metaC \mid \metaC \in \MetaG}$.
```

FN is currently defined as a separate rule distinct from TK.

### 3. Target TK Definition in possible_worlds.tex

**Location**: `/home/benjamin/Documents/Philosophy/Papers/PossibleWorlds/JPL/possible_worlds.tex:2324`

**Target State**:
```latex
\item \textbf{\aref{TK}}: If $\Gamma \vDash \varphi$, then $\Future\Gamma \vDash \Future\varphi$.
```

In the appendix (section "Proof Theory", subsection "Soundness"), TK is defined as a **rule** rather than an axiom schema. The proof (lines 2331-2332) demonstrates:

```latex
For \textbf{\aref{TK}}: Suppose $\Gamma \vDash \varphi$ and let $\M,\tau,x \vDash \Future\gamma$ for all $\gamma \in \Gamma$. By \textbf{\ref{def:BL-semantics}}, $\M,\tau,y \vDash \gamma$ for all $y > x$ and all $\gamma \in \Gamma$. Since $\Gamma \vDash \varphi$, we have $\M,\tau,y \vDash \varphi$ for all $y > x$. Therefore $\M,\tau,x \vDash \Future\varphi$ by \textbf{\ref{def:BL-semantics}}.
```

This is the exact same formulation as the FN rule in LogicNotes.tex, confirming that TK should be defined as a rule, not an axiom.

### 4. Derivability of Axiom TK from Rule TK

The axiom version $\Future(\metaA\rightarrow \metaB)\rightarrow(\Future \metaA\rightarrow\Future \metaB)$ is derivable from the rule version. This is standard in modal/tense logic: the K-axiom pattern for any modal/temporal operator is derivable from the corresponding necessitation rule plus modus ponens.

### 5. Bimodal Metalogic Section - Proofs to Remove

**Location**: `/home/benjamin/Documents/Philosophy/Teaching/LogicNotes/LogicNotes.tex:1300-1316`

**Proof Sketches Found** (lines 1302-1316):

1. **Case MP** (lines 1303-1305): Proof that modus ponens preserves validity
2. **Case MK** (lines 1307-1309): Proof that the K axiom for Box is valid
3. **Case MF** (lines 1311-1313): Proof that the bimodal axiom MF is valid

**Context**: These proofs appear within the "Soundness Proof Sketch" item (line 1300) in the "Bimodal Logic: Metatheory" section.

**Additional Text** (lines 1315-1316):
```latex
The remaining axioms (MT, M4, MB, TD, TL, T4, TA, TF) and rules are shown valid by similar arguments. The key insight is that the bimodal axioms MF and TF ensure that modal and temporal operators interact correctly across world histories and times.
```

### 6. Completeness Section to Remove

**Location**: `/home/benjamin/Documents/Philosophy/Teaching/LogicNotes/LogicNotes.tex:1318-1333`

**Section Contents**:
- Line 1318: "\item[\bf Completeness Theorem:] \textit{If $\Gamma \models_{\textsc{tm}} \metaA$, then $\Gamma \TMproves \metaA$.}"
- Lines 1320-1321: Description of completeness as adequacy
- Lines 1322-1330: Completeness proof strategy using canonical model construction
- Lines 1331-1332: Truth Lemma and final completeness argument

This entire item should be removed from the enumeration.

### 7. Metalogic Problem Set Location

**Location**: `/home/benjamin/Documents/Philosophy/Teaching/LogicNotes/LogicNotes.tex:1344-1366`

**Current Structure**:
```latex
\section*{\it Problem Set: Metatheory}

\begin{enumerate}[leftmargin=1.2in,itemsep=2pt]\small
  \item[\bf Axiom Validity:] Show that the following TM axioms are valid...
  \item[\bf Consistency:] For each of the following sets of formulas...
  \item[\bf Countermodels:] For each invalid formula...
\end{enumerate}
```

This is where the proof exercises from the soundness proof sketch should be moved. The problem set already has:
- Axiom validity problems (MT and T4)
- Consistency problems
- Countermodel problems

### 8. Pattern Comparison with possible_worlds.tex

**Appendix Structure in possible_worlds.tex**:
- Section: Appendix (line 1358)
- Subsection: Model Theory (lines 1361-1820) - definitions and theorems
- Subsection: Task Semantics (lines 1826-2006) - semantic definitions and validity proofs
- Subsection: Proof Theory (lines 2101-2258) - derivations of interaction principles
- Subsection: Soundness (lines 2260-2349) - soundness proofs for axioms and rules

**Key Observation**: The appendix in possible_worlds.tex does NOT include a completeness section. It focuses on:
1. Semantic definitions
2. Validity proofs for specific formulas
3. Proof-theoretic derivations
4. Soundness proofs

This confirms that LogicNotes.tex should remove the completeness section to match the appendix structure.

## Recommendations

### Recommendation 1: Rename FN to TK and Remove Axiom TK

**Action**: In the tense logic axiomatic system section:
1. Remove the axiom schema TK from line 969
2. Rename the "Future Necessitation Rule" (FN) at line 977 to "TK"
3. Update the rule definition to match possible_worlds.tex format if needed
4. Update all references to TK in the TL System definition (line 983) to reflect it as a rule rather than an axiom
5. Update references in proof definitions (line 985) to clarify TK is a rule

**Rationale**: This aligns LogicNotes.tex with the appendix conventions in possible_worlds.tex where TK is the standard name for the tense necessitation rule. The axiom version is derivable from the rule, so no logical content is lost.

### Recommendation 2: Move Soundness Proofs to Problem Set

**Action**: In the bimodal metalogic section:
1. Remove the proof sketches for MP, MK, and MF (lines 1302-1314)
2. Keep the soundness theorem statement and its description (lines 1296-1298)
3. Add the following exercises to "Problem Set: Metatheory" (after line 1347):
   - Prove that modus ponens preserves validity over task frames
   - Prove that the MK axiom is valid over task frames
   - Prove that the MF bimodal axiom is valid over task frames
   - (Optional) Prove validity for other axioms: MT, M4, MB, TD, TL, T4, TA, TF

**Rationale**: Converting proofs to problem set exercises is more pedagogically appropriate for teaching notes. Students learn by working through the proofs themselves rather than reading completed proofs. This matches the pattern used in other sections where metalogical results are stated and then explored through problem sets.

### Recommendation 3: Remove Completeness Section Entirely

**Action**: Remove the entire completeness section (lines 1318-1333), including:
- The completeness theorem statement
- The completeness proof strategy explanation
- The Truth Lemma description
- The final completeness argument

**Rationale**:
1. The appendix in possible_worlds.tex does not include completeness proofs
2. Completeness is significantly more complex than soundness and may be beyond the scope of teaching notes
3. The metalogical consequences section (lines 1334-1340) already mentions completeness and its implications without requiring the full proof
4. This simplifies the metalogic section to focus on more tractable soundness arguments

### Recommendation 4: Preserve Metalogical Consequences

**Action**: Keep the "Metalogical Consequences" item (lines 1334-1340) which discusses:
- Consistency
- Decidability
- Compactness
- Expressiveness

**Rationale**: This provides students with important context about what the TM system can express and its key properties, without requiring detailed proofs. The mention of completeness as a consequence is appropriate even if the proof is omitted.

### Recommendation 5: Update Problem Set with New Exercises

**Action**: Expand "Problem Set: Metatheory" with the soundness proof exercises:

```latex
\item[\bf Soundness Proofs:] Provide explicit soundness proofs showing the following are valid over all task frames:
  \begin{enumerate}[label=\arabic*.]\small
    \item Modus ponens preserves validity (if $\models \metaA$ and $\models \metaA \rightarrow \metaB$, then $\models \metaB$)
    \item MK: $\Box(\metaA \rightarrow \metaB) \rightarrow (\Box\metaA \rightarrow \Box\metaB)$
    \item MF: $\Box\Future\metaA \rightarrow \Future\Box\metaA$
    \item (Challenge) Choose two axioms from MT, M4, MB, TD, TL, T4, TA, TF and prove their validity
  \end{enumerate}
```

**Rationale**: This creates a complete problem set that covers both semantic validity proofs and soundness proofs, giving students hands-on experience with both aspects of metatheory.

## References

### Primary Source Files
- `/home/benjamin/Documents/Philosophy/Teaching/LogicNotes/LogicNotes.tex` (current state)
  - Lines 964-989: Tense logic axiomatic system with TK axiom and FN rule
  - Lines 1288-1342: Bimodal metalogic section with soundness proofs and completeness section
  - Lines 1344-1366: Problem Set: Metatheory

- `/home/benjamin/Documents/Philosophy/Papers/PossibleWorlds/JPL/possible_worlds.tex` (target state)
  - Lines 1358-1359: Appendix section header
  - Lines 2101-2258: Proof Theory subsection with derivations
  - Lines 2260-2349: Soundness subsection with TK defined as rule (line 2324)

### Key Line References

#### LogicNotes.tex - TK Axiom
- Line 969: Current TK axiom definition
- Line 983: TL System description referencing TK as axiom

#### LogicNotes.tex - FN Rule
- Lines 977-981: FN rule definition (to be renamed TK)

#### LogicNotes.tex - Soundness Proofs
- Lines 1303-1305: MP proof (to be moved to problem set)
- Lines 1307-1309: MK proof (to be moved to problem set)
- Lines 1311-1313: MF proof (to be moved to problem set)

#### LogicNotes.tex - Completeness Section
- Lines 1318-1333: Entire section to be removed

#### LogicNotes.tex - Problem Set
- Line 1344: Problem Set: Metatheory header
- Lines 1347-1366: Current problem set structure

#### possible_worlds.tex - TK Rule
- Line 2324: TK defined as rule
- Lines 2331-2332: TK soundness proof showing rule formulation

## Implementation Status
- **Status**: Planning Complete
- **Plan**: [001-tense-logic-harmonize-metalogic-plan.md](../plans/001-tense-logic-harmonize-metalogic-plan.md)
- **Implementation**: [Will be updated by implementation workflow]
- **Date**: 2025-12-02
