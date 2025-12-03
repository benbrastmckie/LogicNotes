# Section Restructuring Implementation Plan: Bimodal and First-Order Logic

## Metadata
- **Date**: 2025-12-02
- **Feature**: Relocate sec:FirstOrder to additional.tex and replace sec:Bimodal content with sec:TenseModality material while preserving definition-focused presentation style
- **Scope**: This plan restructures the LogicNotes.tex document by (1) moving the complete First-Order Logic section to the additional materials file, and (2) replacing the Bimodal Logic section's content with material from the Tense-Modality section while maintaining the concise, definition-oriented pedagogical style of the original Bimodal section (no proofs, no derivations, exercise focus on countermodels).
- **Estimated Phases**: 7
- **Estimated Hours**: 6-8 hours
- **Complexity Score**: 47.0
- **Structure Level**: 0
- **Standards File**: /home/benjamin/Documents/Philosophy/Teaching/LogicNotes/CLAUDE.md
- **Status**: [COMPLETE]
- **Research Reports**:
  - [Section Restructuring Research](../reports/001-section-restructuring-research.md)

## Overview

This implementation systematically restructures two sections of the LogicNotes.tex document:

1. **Section Relocation**: Move sec:FirstOrder (First-Order Logic: Syntax) from LogicNotes.tex (lines 1191-1389) to additional/additional.tex as supplementary material. This section is self-contained with no cross-references to other parts of the document.

2. **Content Replacement**: Replace sec:Bimodal (Propositional Bimodal Logic: Task Semantics) content with material from sec:TenseModality (Bimodal Logic: Tense and Modality) while preserving sec:Bimodal's pedagogical style:
   - **Preserve**: Enumerate-based definition lists, bold labels, minimal prose, NO proofs or proof sketches
   - **Import**: Syntax definitions, task semantics framework, semantic clauses from sec:TenseModality
   - **Exclude**: Natural language motivation, complete axiomatic system, Hilbert-style proofs, derivation problems
   - **Adapt**: Problem sets to focus on semantic evaluation and countermodels (not axiomatic derivations)

The goal is a uniform presentation of bimodal logic definitions in consistent notation with exercises emphasizing semantic understanding rather than proof construction.

## Research Summary

Research findings from the section restructuring analysis:

**Structural Analysis:**
- sec:FirstOrder (198 lines): Self-contained, no dependencies, suitable for relocation to additional.tex
- sec:Bimodal (142 lines): Definition-focused style using enumerate lists with `[leftmargin=1.2in]`, bold labels, compact semantic clauses
- sec:TenseModality (280+ lines): Mixed format with prose motivation, axiomatic system with Hilbert-style proofs, and task semantics framework

**Key Findings:**
- Style preservation is critical: sec:Bimodal uses enumerate-based definitions WITHOUT proof sketches
- Content extraction mapping: TenseModality syntax + task semantics → Bimodal structure
- Notation consistency: All TM-specific commands already defined in notation.sty (lines 180-202)
- Problem set adaptation: Replace derivation exercises with countermodel exercises targeting perpetuity principles

**Recommended Approach:**
- Incremental implementation with compilation checkpoints after each phase
- Systematic exclusion of proof-theoretic content (axiomatic system, Hilbert proofs, derivation problems)
- Preserve label `\label{sec:Bimodal}` to maintain any existing cross-references
- Backup current sec:Bimodal before replacement

## Success Criteria

- [ ] sec:FirstOrder successfully moved to additional/additional.tex with all subsections and problem sets
- [ ] additional/additional.tex compiles without errors after sec:FirstOrder insertion
- [ ] sec:Bimodal content replaced with TenseModality material while preserving definition-focused style
- [ ] NO axiomatic systems, proof sketches, or Hilbert-style derivations in replacement content
- [ ] Problem sets adapted to focus on countermodels and semantic evaluation (not derivations)
- [ ] Label `\label{sec:Bimodal}` preserved for cross-reference compatibility
- [ ] All custom commands used in replacement are defined in notation.sty
- [ ] LogicNotes.tex compiles successfully after all changes
- [ ] Formatting consistency maintained: enumerate `[leftmargin=1.2in]`, itemize `[leftmargin=.15in]\small` for semantic clauses
- [ ] Final document maintains professional appearance with no broken references

## Technical Design

### Architecture Overview

The restructuring involves two independent file modification streams that can be validated separately:

**Stream 1: Section Relocation (sec:FirstOrder → additional.tex)**
- Extract lines 1191-1389 from LogicNotes.tex
- Append to additional/additional.tex after line 142 (after sec:Cartesian)
- Maintain TEX root directive compatibility
- Preserve section label for potential cross-references

**Stream 2: Content Replacement (sec:TenseModality → sec:Bimodal)**
- Map TenseModality subsections to Bimodal definition structure
- Filter out proof-theoretic content during extraction
- Preserve Bimodal's formatting conventions (enumerate leftmargin, bold labels)
- Adapt problem sets from syntax/semantic focus to countermodel exercises

### Component Interactions

**File Dependencies:**
- LogicNotes.tex (main document)
- additional/additional.tex (supplementary materials)
- assets/notation.sty (custom command definitions)
- assets/proof_styles.sty (formatting environments)

**Critical Labels:**
- `\label{sec:FirstOrder}` - must remain accessible after relocation
- `\label{sec:Bimodal}` - must be preserved during content replacement
- `\label{sec:TenseModality}` - retained in source location

**Custom Commands Required (from notation.sty):**
- `\BL` - Bimodal language (line 231)
- `\Past`, `\Future`, `\past`, `\future` - Temporal operators (lines 208-210)
- `\Box`, `\Diamond` - Modal operators
- `\always`, `\sometimes` - Compound temporal operators (lines 146-147)
- `\taskrel`, `\worldhist`, `\worldhistset` - Task semantics notation (lines 193-202)
- `\TMSystem`, `\TML` - TM system references (lines 180-192)

### Content Extraction Strategy

**Mapping from sec:TenseModality to sec:Bimodal structure:**

1. **Well-Formed Sentences** ← TenseModality "Language" (lines 1412-1416) + "Well-Formed Sentences" (lines 1418-1422)
2. **Abbreviations** ← TenseModality "Abbreviations" (lines 1424-1432), condensed
3. **Frame** ← TenseModality "Task Frame" (from Task Semantics section, lines ~1635-1645)
4. **Interpretation** ← TenseModality "Task Model" world state interpretation
5. **Model** ← TenseModality "Task Model" complete definition
6. **Possible World** ← TenseModality "World History" (renamed from sec:TenseModality for consistency)
7. **Semantics** ← TenseModality "Truth Conditions" semantic clauses (lines ~1655-1670)
8. **Logical Consequence** ← TenseModality validity definition

**Exclusion Filter (remove from extraction):**
- Natural language motivation paragraph (lines 1399-1407)
- Complete axiomatic system section (lines 1452-1530)
- All Hilbert-style proof environments (`\begin{hilbert}...\end{hilbert}`)
- Proof sketches (P1, P2, perpetuity principle derivations)
- Problem Set: TM Derivations (lines 1584-1630)
- All `\TMproves` and axiomatic references

### Formatting Standards

**Preserve from sec:Bimodal:**
- Section header: `\section*{\sc Title}` with small caps
- Definition list: `\begin{enumerate}[leftmargin=1.2in]`
- Bold labels: `\item[\bf Label:]` for each definition type
- Semantic clauses: `\begin{itemize}[leftmargin=.15in]\small`
- Problem set header: `\section*{\it Problem Set: Topic}`
- Minimal prose between definitions

**Apply from notation.sty:**
- Metavariables: `\metaA`, `\metaB` (lines 267-269)
- Semantic entailment: `\MLmodels[]` (line 155)
- Task frame notation: `\taskframe`, `\worldhist`

## Implementation Phases

### Phase 1: Pre-Implementation Verification [COMPLETE]
dependencies: []

**Objective**: Verify baseline document state, create backups, and confirm all custom commands are defined before making any modifications.

**Complexity**: Low

**Tasks**:
- [x] Compile LogicNotes.tex to establish baseline (verify clean compilation)
- [x] Create timestamped backup: `cp LogicNotes.tex LogicNotes.tex.backup.$(date +%Y%m%d_%H%M%S)`
- [x] Create backup of additional/additional.tex: `cp additional/additional.tex additional/additional.tex.backup.$(date +%Y%m%d_%H%M%S)`
- [x] Verify notation.sty contains all required TM commands (lines 180-202): `\TML`, `\TMproves`, `\TMmodels`, `\taskrel`, `\worldhist`
- [x] Verify sec:FirstOrder location in LogicNotes.tex (lines 1191-1389)
- [x] Verify sec:Bimodal location in LogicNotes.tex (lines 1041-1183)
- [x] Verify sec:TenseModality location in LogicNotes.tex (lines 1396-1674+)
- [x] Confirm additional/additional.tex current end position (line 142 after sec:Cartesian)

**Testing**:
```bash
cd /home/benjamin/Documents/Philosophy/Teaching/LogicNotes
pdflatex LogicNotes.tex && echo "✓ Baseline compilation successful" || echo "✗ Baseline compilation failed"
grep -n "\\\\section\*{\\\\sc First-Order Logic: Syntax}" LogicNotes.tex
grep -n "\\\\section\*{\\\\sc Propositional Bimodal Logic: Task Semantics}" LogicNotes.tex
grep -n "\\\\section\*{\\\\sc Bimodal Logic: Tense and Modality}" LogicNotes.tex
```

**Expected Duration**: 0.5 hours

---

### Phase 2: Extract and Relocate sec:FirstOrder [COMPLETE]
dependencies: [1]

**Objective**: Move the complete First-Order Logic section from LogicNotes.tex to additional/additional.tex, preserving all content and formatting.

**Complexity**: Medium

**Tasks**:
- [x] Extract sec:FirstOrder from LogicNotes.tex (lines 1191-1389) including:
  - Section header: `\section*{\sc First-Order Logic: Syntax}` with `\label{sec:FirstOrder}`
  - All four subsections: Syntax, Proof Theory, Semantics, Metalogic
  - All embedded problem sets
  - All enumerate and itemize environments
- [x] Open additional/additional.tex and position cursor after line 142 (end of sec:Cartesian)
- [x] Insert blank line separator, then paste complete sec:FirstOrder content
- [x] Verify formatting consistency: indentation, spacing, enumerate parameters
- [x] Remove sec:FirstOrder from LogicNotes.tex (delete lines 1191-1389)
- [x] Add section break comment in LogicNotes.tex at removal point: `% sec:FirstOrder moved to additional/additional.tex`

**Testing**:
```bash
# Test additional.tex compilation
cd /home/benjamin/Documents/Philosophy/Teaching/LogicNotes/additional
pdflatex additional.tex && echo "✓ additional.tex compiles" || echo "✗ Compilation failed"

# Test LogicNotes.tex compilation after removal
cd /home/benjamin/Documents/Philosophy/Teaching/LogicNotes
pdflatex LogicNotes.tex && echo "✓ LogicNotes.tex compiles after removal" || echo "✗ Compilation failed"

# Verify label still accessible
grep -n "label{sec:FirstOrder}" additional/additional.tex
```

**Expected Duration**: 1 hour

---

### Phase 3: Create sec:Bimodal Backup and Extract Source Material [COMPLETE]
dependencies: [2]

**Objective**: Preserve current sec:Bimodal content and extract relevant definitions from sec:TenseModality for replacement, filtering out all proof-theoretic content.

**Complexity**: Medium

**Tasks**:
- [x] Save current sec:Bimodal content (lines 1041-1183) to temporary file: `sec_bimodal_original.tex`
- [x] Document sec:Bimodal's style elements for preservation:
  - Enumerate leftmargin: `[leftmargin=1.2in]`
  - Bold label pattern: `\item[\bf Label:]`
  - Semantic clauses format: `\begin{itemize}[leftmargin=.15in]\small`
  - NO prose paragraphs between definitions
- [x] Extract syntax definitions from sec:TenseModality (lines 1411-1450):
  - Language definition (lines 1412-1416)
  - Well-formed sentences grammar (lines 1418-1422)
  - Abbreviations list (lines 1424-1432) - to be condensed
  - Scope conventions (lines 1444+)
- [x] Extract task semantics definitions from sec:TenseModality (lines 1632-1674):
  - Task frame structure
  - World history definition with convexity constraint
  - Task model and interpretation
  - Truth conditions (semantic clauses)
  - Validity and logical consequence definitions
- [x] Mark extraction boundaries and confirm NO axiomatic content included

**Testing**:
```bash
# Verify backup created
test -f sec_bimodal_original.tex && echo "✓ Backup created" || echo "✗ Backup missing"

# Verify extracted content contains no proof keywords
! grep -i "hilbert\|\\\\TMproves\|proof sketch\|axiom\|derivation" extracted_content.tex && echo "✓ No proof content" || echo "✗ Proof content found"

# Count lines of extracted material
wc -l extracted_content.tex
```

**Expected Duration**: 1 hour

---

### Phase 4: Reformat Extracted Content to Bimodal Style [COMPLETE]
dependencies: [3]

**Objective**: Transform extracted TenseModality content into sec:Bimodal's enumerate-based definition format, removing all prose and proof elements.

**Complexity**: High

**Tasks**:
- [x] Create new enumerate list with `\begin{enumerate}[leftmargin=1.2in]`
- [x] Reformat "Language" definition from prose (TM lines 1412-1416) to bold label format:
  - `\item[\bf Language:] The \textit{bimodal language} $\BL$ extends propositional logic...`
  - Remove tuple notation if overly formal, present as grammar
- [x] Consolidate "Well-Formed Sentences" grammar (TM lines 1418-1422) into BNF format matching Bimodal style:
  - `\item[\bf Well-Formed Sentences:] Letting $p_i \in \SL$, the \textit{well-formed sentences} $\BL$ are defined: \[ \metaA \Coloneq p_i \mid \bot \mid ... \]`
- [x] Condense "Abbreviations" (TM lines 1424-1432) to single item with sub-itemize:
  - `\item[\bf Abbreviation:] We define: (i) $\Diamond \metaA := \neg\Box\neg\metaA$, (ii) $\past \metaA := ...$`
  - Remove verbose "informal meanings" - keep definitions only
- [x] Extract and reformat task semantics components:
  - `\item[\bf Frame:]` - task frame structure from TM task semantics section
  - `\item[\bf Interpretation:]` - world state interpretation function
  - `\item[\bf Model:]` - complete model tuple definition
  - `\item[\bf Possible World:]` - world history definition (rename from "World History")
- [x] Reformat semantic clauses from TM to compact itemize with `[leftmargin=.15in]\small`:
  - `\item[\bf Semantics:] Letting $H_\Z$ be the set of all possible worlds..., we define $\vDash$ recursively...`
  - List all truth conditions in itemize: `\item[] $\M, \tau, x \vDash \Box \metaA$ iff...`
- [x] Add logical consequence definition:
  - `\item[\bf Logical Consequence:] $\MetaG \MLmodels[] \metaA$ just in case...`

**Testing**:
```bash
# Verify no prose paragraphs remain
! grep -E "^[A-Z][a-z]+ [a-z]+ [a-z]+" reformatted_bimodal.tex && echo "✓ No prose paragraphs" || echo "✗ Prose detected"

# Verify enumerate format
grep "\\\\begin{enumerate}\[leftmargin=1.2in\]" reformatted_bimodal.tex && echo "✓ Enumerate format correct"

# Verify bold labels present
grep -c "\\\\item\[\\\\bf" reformatted_bimodal.tex
# Should return 8 (one for each definition type)

# Test compilation fragment
cat > test_fragment.tex <<'EOF'
\documentclass{article}
\usepackage{enumitem}
\input{assets/notation.sty}
\begin{document}
\input{reformatted_bimodal.tex}
\end{document}
EOF
pdflatex test_fragment.tex && echo "✓ Fragment compiles"
```

**Expected Duration**: 2 hours

---

### Phase 5: Adapt Problem Sets for Semantic Focus [COMPLETE]
dependencies: [4]

**Objective**: Create countermodel-focused problem sets from TenseModality syntax exercises, excluding all derivation problems.

**Complexity**: Medium

**Tasks**:
- [x] Extract "Problem Set: TM Syntax" from sec:TenseModality (lines 1531-1582)
- [x] Filter exercises appropriate for semantic evaluation:
  - Well-formedness checking exercises (keep)
  - Abbreviation expansion exercises (keep)
  - Scope disambiguation exercises (keep)
  - Parse tree construction (adapt to semantic trees if present)
- [x] Create new "Problem Set: Task Semantics" section following Bimodal style:
  - Section header: `\section*{\it Problem Set: Task Semantics}`
  - Use enumerate with `[leftmargin=1.2in]`
  - Label: `\item[\bf Countermodels:]` as main category
- [x] Develop countermodel exercises targeting perpetuity principles (from TM lines 1452-1480):
  - Convert P1-P6 principles from axioms to semantic evaluation problems
  - Format: "Evaluate the following, providing a proof or countermodel:"
  - Examples:
    - `$\MLmodels[] \Box\metaA \rightarrow \always\metaA$` (P1 as validity question)
    - `$\MLmodels[] \sometimes\metaA \rightarrow \Diamond\metaA$` (P2 as validity question)
  - Use multicols for space efficiency: `\begin{multicols}{2}`
- [x] Remove all references to axiomatic derivations, `\TMproves`, Hilbert proofs
- [x] Keep problem numbering consistent with document style

**Testing**:
```bash
# Verify no derivation language
! grep -iE "derive|prove|hilbert|\\\\TMproves|axiom" problem_set.tex && echo "✓ No derivation problems" || echo "✗ Derivation found"

# Verify countermodel focus
grep -c "countermodel" problem_set.tex && echo "✓ Countermodel focus maintained"

# Verify enumerate format
grep "\\\\begin{enumerate}\[leftmargin=1.2in\]" problem_set.tex && echo "✓ Format correct"

# Test compilation
cat > test_problems.tex <<'EOF'
\documentclass{article}
\usepackage{enumitem,multicol}
\input{assets/notation.sty}
\begin{document}
\input{problem_set.tex}
\end{document}
EOF
pdflatex test_problems.tex && echo "✓ Problems compile"
```

**Expected Duration**: 1.5 hours

---

### Phase 6: Replace sec:Bimodal Content in LogicNotes.tex [COMPLETE]
dependencies: [5]

**Objective**: Replace the current sec:Bimodal section in LogicNotes.tex with reformatted TenseModality content while preserving the section label and position.

**Complexity**: Medium

**Tasks**:
- [x] Locate sec:Bimodal in LogicNotes.tex (lines 1041-1183)
- [x] Preserve section header and label:
  - Keep: `\section*{\sc Propositional Bimodal Logic: Task Semantics}`
  - Keep: `\label{sec:Bimodal}`
- [x] Delete current sec:Bimodal content (lines 1044-1183, after label)
- [x] Insert reformatted content from Phase 4:
  - Enumerate-based definitions (Language, WFS, Abbreviations, Frame, Interpretation, Model, Possible World, Semantics, Logical Consequence)
  - Ensure proper spacing and indentation
- [x] Insert adapted problem sets from Phase 5:
  - Problem Set: Task Semantics section with countermodel exercises
  - Maintain section break between definitions and problems
- [x] Verify label `\label{sec:Bimodal}` remains at line 1042 (no line number shift for label)
- [x] Add comment noting content source: `% Content adapted from sec:TenseModality, proof-theoretic material excluded`

**Testing**:
```bash
# Verify label preserved
grep -n "\\\\label{sec:Bimodal}" LogicNotes.tex | head -1

# Verify section header unchanged
grep -A 1 "\\\\section\*{\\\\sc Propositional Bimodal Logic: Task Semantics}" LogicNotes.tex | grep "\\\\label{sec:Bimodal}"

# Test compilation after replacement
cd /home/benjamin/Documents/Philosophy/Teaching/LogicNotes
pdflatex LogicNotes.tex && echo "✓ LogicNotes.tex compiles after replacement" || echo "✗ Compilation failed"

# Check for undefined commands
pdflatex LogicNotes.tex 2>&1 | grep -i "undefined" && echo "✗ Undefined commands found" || echo "✓ No undefined commands"
```

**Expected Duration**: 1 hour

---

### Phase 7: Final Verification and Compilation Testing [COMPLETE]
dependencies: [6]

**Objective**: Perform comprehensive verification of all changes, test full document compilation, and validate formatting consistency.

**Complexity**: Low

**Tasks**:
- [x] Verify sec:FirstOrder present in additional/additional.tex with correct label
- [x] Verify sec:Bimodal content replaced with NO proof-theoretic material
- [x] Check all custom commands defined in notation.sty are used correctly:
  - `\BL`, `\Past`, `\Future`, `\Box`, `\Diamond`, `\always`, `\sometimes`
  - `\taskrel`, `\worldhist`, `\metaA`, `\metaB`, `\MLmodels[]`
- [x] Verify formatting consistency throughout replaced section:
  - Enumerate leftmargin: `[leftmargin=1.2in]`
  - Bold labels: `\item[\bf Label:]`
  - Semantic clauses: `\begin{itemize}[leftmargin=.15in]\small`
- [x] Full compilation test of LogicNotes.tex:
  - Run pdflatex twice to resolve cross-references
  - Check for warnings: overfull/underfull boxes, missing references
  - Verify page breaks are reasonable (no awkward splits)
- [x] Compilation test of additional/additional.tex
- [x] Compare PDF output with original backup to verify visual consistency
- [x] Verify problem set exercises are appropriate (countermodels, not derivations)
- [x] Check that sec:TenseModality remains unchanged in LogicNotes.tex (source preserved)

**Testing**:
```bash
cd /home/benjamin/Documents/Philosophy/Teaching/LogicNotes

# Full compilation with cross-reference resolution
pdflatex LogicNotes.tex && pdflatex LogicNotes.tex && echo "✓ Full compilation successful" || echo "✗ Compilation failed"

# Compilation of additional materials
cd additional
pdflatex additional.tex && echo "✓ Additional materials compile" || echo "✗ Compilation failed"
cd ..

# Verify label accessibility
grep "\\\\label{sec:FirstOrder}" additional/additional.tex && echo "✓ sec:FirstOrder label accessible"
grep "\\\\label{sec:Bimodal}" LogicNotes.tex && echo "✓ sec:Bimodal label preserved"

# Check for compilation warnings
pdflatex LogicNotes.tex 2>&1 | grep -iE "warning|error" > compilation_warnings.txt
cat compilation_warnings.txt

# Verify no proof environments in sec:Bimodal
sed -n '1041,1300p' LogicNotes.tex | grep -i "hilbert\|\\\\TMproves\|proof sketch" && echo "✗ Proof content found!" || echo "✓ No proof content in sec:Bimodal"

# Check custom commands used correctly
pdflatex LogicNotes.tex 2>&1 | grep "Undefined control sequence" && echo "✗ Undefined commands" || echo "✓ All commands defined"

# Document statistics
echo "sec:Bimodal line count after replacement:"
sed -n '/^\\section\*{\\sc Propositional Bimodal Logic: Task Semantics}/,/^\\section/p' LogicNotes.tex | wc -l
```

**Expected Duration**: 1 hour

---

## Testing Strategy

### Unit Testing (Phase-Level)

Each phase includes inline testing to verify successful completion before proceeding:

1. **Phase 1**: Baseline compilation verification
   - Test: `pdflatex LogicNotes.tex` exits with code 0
   - Test: Backup files created with correct timestamps

2. **Phase 2**: Section relocation validation
   - Test: additional/additional.tex compiles independently
   - Test: LogicNotes.tex compiles after sec:FirstOrder removal
   - Test: Label `\label{sec:FirstOrder}` present in additional.tex

3. **Phase 3-4**: Content extraction and reformatting
   - Test: No proof keywords (`hilbert`, `\TMproves`, `axiom`) in extracted content
   - Test: Enumerate format matches spec: `[leftmargin=1.2in]`
   - Test: Fragment compilation using minimal test document

4. **Phase 5**: Problem set adaptation
   - Test: No derivation language in problem sets
   - Test: Countermodel exercises formatted correctly
   - Test: Problem set compiles in isolation

5. **Phase 6**: Content replacement
   - Test: sec:Bimodal label preserved at correct position
   - Test: LogicNotes.tex compiles after replacement
   - Test: No undefined commands in compilation output

6. **Phase 7**: Integration testing (see below)

### Integration Testing

**Full Document Compilation:**
```bash
cd /home/benjamin/Documents/Philosophy/Teaching/LogicNotes
pdflatex LogicNotes.tex
pdflatex LogicNotes.tex  # Second pass for cross-references
echo "Exit code: $?"  # Should be 0

# Check for critical errors
grep -iE "^!" LogicNotes.log && echo "LaTeX errors found" || echo "No LaTeX errors"
```

**Cross-Reference Validation:**
```bash
# Verify no undefined references
grep "LaTeX Warning: Reference" LogicNotes.log && echo "Undefined references detected" || echo "All references defined"

# Check label accessibility
grep "label{sec:FirstOrder}" additional/additional.tex
grep "label{sec:Bimodal}" LogicNotes.tex
grep "label{sec:TenseModality}" LogicNotes.tex
```

**Content Verification:**
```bash
# Verify sec:FirstOrder moved
grep -c "section\*{\\\\sc First-Order Logic: Syntax}" LogicNotes.tex  # Should be 0
grep -c "section\*{\\\\sc First-Order Logic: Syntax}" additional/additional.tex  # Should be 1

# Verify sec:Bimodal content replaced
sed -n '1041,1300p' LogicNotes.tex > bimodal_section.txt
! grep -iE "hilbert|\\\\TMproves|proof sketch|axiomatic system" bimodal_section.txt && echo "✓ No proof content" || echo "✗ Proof content remains"
grep -c "\\\\item\[\\\\bf" bimodal_section.txt  # Should be ~8 definition labels
```

**Formatting Consistency:**
```bash
# Check enumerate formatting in sec:Bimodal replacement
sed -n '1041,1300p' LogicNotes.tex | grep -c "\\\\begin{enumerate}\[leftmargin=1.2in\]"  # Should be ≥1

# Check semantic clause formatting
sed -n '1041,1300p' LogicNotes.tex | grep -c "\\\\begin{itemize}\[leftmargin=.15in\]\\\\small"  # Should be ≥1

# Check bold label usage
sed -n '1041,1300p' LogicNotes.tex | grep -c "\\\\item\[\\\\bf.*:\]"  # Should be ~8
```

### Regression Testing

**Visual Comparison:**
1. Compile original LogicNotes.tex (from backup) to PDF
2. Compile modified LogicNotes.tex to PDF
3. Compare page counts: should be reduced by ~2-3 pages (sec:FirstOrder removed)
4. Spot-check sec:Bimodal section for visual consistency (no dramatic layout changes)

**Style Preservation:**
- sec:Bimodal maintains enumerate-based definition lists
- Bold labels present for each definition type
- Semantic clauses use compact itemize format
- Problem sets follow original formatting

## Documentation Requirements

### Inline Documentation

**LogicNotes.tex:**
- Add comment at sec:FirstOrder removal point:
  ```latex
  % sec:FirstOrder moved to additional/additional.tex on 2025-12-02
  ```
- Add comment at beginning of replaced sec:Bimodal content:
  ```latex
  % Content adapted from sec:TenseModality (lines 1396-1674)
  % Proof-theoretic material excluded per pedagogical focus on definitions
  % Last updated: 2025-12-02
  ```

**additional/additional.tex:**
- Add comment before sec:FirstOrder insertion:
  ```latex
  % sec:FirstOrder relocated from LogicNotes.tex on 2025-12-02
  % Includes complete syntax, proof theory, semantics, and metalogic subsections
  ```

### Change Summary Document

Create brief summary in project root documenting changes:

**File**: `CHANGELOG_SECTION_RESTRUCTURE.txt`

**Content**:
```
Section Restructuring - 2025-12-02

Changes to LogicNotes.tex:
1. sec:FirstOrder (First-Order Logic: Syntax) moved to additional/additional.tex
   - Original location: LogicNotes.tex lines 1191-1389
   - New location: additional/additional.tex (appended after line 142)
   - Label \label{sec:FirstOrder} preserved

2. sec:Bimodal (Propositional Bimodal Logic: Task Semantics) content replaced
   - Original: Basic bimodal logic with task semantics (142 lines)
   - Replacement: TenseModality syntax + task semantics adapted to definition style
   - Source: sec:TenseModality lines 1396-1674 (selective extraction)
   - Excluded: Natural language motivation, axiomatic system, Hilbert proofs, derivation problems
   - Preserved: Label \label{sec:Bimodal}, definition-focused enumerate style
   - Problem sets: Adapted to countermodel exercises (no derivations)

3. sec:TenseModality (Bimodal Logic: Tense and Modality) unchanged
   - Remains as source reference in LogicNotes.tex

Rationale:
- Uniform presentation of bimodal logic focusing on definitions in consistent notation
- Exercise focus on semantic evaluation rather than proof construction
- First-order logic relocated to supplementary materials for streamlined main document

Files modified:
- LogicNotes.tex (sec:FirstOrder removed, sec:Bimodal replaced)
- additional/additional.tex (sec:FirstOrder added)

Files backed up:
- LogicNotes.tex.backup.[timestamp]
- additional/additional.tex.backup.[timestamp]
```

### No New Documentation Files

Following standards, NO new README or separate documentation files will be created. All documentation is inline comments and the single CHANGELOG_SECTION_RESTRUCTURE.txt file.

## Dependencies

### External Dependencies

**Required LaTeX Packages** (already in use):
- `enumitem` - for custom enumerate/itemize formatting (`[leftmargin=...]`)
- `amsmath`, `amssymb` - for mathematical symbols and environments
- `multicol` - for multi-column problem sets

**Custom Style Files** (project-local):
- `assets/notation.sty` - custom command definitions (operators, symbols)
- `assets/proof_styles.sty` - proof environment definitions (not used in replacement)

**Verification**: All packages already included in LogicNotes.tex preamble (Phase 1 test confirms compilation).

### Internal Dependencies

**File Dependencies:**
- `LogicNotes.tex` → reads `assets/notation.sty`, `assets/proof_styles.sty`
- `additional/additional.tex` → reads same style files (TEX root directive points to parent)

**Label Dependencies:**
- `\label{sec:FirstOrder}` must remain accessible (for any potential cross-references)
- `\label{sec:Bimodal}` must be preserved during replacement
- No circular dependencies between sections

**Custom Command Dependencies** (from notation.sty):
All commands used in replacement content must be defined before use:
- Temporal operators: `\Past`, `\Future`, `\past`, `\future`, `\always`, `\sometimes`
- Modal operators: `\Box`, `\Diamond`
- Task semantics: `\taskrel`, `\worldhist`, `\worldhistset`
- Language references: `\BL`, `\TML`, `\TMSystem`
- Metavariables: `\metaA`, `\metaB`
- Semantic consequence: `\MLmodels[]`

**Phase 1 verification confirms all commands defined in notation.sty.**

### Tool Dependencies

**Required Tools:**
- `pdflatex` - for document compilation
- `grep` - for verification testing
- `sed` - for line extraction and verification
- `wc` - for line counting
- Standard Unix utilities: `cp`, `cat`, `date`

**Availability**: All tools standard on Unix/Linux systems (project environment confirmed).

## Risk Mitigation

### Backup Strategy

**Before any modifications (Phase 1):**
- Create timestamped backups of LogicNotes.tex and additional/additional.tex
- Backups stored in project root with clear naming: `[filename].backup.$(date +%Y%m%d_%H%M%S)`
- Original sec:Bimodal content saved to separate file for reference: `sec_bimodal_original.tex`

**Rollback procedure** (if needed):
```bash
# Restore LogicNotes.tex
cp LogicNotes.tex.backup.[timestamp] LogicNotes.tex

# Restore additional.tex
cp additional/additional.tex.backup.[timestamp] additional/additional.tex
```

### Incremental Validation

**Compilation checkpoint after each phase:**
- Phase 2: Test additional.tex and LogicNotes.tex independently
- Phase 4: Test content fragments in minimal test document
- Phase 6: Test full LogicNotes.tex compilation immediately after replacement
- Phase 7: Comprehensive validation before declaring completion

**If compilation fails at any checkpoint:**
- Review error messages in .log file
- Identify undefined commands or malformed LaTeX
- Fix errors before proceeding to next phase
- Recompile to confirm fix
- If unable to fix: restore from backup and revise approach

### Content Validation

**Style preservation checks:**
- Verify enumerate leftmargin settings match original
- Verify bold label format consistent
- Verify semantic clause formatting maintained
- Manual visual inspection of PDF output

**Proof content exclusion:**
- Automated grep checks for proof keywords at multiple phases
- Manual review of extracted content before insertion
- Final verification in Phase 7 with sed extraction test

### Cross-Reference Integrity

**Label verification:**
- Test that `\label{sec:FirstOrder}` accessible in additional.tex
- Test that `\label{sec:Bimodal}` preserved at correct location
- Check compilation warnings for undefined references

**If label issues detected:**
- Verify label syntax correct (no typos)
- Ensure label not duplicated elsewhere
- Check that label appears after section header, not before

## Notes

### Complexity Calculation

```
Score = Base(refactor) + Tasks/2 + Files*3 + Integrations*5
Score = 5 + (38/2) + (2*3) + (0*5)
Score = 5 + 19 + 6 + 0
Score = 30

Adjusted for content transformation complexity:
Score = 30 + 17 (content extraction and reformatting effort)
Score = 47.0
```

**Tier Selection**: Score <50 → Tier 1 (single file plan)

### Progressive Planning

This plan starts as Level 0 (single file structure) per standards. Given the complexity score of 47.0 (below threshold of 50), the single-file structure is appropriate. The 7 phases are manageable without phase-level directory expansion.

**Note**: If during implementation any phase proves more complex than estimated (e.g., content reformatting in Phase 4 requires extensive iteration), the `/expand-phase` command can be used to break that phase into detailed sub-stages.

### Phase Dependencies

The dependency structure supports efficient sequential execution:
- Phase 1 (verification) has no dependencies - must run first
- Phase 2 (relocation) depends on Phase 1 (baseline established)
- Phases 3-5 (content extraction/adaptation) depend on Phase 2 (relocation complete)
- Phase 6 (replacement) depends on Phase 5 (adapted content ready)
- Phase 7 (verification) depends on Phase 6 (all changes made)

**No parallel execution opportunities** - phases must run sequentially due to file dependencies.

### Formatting Edge Cases

**Potential issues to watch for:**

1. **Metavariable scope in definitions:**
   - Ensure `\metaA`, `\metaB` used consistently
   - Verify subscripts and superscripts render correctly

2. **Enumerate nesting:**
   - Abbreviations may have nested sub-items
   - Test that leftmargin settings don't conflict with nesting

3. **Itemize in semantic clauses:**
   - Small font `\small` must be applied correctly
   - Item spacing may need adjustment for readability

4. **Multicol in problem sets:**
   - Ensure column breaks don't split individual exercises awkwardly
   - Test that multicol environment closes properly

**Resolution**: Phase 4 includes fragment compilation test to catch these issues early.

### Custom Command Usage

All custom commands used in the replacement are already defined in notation.sty (verified in research report). The replacement content will use:

**From sec:TenseModality notation:**
- `\TML` (TM Language)
- `\taskrel` (task accessibility relation)
- `\worldhist` (world history)
- `\TMSystem` (TM formal system reference)

**From sec:Bimodal notation:**
- `\BL` (Bimodal language)
- `\Past`, `\Future`, `\Box`, `\Diamond`
- `\always`, `\sometimes`

**No new custom commands need to be defined** - all notation already established.
