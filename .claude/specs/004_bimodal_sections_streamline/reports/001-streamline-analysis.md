# Bimodal Sections Streamlining Research Report

## Metadata
- **Date**: 2025-12-02
- **Agent**: research-specialist
- **Topic**: Streamlining bimodal logic sections for conciseness and systematic presentation
- **Report Type**: codebase analysis
- **Complexity**: 3

## Executive Summary

The current bimodal logic sections (lines 1041-1493) contain significant redundancy in syntax definitions, verbose semantic explanations with worked examples, and an axiomatic system that does not leverage previously established tense logic axioms. The sections can be streamlined by: (1) eliminating redundant operator introductions since tense and modal operators are already defined in prior sections; (2) reducing semantic definitions to clean mathematical statements without discursive examples; (3) establishing a tense logic axiomatic system (TL) in the tense logic section that can be imported into the bimodal section; and (4) presenting the bimodal axiomatic system as the minimal extension combining S5 and TL with two interaction principles.

## Findings

### Current State Analysis

#### Syntax Section (Lines 1066-1143)

**Location**: `/home/benjamin/Documents/Philosophy/Teaching/LogicNotes/LogicNotes.tex:1066-1143`

**Current Content**:
- Lines 1069-1073: Language definition explicitly lists all operators including `$\Box$`, `$\Past$`, `$\Future$`
- Lines 1075-1089: Full WFF definition and all abbreviation definitions including `$\Diamond$`, `$\past$`, `$\future$`, `$\always$`, `$\sometimes$`
- Lines 1091-1099: Informal interpretation section explaining what each temporal operator means
- Lines 1101-1107: Scope conventions section

**Redundancy Issues**:
1. Modal operators (`$\Box$`, `$\Diamond$`) already introduced in "Propositional Modal Logic: Syntax" (lines 427-444)
2. Tense operators (`$\Past$`, `$\Future$`, `$\past$`, `$\future$`) already introduced in "Propositional Tense Logic: Syntax" (lines 778-820)
3. The abbreviations `$\always$` and `$\sometimes$` are already defined in tense logic section (lines 814-815)
4. Scope conventions for `$\Box$` already established in modal logic section
5. The informal interpretation section (lines 1091-1099) repeats information from tense logic section (lines 783-784, 810-811)

**Streamlining Opportunity**: This section should state that the bimodal language simply combines the modal and tense languages already defined, requiring only minimal new notation or clarification. Current estimate: 77 lines could be reduced to ~15-20 lines.

#### Semantics Section (Lines 1145-1229)

**Location**: `/home/benjamin/Documents/Philosophy/Teaching/LogicNotes/LogicNotes.tex:1145-1229`

**Current Content**:
- Lines 1147-1148: Introductory paragraph explaining motivation for task semantics
- Lines 1151-1183: Formal definitions (task frame, world history, task model, truth conditions, validity)
- Lines 1189-1206: Worked example with specific task frame, valuation, and truth evaluations

**Verbosity Issues**:
1. The introductory paragraph (lines 1147-1148) provides discursive motivation rather than direct definition
2. Each definition includes extensive interpretation clauses explaining the intuition (lines 1157, 1160, 1163, 1169, 1182)
3. The worked example (lines 1189-1206) demonstrates the semantics but adds 18 lines
4. Truth condition definitions include parenthetical explanations (line 1176: "absurdity is always false", line 1182: "Key insight: ...")

**Streamlining Opportunity**: Remove all discursive text, interpretation clauses, and worked examples. Present definitions as clean mathematical statements. Move examples to problem sets if needed. Current estimate: 85 lines could be reduced to ~35-40 lines.

#### Axiomatic System Section (Lines 1231-1329)

**Location**: `/home/benjamin/Documents/Philosophy/Teaching/LogicNotes/LogicNotes.tex:1231-1329`

**Current Content**:
- Lines 1234-1241: Propositional axioms
- Lines 1243-1254: Modal axioms (S5 system: K, MT, M4, MB, MF)
- Lines 1256-1267: Temporal axioms (TD, TK, TL, T4, TA, TF)
- Lines 1269-1280: Perpetuity principles (P1-P6)
- Lines 1284-1308: Full proofs of P1 and P2 with detailed steps

**Structural Issues**:
1. No separate tense logic axiomatic system exists in the tense logic sections - the axioms TD, TK, TL, T4, TA are only defined here in the bimodal context
2. The system is presented as a monolithic collection rather than as an extension of pre-existing systems
3. Detailed proofs of perpetuity principles (lines 1284-1308) take up 25 lines
4. The presentation does not clearly distinguish between:
   - S5 modal logic axioms (already established)
   - Tense logic axioms (should be established in tense section)
   - Bimodal interaction axioms (MF, TF - the truly novel content)

**Streamlining Opportunity**:
1. Create a tense logic axiomatic system TL in the "Propositional Tense Logic" section (after line 957) containing axioms TD, TK, TL, T4, TA
2. Reduce bimodal axiomatic section to state: "TM is the minimal extension of S5 ⊕ TL including axioms MF and TF"
3. Remove detailed proofs (they can be problem set exercises)
4. Current estimate: 99 lines could be reduced to ~20-25 lines

### Missing Infrastructure: Tense Logic Axiomatic System

**Critical Gap**: The "Propositional Tense Logic" sections (lines 778-1037) include:
- Syntax (lines 778-820)
- Frames (lines 848-880)
- Logical Consequence (lines 906-957)

**Missing**: There is no "Propositional Tense Logic: Axiomatic System" section that would parallel the modal logic structure. The modal logic sections include:
- Syntax (lines 427-444)
- Axiomatic Systems (lines 470-511)
- Frames (lines 557-605)
- Logical Consequence (lines 607-686)

**Required Addition**: A new section "Propositional Tense Logic: Axiomatic System" should be inserted around line 957 (after Logical Consequence, before the bimodal sections begin). This section should define:
- The TL proof system
- Axiom schemata: TD (temporal duality), TK (future distribution), TL (linearity), T4 (temporal transitivity), TA (temporal accessibility)
- Inference rules for temporal operators
- Derivability relation for TL

This would allow the bimodal section to simply reference "TL" rather than re-defining all tense axioms.

### Comparison with Modal Logic Presentation Style

**Modal Logic Syntax** (lines 427-444):
- 18 lines total
- Concise language definition (line 430)
- Minimal WFF clause (lines 431-437)
- Two abbreviations only (lines 438-442)
- One citation for historical context (line 443)

**Bimodal Logic Syntax** (lines 1066-1143):
- 77 lines total
- Verbose language definition with full tuple notation (lines 1069-1073)
- Recursive WFF definition (lines 1075-1079)
- Six abbreviations with detailed structure (lines 1081-1089)
- Extensive interpretation section (lines 1091-1099)
- Full scope convention section (lines 1101-1107)
- Problem set (lines 1109-1143)

**Style Mismatch**: The bimodal syntax section is 4× longer than modal syntax despite having less novel content (since operators are already defined). This violates the principle of "austere presentation" and "systematic building."

## Recommendations

### 1. Add Tense Logic Axiomatic System Section

**Location**: Insert after line 957 (after "Propositional Tense Logic: Logical Consequence" problem set, before line 1041 bimodal introduction)

**Content Structure**:
```latex
\section*{\sc Propositional Tense Logic: Axiomatic System}

\begin{enumerate}[leftmargin=1.2in]
  \item[\bf TL System:] The \textit{TL proof system} consists of all tautologies plus axiom instances below, closed under inference rules.
  \item[\bf Temporal Axioms:] The temporal operators satisfy:
    \begin{enumerate}[...]
      \item[\bf TD:] If $\TLproves \metaA$, then $\TLproves \metaA[\Past/\Future]$
      \item[\bf TK:] If $\MetaG \TLproves \metaA$, then $\Future\MetaG \TLproves \Future\metaA$
      \item[\bf TL:] $\always\metaA \rightarrow \Future\Past\metaA$
      \item[\bf T4:] $\Future\metaA \rightarrow \Future\Future\metaA$
      \item[\bf TA:] $\metaA \rightarrow \Future\past\metaA$
    \end{enumerate}
  \item[\bf Derivability:] $\MetaG \TLproves \metaA$ when a TL-proof exists.
\end{enumerate}

\section*{\it Problem Set: Tense Proofs}
[Exercises deriving tense theorems]
```

**Rationale**: This establishes the tense logic foundation before bimodal logic, following the same pattern as modal logic (which has its axiomatic system before bimodal logic introduces modal-temporal interaction).

### 2. Streamline Bimodal Syntax Section

**Location**: Lines 1066-1143

**Target Length**: Reduce from 77 lines to ~20 lines (not counting problem set)

**Revised Structure**:
```latex
\section*{\sc Bimodal Logic: Syntax}

\begin{enumerate}[leftmargin=1.2in]
  \item[\bf Language:] The bimodal language $\BL$ combines modal and tense operators:
    \[ \metaA ::= p_i \mid \bot \mid \metaA \rightarrow \metaA \mid \Box \metaA \mid \Past \metaA \mid \Future \metaA \]
  \item[\bf Notation:] We maintain abbreviations from modal logic ($\Diamond$) and tense logic ($\past$, $\future$, $\always$, $\sometimes$) with standard scope conventions.
\end{enumerate}
```

**Deletions**:
- Remove full language tuple definition (lines 1069-1073)
- Remove expanded abbreviation list (lines 1081-1089) - reference prior sections instead
- Remove informal interpretation section (lines 1091-1099) - already covered in tense section
- Remove scope convention section (lines 1101-1107) - reference modal logic conventions

**Estimated Savings**: ~60 lines

### 3. Streamline Bimodal Semantics Section

**Location**: Lines 1145-1229

**Target Length**: Reduce from 85 lines to ~40 lines (not counting problem set)

**Revised Structure**:
- Remove introductory paragraph (lines 1147-1148)
- Remove interpretation clauses from definitions (e.g., lines 1157, 1160, 1163, 1169)
- Remove "Key insight" commentary (line 1182)
- Delete entire worked example (lines 1189-1206)
- Present definitions as clean mathematical statements only

**Example Before** (lines 1151-1163):
```latex
\item[\bf Task Frame:] A \textbf{task frame} is a triple $\taskframe = \tuple{\worldstateset, \Tor, \taskrel}$ where:
  \begin{itemize}
    \item $\worldstateset$ is a non-empty set of \textbf{world states}
    \item $\Tor = \tuple{T, +, \leq}$ is a \textbf{totally ordered abelian group} (...)
    \item $\taskrel \subseteq \worldstateset \times T \times \worldstateset$ is a parameterized \textbf{task relation}
  \end{itemize}
  We write $w \taskrel_x v$ to mean $\tuple{w,x,v} \in \taskrel$, read as ``world state $v$ is accessible...''

\item[\it Nullity Constraint:] For all $w \in \worldstateset$, we have $w \taskrel_0 w$. \\
  \textit{Interpretation:} Every world state can perform the null task...
```

**Example After**:
```latex
\item[\bf Task Frame:] A \textbf{task frame} is a triple $\taskframe = \tuple{\worldstateset, \Tor, \taskrel}$ where $\worldstateset$ is a non-empty set, $\Tor = \tuple{T, +, \leq}$ is a totally ordered abelian group, and $\taskrel \subseteq \worldstateset \times T \times \worldstateset$. Write $w \taskrel_x v$ for $\tuple{w,x,v} \in \taskrel$.
\item[\it Nullity:] $w \taskrel_0 w$ for all $w \in \worldstateset$.
```

**Estimated Savings**: ~45 lines

### 4. Streamline Bimodal Axiomatic System Section

**Location**: Lines 1231-1329

**Target Length**: Reduce from 99 lines to ~25 lines (not counting problem set)

**Revised Structure**:
```latex
\section*{\sc Bimodal Logic: Axiomatic System}

\begin{enumerate}[leftmargin=1.2in]
  \item[\bf TM System:] The TM proof system is the minimal extension of S5 modal logic and TL tense logic including all instances of:
    \begin{enumerate}[...]
      \item[\bf MF:] $\Box\metaA \rightarrow \Box\Future\metaA$
      \item[\bf TF:] $\Box\metaA \rightarrow \Future\Box\metaA$
    \end{enumerate}
  \item[\bf Derivability:] $\MetaG \TMproves \metaA$ when a TM-proof exists combining S5-proofs, TL-proofs, and applications of MF, TF.
  \item[\bf Perpetuity Principles:] The following are TM-derivable:
    [List P1-P6 without proofs]
\end{enumerate}
```

**Deletions**:
- Remove propositional axioms list (lines 1236-1241) - reference S5 instead
- Remove full modal axioms list (lines 1243-1254) - reference S5 instead
- Remove full temporal axioms list (lines 1256-1267) - reference TL instead
- Remove detailed proofs of P1, P2 (lines 1284-1308) - move to problem set
- State only the two genuinely new bimodal interaction axioms: MF and TF

**Estimated Savings**: ~75 lines

### 5. Preserve Problem Sets

**Recommendation**: Maintain all problem sets but consider:
- Moving worked proofs to problem set exercises
- Adding exercises that explicitly ask students to derive perpetuity principles
- Including exercises that demonstrate how TM extends both S5 and TL

**Rationale**: Problem sets are pedagogically valuable and the user specified they are "OK" to keep.

### 6. Remove Examples and Proofs from Main Text

**Current Examples**:
- Bimodal Semantics worked example (lines 1189-1206): 18 lines
- Perpetuity principle proofs P1, P2 (lines 1284-1308): 25 lines

**Recommendation**: Delete all worked examples and detailed proofs from main sections. If needed, these can become problem set exercises where students complete them.

**Rationale**: User explicitly requested "no worked examples or proofs anywhere" in favor of "clean and austere presentation."

## References

### Files Analyzed
- `/home/benjamin/Documents/Philosophy/Teaching/LogicNotes/LogicNotes.tex`:
  - Lines 427-444: Propositional Modal Logic: Syntax
  - Lines 470-511: Propositional Modal Logic: Axiomatic Systems
  - Lines 778-820: Propositional Tense Logic: Syntax
  - Lines 848-880: Propositional Tense Logic: Frames
  - Lines 906-957: Propositional Tense Logic: Logical Consequence
  - Lines 1041-1065: Bimodal Logic: Tense and Modality (introduction)
  - Lines 1066-1143: Bimodal Logic: Syntax
  - Lines 1145-1229: Bimodal Logic: Semantics
  - Lines 1231-1329: Bimodal Logic: Axiomatic System
  - Lines 1331-1409: Bimodal Logic: Metatheory
  - Lines 1414-1493: Bimodal Logic: Extensions

### Key Observations
- Modal operators introduced at line 430
- Modal abbreviation `$\Diamond$` defined at line 440
- Tense operators introduced at lines 783-784
- Tense abbreviations `$\past$`, `$\future$`, `$\always$`, `$\sometimes$` defined at lines 810-815
- Modal axiom schemata (K, T, B, 4, 5) defined at lines 476-481
- S5 system defined at lines 503-504
- No tense logic axiomatic system exists in current text
- Bimodal system defines modal axioms MT, M4, MB at lines 1248-1250 (equivalent to T, 4, B)
- Bimodal system defines temporal axioms TD, TK, TL, T4, TA at lines 1259-1263
- Bimodal interaction axioms MF, TF defined at lines 1251, 1264

### Structural Pattern
The document follows a consistent organizational pattern for each logic:
1. Syntax (language, WFF, abbreviations)
2. Axiomatic Systems or Frames
3. Logical Consequence or Semantics
4. Metatheory

Modal Logic sections: Syntax → Axiomatic Systems → Frames → Logical Consequence → Metalogic
Tense Logic sections: Syntax → Frames → Logical Consequence → [MISSING: Axiomatic System]
Bimodal sections: Introduction → Syntax → Semantics → Axiomatic System → Metatheory → Extensions

The missing tense logic axiomatic system breaks this pattern and creates the need for redundancy in the bimodal section.

## Implementation Status

- **Status**: Planning Complete
- **Plan**: [../plans/001-bimodal-sections-streamline-plan.md](../plans/001-bimodal-sections-streamline-plan.md)
- **Implementation**: Not yet started
- **Date**: 2025-12-02
