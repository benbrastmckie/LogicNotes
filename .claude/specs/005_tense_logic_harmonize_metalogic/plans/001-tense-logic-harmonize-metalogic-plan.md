# Tense Logic Harmonization and Metalogic Restructuring Implementation Plan

## Metadata
- **Date**: 2025-12-02
- **Feature**: Harmonize tense logic axiom system with possible_worlds.tex and restructure bimodal metalogic section
- **Scope**: Replace TK axiom with TK rule (matching FN), remove metalogic proofs to problem set, remove completeness section entirely
- **Estimated Phases**: 4
- **Estimated Hours**: 3-5 hours
- **Standards File**: /home/benjamin/Documents/Philosophy/Teaching/LogicNotes/.claude/CLAUDE.md
- **Status**: [COMPLETE]
- **Complexity Score**: 42.5
- **Structure Level**: 0
- **Research Reports**:
  - [Tense Logic Harmonization Research Report](../reports/001-research-report.md)

## Overview

This plan harmonizes the tense logic axiomatic system in LogicNotes.tex with the appendix conventions in possible_worlds.tex, and restructures the bimodal metalogic section to be more pedagogically appropriate for teaching notes. The main changes are:

1. **TK Axiom → TK Rule**: Replace the TK axiom schema with the TK rule (renaming the current FN rule), matching the appendix format in possible_worlds.tex where TK is defined as a rule rather than an axiom
2. **Metalogic Proofs → Problem Set**: Remove the three proof sketches (MP, MK, MF) from the soundness section and convert them into problem set exercises
3. **Remove Completeness Section**: Delete the entire completeness theorem, proof strategy, and Truth Lemma discussion to match the appendix structure in possible_worlds.tex

These changes align the teaching notes with the research paper's appendix structure while making the metalogic section more suitable for student engagement through problem solving rather than passive reading of completed proofs.

## Research Summary

The research report identified the following key findings:

- **TK Definition Discrepancy**: LogicNotes.tex defines TK as an axiom schema (line 969: $\Future(\metaA\rightarrow \metaB)\rightarrow(\Future \metaA\rightarrow\Future \metaB)$) while possible_worlds.tex defines it as a rule (line 2324: "If $\Gamma \vDash \varphi$, then $\Future\Gamma \vDash \Future\varphi$")
- **FN Rule Equivalence**: The current FN rule in LogicNotes.tex (lines 977-981) has the exact same formulation as the TK rule in possible_worlds.tex, confirming they are the same inference rule
- **Derivability**: The axiom version of TK is derivable from the rule version plus modus ponens, so no logical content is lost by the change
- **Metalogic Structure**: The appendix in possible_worlds.tex does not include a completeness section, focusing instead on semantic definitions, validity proofs, derivations, and soundness proofs
- **Proof Sketches Found**: Three proof sketches in LogicNotes.tex (MP, MK, MF) at lines 1303-1314 that should become problem set exercises
- **Completeness Section**: Lines 1318-1333 contain the full completeness discussion to be removed

Recommended approach: Make targeted edits to the tense logic axiomatic system section and the bimodal metalogic section, then expand the problem set with new soundness proof exercises.

## Success Criteria

- [ ] TK axiom schema removed from tense logic axiom schemata enumeration (line 969)
- [ ] FN rule renamed to TK rule with updated description matching possible_worlds.tex format
- [ ] All references to TK updated to reflect it as a rule rather than an axiom (lines 983, 985)
- [ ] All references to FN updated to TK throughout the document
- [ ] Soundness proof sketches for MP, MK, MF removed from metalogic section (lines 1302-1314)
- [ ] Explanatory text about remaining axioms removed (lines 1315-1316)
- [ ] Completeness theorem statement and proof strategy removed entirely (lines 1318-1333)
- [ ] Metalogical Consequences section preserved (lines 1334-1340)
- [ ] New problem set exercises added for soundness proofs (MP, MK, MF, and optional additional axioms)
- [ ] Document compiles without LaTeX errors
- [ ] All mathematical notation remains consistent and correct
- [ ] Changes exactly match the appendix structure in possible_worlds.tex

## Technical Design

### Architecture

This is a documentation refactoring task involving LaTeX source files. The changes are localized to two main sections:

1. **Tense Logic Axiomatic System** (lines 964-989): Remove TK axiom, rename FN to TK, update references
2. **Bimodal Metalogic** (lines 1296-1343): Remove proof sketches and completeness section, preserve soundness theorem statement and metalogical consequences

### Component Interactions

- The tense logic axiom system section defines the formal proof system that is used in later sections
- The bimodal metalogic section builds on both the modal and tense logic systems
- The problem set section provides exercises based on the metalogic theorems
- Changes to axiom/rule names must be reflected consistently across all three sections

### Design Decisions

**Decision 1: Remove TK axiom rather than keep both**
- Rationale: The axiom version is derivable from the rule, keeping both would be redundant and confusing
- Alternative considered: Keep both and note the derivability relationship
- Chosen approach: Follow possible_worlds.tex conventions exactly (rule only, named TK)

**Decision 2: Convert proofs to problem set exercises rather than remove entirely**
- Rationale: Pedagogically valuable for students to work through proofs themselves; preserves educational content while making it more engaging
- Alternative considered: Remove proofs entirely and just state theorems
- Chosen approach: Move proofs to problem set as guided exercises with hints

**Decision 3: Remove completeness section entirely rather than simplify**
- Rationale: Matches possible_worlds.tex appendix structure; completeness proofs are significantly more complex than soundness and may exceed scope of teaching notes
- Alternative considered: Provide simplified completeness proof sketch
- Chosen approach: Remove section completely, keep mention in metalogical consequences

### File Structure

Changes affect single file:
- `/home/benjamin/Documents/Philosophy/Teaching/LogicNotes/LogicNotes.tex`

No new files created, no files deleted.

## Implementation Phases

### Phase 1: Replace TK Axiom with TK Rule [COMPLETE]
dependencies: []

**Objective**: Remove the TK axiom schema and rename the FN rule to TK, matching the convention in possible_worlds.tex appendix.

**Complexity**: Low

**Tasks**:
- [x] Remove TK axiom from the enumeration at line 969 (file: /home/benjamin/Documents/Philosophy/Teaching/LogicNotes/LogicNotes.tex)
- [x] Rename "Future Necessitation Rule" to "TK Rule" at line 977 (file: /home/benjamin/Documents/Philosophy/Teaching/LogicNotes/LogicNotes.tex)
- [x] Update the rule label from "FN" to "TK" at line 979 (file: /home/benjamin/Documents/Philosophy/Teaching/LogicNotes/LogicNotes.tex)
- [x] Update TL System description at line 983 to list TK as a rule rather than an axiom (file: /home/benjamin/Documents/Philosophy/Teaching/LogicNotes/LogicNotes.tex)
- [x] Update Tense Proofs definition at line 985 to reference "TK" rule instead of "FN" rule (file: /home/benjamin/Documents/Philosophy/Teaching/LogicNotes/LogicNotes.tex)
- [x] Verify that the rule formulation matches possible_worlds.tex line 2324 format (file: /home/benjamin/Documents/Philosophy/Teaching/LogicNotes/LogicNotes.tex)

**Testing**:
```bash
# Verify TK no longer appears as an axiom
grep -n "\\\\item\[\\\\bf TK\]" /home/benjamin/Documents/Philosophy/Teaching/LogicNotes/LogicNotes.tex

# Verify TK now appears as a rule
grep -n "TK Rule" /home/benjamin/Documents/Philosophy/Teaching/LogicNotes/LogicNotes.tex

# Verify no references to FN remain
grep -n "\\bFN\\b" /home/benjamin/Documents/Philosophy/Teaching/LogicNotes/LogicNotes.tex

# Compile LaTeX to ensure no errors
cd /home/benjamin/Documents/Philosophy/Teaching/LogicNotes && pdflatex LogicNotes.tex
```

**Expected Duration**: 1 hour

### Phase 2: Remove Metalogic Proof Sketches [COMPLETE]
dependencies: [1]

**Objective**: Remove the proof sketches for MP, MK, and MF from the soundness section, preserving only the soundness theorem statement and description.

**Complexity**: Low

**Tasks**:
- [x] Remove the entire "Soundness Proof Sketch" enumeration (lines 1302-1314) while preserving the surrounding structure (file: /home/benjamin/Documents/Philosophy/Teaching/LogicNotes/LogicNotes.tex)
- [x] Remove the explanatory text about remaining axioms (lines 1315-1316) (file: /home/benjamin/Documents/Philosophy/Teaching/LogicNotes/LogicNotes.tex)
- [x] Verify that the soundness theorem statement (lines 1296-1298) remains intact (file: /home/benjamin/Documents/Philosophy/Teaching/LogicNotes/LogicNotes.tex)
- [x] Ensure the transition from soundness theorem to the next section (completeness or metalogical consequences after Phase 3) is smooth (file: /home/benjamin/Documents/Philosophy/Teaching/LogicNotes/LogicNotes.tex)

**Testing**:
```bash
# Verify proof sketches removed
grep -n "Case MP:" /home/benjamin/Documents/Philosophy/Teaching/LogicNotes/LogicNotes.tex
grep -n "Case MK:" /home/benjamin/Documents/Philosophy/Teaching/LogicNotes/LogicNotes.tex
grep -n "Case MF:" /home/benjamin/Documents/Philosophy/Teaching/LogicNotes/LogicNotes.tex

# Verify soundness theorem statement still present
grep -n "Soundness Theorem:" /home/benjamin/Documents/Philosophy/Teaching/LogicNotes/LogicNotes.tex

# Compile LaTeX to ensure structure is valid
cd /home/benjamin/Documents/Philosophy/Teaching/LogicNotes && pdflatex LogicNotes.tex
```

**Expected Duration**: 0.5 hours

### Phase 3: Remove Completeness Section [COMPLETE]
dependencies: [2]

**Objective**: Remove the entire completeness theorem, proof strategy, and Truth Lemma discussion from the metalogic section.

**Complexity**: Low

**Tasks**:
- [x] Remove the completeness theorem statement (line 1318) (file: /home/benjamin/Documents/Philosophy/Teaching/LogicNotes/LogicNotes.tex)
- [x] Remove the completeness theorem description (lines 1320-1321) (file: /home/benjamin/Documents/Philosophy/Teaching/LogicNotes/LogicNotes.tex)
- [x] Remove the completeness proof strategy section (lines 1322-1330) (file: /home/benjamin/Documents/Philosophy/Teaching/LogicNotes/LogicNotes.tex)
- [x] Remove the Truth Lemma and final completeness argument (lines 1331-1333) (file: /home/benjamin/Documents/Philosophy/Teaching/LogicNotes/LogicNotes.tex)
- [x] Verify that the metalogical consequences section (lines 1334-1340) immediately follows the soundness section (file: /home/benjamin/Documents/Philosophy/Teaching/LogicNotes/LogicNotes.tex)
- [x] Update the metalogical consequences text to remove references to "soundness and completeness theorems" if needed, replacing with just "soundness theorem" or similar phrasing (file: /home/benjamin/Documents/Philosophy/Teaching/LogicNotes/LogicNotes.tex)

**Testing**:
```bash
# Verify completeness section removed
grep -n "Completeness Theorem:" /home/benjamin/Documents/Philosophy/Teaching/LogicNotes/LogicNotes.tex
grep -n "Truth Lemma" /home/benjamin/Documents/Philosophy/Teaching/LogicNotes/LogicNotes.tex
grep -n "canonical model" /home/benjamin/Documents/Philosophy/Teaching/LogicNotes/LogicNotes.tex

# Verify metalogical consequences section still present
grep -n "Metalogical Consequences:" /home/benjamin/Documents/Philosophy/Teaching/LogicNotes/LogicNotes.tex

# Compile LaTeX to ensure document structure is valid
cd /home/benjamin/Documents/Philosophy/Teaching/LogicNotes && pdflatex LogicNotes.tex
```

**Expected Duration**: 0.5 hours

### Phase 4: Add Soundness Proof Exercises to Problem Set [COMPLETE]
dependencies: [2]

**Objective**: Expand the "Problem Set: Metatheory" section with new exercises for soundness proofs, converting the removed proof sketches into student exercises.

**Complexity**: Medium

**Tasks**:
- [x] Add a new "Soundness Proofs" item to the problem set enumeration (after line 1347, before "Axiom Validity") (file: /home/benjamin/Documents/Philosophy/Teaching/LogicNotes/LogicNotes.tex)
- [x] Create sub-exercise for MP soundness proof with hint about validity preservation (file: /home/benjamin/Documents/Philosophy/Teaching/LogicNotes/LogicNotes.tex)
- [x] Create sub-exercise for MK axiom validity proof with hint about Box operator semantics (file: /home/benjamin/Documents/Philosophy/Teaching/LogicNotes/LogicNotes.tex)
- [x] Create sub-exercise for MF bimodal axiom validity proof with hint about history and time interaction (file: /home/benjamin/Documents/Philosophy/Teaching/LogicNotes/LogicNotes.tex)
- [x] Add optional challenge exercise for additional axioms (MT, M4, MB, TD, TL, T4, TA, TF) allowing students to choose two (file: /home/benjamin/Documents/Philosophy/Teaching/LogicNotes/LogicNotes.tex)
- [x] Format exercises consistently with existing problem set style (enumerate with labels, small font, appropriate hints) (file: /home/benjamin/Documents/Philosophy/Teaching/LogicNotes/LogicNotes.tex)
- [x] Verify that new exercises integrate smoothly with existing "Axiom Validity", "Consistency", and "Countermodels" problems (file: /home/benjamin/Documents/Philosophy/Teaching/LogicNotes/LogicNotes.tex)

**Testing**:
```bash
# Verify new soundness proof exercises added
grep -n "Soundness Proofs:" /home/benjamin/Documents/Philosophy/Teaching/LogicNotes/LogicNotes.tex

# Verify exercises reference MP, MK, MF
grep -n "Modus ponens preserves validity" /home/benjamin/Documents/Philosophy/Teaching/LogicNotes/LogicNotes.tex

# Count problem set items to ensure one was added
grep -c "\\\\item\[\\\\bf" /home/benjamin/Documents/Philosophy/Teaching/LogicNotes/LogicNotes.tex

# Compile LaTeX to ensure formatting is correct
cd /home/benjamin/Documents/Philosophy/Teaching/LogicNotes && pdflatex LogicNotes.tex

# Visual inspection of PDF to verify problem set formatting
# (Open generated PDF and review problem set section)
```

**Expected Duration**: 1.5 hours

## Testing Strategy

### Unit Testing
Each phase includes specific LaTeX compilation tests to ensure:
- No syntax errors introduced
- Document structure remains valid
- Mathematical notation compiles correctly
- Cross-references remain functional

### Integration Testing
After all phases complete:
1. Full document compilation test with pdflatex
2. Visual inspection of generated PDF to verify:
   - Tense logic axiom system section displays correctly with TK as a rule
   - Bimodal metalogic section flows smoothly from soundness theorem to metalogical consequences
   - Problem set includes new soundness proof exercises with proper formatting
   - No orphaned references or broken cross-references
3. Comparison with possible_worlds.tex appendix to verify alignment:
   - TK rule formulation matches line 2324 format
   - Axiom/rule structure parallels appendix conventions
   - Overall presentation style is consistent

### Validation Testing
1. Mathematical correctness:
   - Verify all logical formulas are correctly formatted
   - Check that axiom/rule references are updated consistently
   - Ensure problem set exercises are mathematically sound
2. Pedagogical effectiveness:
   - Confirm problem set exercises provide appropriate scaffolding
   - Verify hints are helpful without giving away complete solutions
   - Check that exercise difficulty progression is appropriate

## Documentation Requirements

### Primary Documentation
- No separate documentation files need updating
- The LogicNotes.tex file serves as its own documentation

### Comments and Annotations
- No inline comments need to be added (LaTeX teaching document)
- Changes should be self-documenting through clear section structure

### Update Existing Documentation
- If a separate changelog or version history exists for LogicNotes.tex, add entry describing:
  - TK axiom → TK rule change
  - Removal of metalogic proof sketches
  - Removal of completeness section
  - Addition of soundness proof exercises to problem set

## Dependencies

### External Dependencies
- LaTeX distribution (pdflatex) for compilation testing
- Standard LaTeX packages used by LogicNotes.tex (enumitem, amsmath, etc.)

### Internal Dependencies
- `/home/benjamin/Documents/Philosophy/Teaching/LogicNotes/LogicNotes.tex` (file to be modified)
- `/home/benjamin/Documents/Philosophy/Papers/PossibleWorlds/JPL/possible_worlds.tex` (reference file for target format)

### Prerequisite Knowledge
- Understanding of tense logic and modal logic
- Familiarity with LaTeX editing and compilation
- Knowledge of the distinction between axioms and inference rules in formal systems
- Understanding of soundness vs completeness in formal logic

## Risk Assessment

### Low Risks
- **LaTeX compilation errors**: Mitigated by incremental compilation testing after each phase
- **Inconsistent notation**: Mitigated by careful verification against possible_worlds.tex
- **Problem set formatting issues**: Mitigated by following existing problem set style patterns

### Medium Risks
- **Accidental removal of essential content**: Mitigated by precise line number targeting and verification steps
- **Breaking mathematical logic**: Mitigated by verification that TK rule is logically equivalent to removed axiom

### Risk Mitigation
- Create backup of LogicNotes.tex before starting implementation
- Use version control (git) to track changes and enable rollback if needed
- Compile and visually inspect PDF after each phase to catch issues early
- Cross-reference with possible_worlds.tex throughout to ensure alignment
