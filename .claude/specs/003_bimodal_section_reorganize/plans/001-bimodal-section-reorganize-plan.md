# Bimodal Section Reorganization Implementation Plan

## Metadata
- **Date**: 2025-12-02
- **Feature**: Reorganize sec:Bimodal to follow standard four-part organizational pattern
- **Scope**: Consolidate three redundant bimodal sections into one unified section with subsections for Syntax, Semantics, Proof Theory, and Metalogic, following the organizational pattern established in First-Order Logic and Tense Logic sections
- **Estimated Phases**: 6
- **Estimated Hours**: 8-12 hours
- **Standards File**: /home/benjamin/Documents/Philosophy/Teaching/LogicNotes/CLAUDE.md
- **Status**: [COMPLETE]
- **Research Reports**:
  - [Structural Analysis Report](../reports/001-structural-analysis.md)
- **Complexity Score**: 68.0
- **Structure Level**: 0

## Overview

This plan reorganizes the bimodal logic material currently spread across three sections into one cohesive section following the standard organizational pattern. The research report identified significant redundancy (3 WFF definitions, 2 task semantics treatments, 3 logical consequence definitions) and structural problems (syntax mixed with semantics, proof theory and metalogic missing from sec:Bimodal). The reorganization will eliminate redundancy while preserving all task semantics content that was recently added.

## Research Summary

The structural analysis revealed:
- **Standard Pattern**: First-Order Logic and Tense Logic sections follow a consistent four-part pattern: Syntax, Semantics (with Frames when applicable), Proof Theory, and Metalogic
- **Current Problems**: Three separate bimodal sections with redundant content, syntax mixed with semantics, proof theory and metalogic missing from main sec:Bimodal
- **Key Content to Preserve**: Task semantics framework (task frames, world histories, task coherence), perpetuity principles with proofs, extensions with open futures/pasts operators
- **Recommended Structure**: Single unified section with four subsections following established pattern, extensions moved to separate advanced section

## Success Criteria
- [ ] All three current bimodal sections consolidated into single sec:Bimodal with four subsections
- [ ] No redundant definitions (single WFF definition, single task semantics treatment, single logical consequence definition)
- [ ] Section follows standard pattern: Syntax → Semantics → Proof Theory → Metalogic
- [ ] All task semantics content preserved (task frames, world histories, coherence constraints)
- [ ] All perpetuity principles and proofs preserved
- [ ] Extensions content moved to separate sec:BimodalExtensions
- [ ] Label sec:Bimodal points to unified section (currently points to old Task Semantics section)
- [ ] Label sec:TenseModality removed (content integrated into sec:Bimodal)
- [ ] Document compiles without errors
- [ ] All problem sets preserved in appropriate subsections

## Technical Design

### Architecture Overview

The reorganization will transform:
```
CURRENT STRUCTURE:
  Section: Propositional Bimodal Logic: Task Semantics (sec:Bimodal, lines 1041-1088)
    - Language, WFF, abbreviations
    - Task frames, world histories, task models
    - Semantics, logical consequence
    - Problem set

  Section: Propositional Bimodal Logic: Extensions (lines 1150-1225)
    - Extended WFF (redundant)
    - Additional operators (Inevitably, Openpast, Openfuture)
    - Extended semantics
    - Problem set

  Section: Bimodal Logic: Tense and Modality (sec:TenseModality, lines 1244-1776+)
    - TM Logic: Syntax (lines 1257-1290)
    - TM Logic: Axiomatic System (lines 1300-1377)
    - TM Logic: Task Semantics (lines 1480-1658)
    - TM Logic: Metatheory (lines 1659-1775)
    - TM Logic: Extensions (lines 1776+)
    - Problem sets throughout

INTO NEW STRUCTURE:
  Section: Bimodal Logic: Tense and Modality (sec:Bimodal, unified section)
    Subsection 1: Bimodal Logic: Syntax
      - Language definition
      - Well-formed sentences
      - Abbreviations
      - Informal interpretation
      - Scope conventions
      - Problem Set: Syntax

    Subsection 2: Bimodal Logic: Semantics
      - Task frames (with nullity and compositionality)
      - World histories (with convexity and coherence)
      - Task models
      - Semantic clauses
      - Truth and validity
      - Problem Set: Semantics

    Subsection 3: Bimodal Logic: Axiomatic System
      - TM proof system definition
      - Propositional axioms
      - Modal axioms (S5: MT, M4, MB, MF)
      - Temporal axioms (TD, TK, TL, T4, TA, TF)
      - Perpetuity principles with proofs
      - Problem Set: Derivations

    Subsection 4: Bimodal Logic: Metatheory
      - Logical consequence for task models
      - Soundness theorem
      - Completeness theorem
      - Problem Set: Metatheory

  Section: Bimodal Logic: Extensions (sec:BimodalExtensions, separate section)
    - Extended language with Inevitably, Openpast, Openfuture
    - Intersection, open futures, open pasts definitions
    - Extended semantic clauses
    - Extended consequence relation
    - Problem Set: Extensions
```

### Implementation Strategy

**Phase-by-Phase Approach**:
1. **Phase 1**: Create backup and reorganize Syntax subsection
2. **Phase 2**: Reorganize Semantics subsection (preserving task semantics)
3. **Phase 3**: Reorganize Proof Theory subsection (axiomatic system)
4. **Phase 4**: Reorganize Metalogic subsection
5. **Phase 5**: Create separate Extensions section
6. **Phase 6**: Remove old sections, update labels, verify compilation

**Content Source Mapping**:
- Syntax: TM Syntax (lines 1260-1289) + scope conventions from Task Semantics (line 1065)
- Semantics: Task Semantics (lines 1067-1087) + truth/validity from TM Semantics
- Proof Theory: TM Axiomatic System (lines 1302-1377)
- Metalogic: Task Semantics consequence (line 1087) + TM Metatheory (lines 1659-1775)
- Extensions: Current Extensions section (lines 1153-1225) + TM Extensions (lines 1776+)

**Label Management**:
- Retain `\label{sec:Bimodal}` on unified section header
- Remove `\label{sec:TenseModality}` (no longer needed)
- Add `\label{sec:BimodalExtensions}` for extensions section
- Verify no other cross-references to sec:TenseModality exist

## Implementation Phases

### Phase 1: Create Backup and Reorganize Syntax Subsection [COMPLETE]
dependencies: []

**Objective**: Create timestamped backup and reorganize the Syntax subsection as first component of unified sec:Bimodal

**Complexity**: Low

**Tasks**:
- [x] Create timestamped backup (file: /home/benjamin/Documents/Philosophy/Teaching/LogicNotes/LogicNotes.tex.backup.YYYYMMDD_HHMMSS)
- [x] Locate current sec:Bimodal section (line 1041)
- [x] Replace section header with unified title: `\section*{\sc Bimodal Logic: Tense and Modality}`
- [x] Ensure `\label{sec:Bimodal}` remains on unified section header
- [x] Add organizational metadata comment documenting structure and content sources
- [x] Create Syntax subsection header: `\section*{\sc Bimodal Logic: Syntax}`
- [x] Extract language definition from TM Syntax (lines 1260-1263)
- [x] Extract WFF definition from TM Syntax (lines 1266-1270)
- [x] Extract abbreviations from TM Syntax (lines 1272-1280)
- [x] Extract informal interpretation from TM Syntax (lines 1282-1289)
- [x] Add scope conventions from current Task Semantics (line 1065)
- [x] Preserve Problem Set: Syntax from TM section
- [x] Verify subsection compiles without errors

**Testing**:
```bash
# Compile LaTeX to verify syntax subsection
cd /home/benjamin/Documents/Philosophy/Teaching/LogicNotes
pdflatex LogicNotes.tex 2>&1 | grep -i error

# Check backup created
test -f LogicNotes.tex.backup.* && echo "Backup exists" || echo "ERROR: No backup"

# Verify label exists
grep -n "label{sec:Bimodal}" LogicNotes.tex

# Count WFF definitions (should be reducing)
grep -c "well-formed sentences" LogicNotes.tex
```

**Expected Duration**: 1.5 hours

### Phase 2: Reorganize Semantics Subsection [COMPLETE]
dependencies: [1]

**Objective**: Reorganize Semantics subsection preserving all task semantics content

**Complexity**: Medium

**Tasks**:
- [x] Create Semantics subsection header: `\section*{\sc Bimodal Logic: Semantics}`
- [x] Extract task frame definition from current Task Semantics (lines 1067-1071, including nullity and compositionality conditions)
- [x] Extract world history definition from current Task Semantics (line 1073, including convexity and coherence)
- [x] Extract task model definition from current Task Semantics (line 1075)
- [x] Extract semantic clauses from current Task Semantics (lines 1077-1085, including Box operator task quantification)
- [x] Add truth and validity definitions from TM Semantics section
- [x] Preserve all mathematical notation (task relation symbols, world history functions)
- [x] Preserve Problem Set: Semantics from Task Semantics section
- [x] Add inline comments explaining task coherence constraint
- [x] Verify all task semantics content preserved (compare with backup)

**Testing**:
```bash
# Verify task frame content preserved
grep -A 5 "task frame" LogicNotes.tex | grep -q "nullity" && echo "Task frame preserved" || echo "ERROR: Missing task frame content"

# Verify world history preserved
grep -q "world history" LogicNotes.tex && echo "World history preserved" || echo "ERROR: Missing world history"

# Verify semantic clauses preserved
grep -c "\\\\models" LogicNotes.tex

# Compile to check for errors
pdflatex LogicNotes.tex 2>&1 | grep -i error
```

**Expected Duration**: 2 hours

### Phase 3: Reorganize Proof Theory Subsection [COMPLETE]
dependencies: [2]

**Objective**: Reorganize Proof Theory subsection with complete TM axiomatic system

**Complexity**: Medium

**Tasks**:
- [x] Create Axiomatic System subsection header: `\section*{\sc Bimodal Logic: Axiomatic System}`
- [x] Extract TM proof system definition from TM Axiomatic System (lines 1302-1303)
- [x] Extract propositional axioms from TM Axiomatic System (lines 1305-1310)
- [x] Extract modal axioms (S5: MT, M4, MB, MF) from TM Axiomatic System (lines 1312-1323)
- [x] Extract temporal axioms (TD, TK, TL, T4, TA, TF) from TM Axiomatic System (lines 1325-1336)
- [x] Extract perpetuity principles (P1-P6) with complete proofs from TM Axiomatic System (lines 1338-1377)
- [x] Preserve all proof environments and derivation formatting
- [x] Preserve Problem Set: Derivations from TM section
- [x] Verify all axioms and proofs preserved (compare with backup)

**Testing**:
```bash
# Verify modal axioms present
grep -c "\\\\textbf{MT}" LogicNotes.tex

# Verify temporal axioms present
grep -c "\\\\textbf{TD}" LogicNotes.tex

# Verify perpetuity principles present
grep -c "\\\\textbf{P[1-6]}" LogicNotes.tex

# Verify proofs preserved
grep -c "\\\\begin{proof}" LogicNotes.tex

# Compile to check for errors
pdflatex LogicNotes.tex 2>&1 | grep -i error
```

**Expected Duration**: 2 hours

### Phase 4: Reorganize Metalogic Subsection [COMPLETE]
dependencies: [3]

**Objective**: Reorganize Metalogic subsection with soundness and completeness theorems

**Complexity**: Medium

**Tasks**:
- [x] Create Metatheory subsection header: `\section*{\sc Bimodal Logic: Metatheory}`
- [x] Extract logical consequence definition from current Task Semantics (line 1087)
- [x] Extract soundness theorem from TM Metatheory (lines 1659+)
- [x] Extract completeness theorem from TM Metatheory
- [x] Extract decidability results from TM Metatheory (if present)
- [x] Preserve all theorem environments and proof references
- [x] Preserve Problem Set: Metatheory from TM section
- [x] Add cross-references connecting metatheory to proof system and semantics
- [x] Verify all metatheoretic content preserved (compare with backup)

**Testing**:
```bash
# Verify logical consequence definition
grep -q "logical consequence" LogicNotes.tex && echo "Consequence definition present" || echo "ERROR: Missing consequence"

# Verify soundness theorem
grep -q "soundness" LogicNotes.tex && echo "Soundness present" || echo "ERROR: Missing soundness"

# Verify completeness theorem
grep -q "completeness" LogicNotes.tex && echo "Completeness present" || echo "ERROR: Missing completeness"

# Compile to check for errors
pdflatex LogicNotes.tex 2>&1 | grep -i error
```

**Expected Duration**: 2 hours

### Phase 5: Create Separate Extensions Section [COMPLETE]
dependencies: [4]

**Objective**: Create separate sec:BimodalExtensions section for advanced material

**Complexity**: Low

**Tasks**:
- [x] Create new section header after unified sec:Bimodal: `\section*{\sc Bimodal Logic: Extensions}`
- [x] Add label: `\label{sec:BimodalExtensions}`
- [x] Extract extended language definition from current Extensions (lines 1153-1166)
- [x] Extract intersection, open futures, open pasts definitions from current Extensions (lines 1177-1179)
- [x] Extract extended semantic clauses from current Extensions (lines 1181-1193)
- [x] Extract extended consequence relation from current Extensions (line 1194)
- [x] Preserve Problem Set: Extensions from current Extensions (lines 1199-1225)
- [x] Extract additional extensions from TM Extensions section (lines 1776+) if applicable
- [x] Add introductory text explaining extensions build on core system
- [x] Verify all extensions content preserved

**Testing**:
```bash
# Verify extensions section exists
grep -q "label{sec:BimodalExtensions}" LogicNotes.tex && echo "Extensions section created" || echo "ERROR: Missing extensions section"

# Verify extended operators preserved
grep -q "Inevitably" LogicNotes.tex && echo "Extended operators present" || echo "ERROR: Missing extended operators"

# Verify extended semantics preserved
grep -q "open futures" LogicNotes.tex && echo "Open futures present" || echo "ERROR: Missing open futures"

# Compile to check for errors
pdflatex LogicNotes.tex 2>&1 | grep -i error
```

**Expected Duration**: 1.5 hours

### Phase 6: Remove Old Sections, Update Labels, Verify Compilation [COMPLETE]
dependencies: [5]

**Objective**: Remove old redundant sections, clean up labels, verify document integrity

**Complexity**: Low

**Tasks**:
- [x] Remove old "Propositional Bimodal Logic: Task Semantics" section (lines 1041-1088) - content now in unified sec:Bimodal
- [x] Remove old "Propositional Bimodal Logic: Extensions" section (lines 1150-1225) - content now in sec:BimodalExtensions
- [x] Remove old "Bimodal Logic: Tense and Modality" section (lines 1244-1776+) - content now in unified sec:Bimodal
- [x] Remove `\label{sec:TenseModality}` label (no longer needed)
- [x] Search for cross-references to sec:TenseModality and update to sec:Bimodal
- [x] Verify no redundant WFF definitions remain (grep check)
- [x] Verify no redundant task semantics treatments remain (grep check)
- [x] Verify no redundant logical consequence definitions remain (grep check)
- [x] Full document compilation test (pdflatex)
- [x] Visual inspection of PDF output for formatting issues
- [x] Verify problem sets all present and correctly positioned
- [x] Create final comparison with backup showing reduction in redundancy

**Testing**:
```bash
# Count WFF definitions (should be 1 in bimodal section)
grep -n "well-formed" LogicNotes.tex | grep -i bimodal | wc -l

# Verify no sec:TenseModality label remains
grep -c "label{sec:TenseModality}" LogicNotes.tex

# Verify sec:Bimodal points to unified section
grep -B 2 "label{sec:Bimodal}" LogicNotes.tex

# Full compilation test
pdflatex LogicNotes.tex && pdflatex LogicNotes.tex && echo "Compilation successful" || echo "ERROR: Compilation failed"

# Check for undefined references
grep -i "undefined" LogicNotes.log

# Check for multiply defined labels
grep -i "multiply defined" LogicNotes.log

# Compare file sizes (should be similar or smaller)
wc -l LogicNotes.tex LogicNotes.tex.backup.*
```

**Expected Duration**: 1 hour

## Testing Strategy

### Unit Testing (Per Phase)
- Each phase includes immediate compilation test after changes
- Grep-based verification of content preservation
- Label verification to ensure cross-references remain valid
- Incremental approach allows isolating errors to specific phases

### Integration Testing (Phase 6)
- Full document compilation (multiple passes for cross-references)
- Log file analysis for undefined references or multiply defined labels
- Visual PDF inspection for formatting consistency
- Comparison with backup to verify reduction in redundancy

### Regression Testing
- Verify all problem sets preserved and correctly positioned
- Verify all mathematical notation renders correctly
- Verify all cross-references resolve (no "??" in output)
- Verify table of contents structure (if present)

### Success Metrics
- Document compiles without errors (exit code 0)
- No undefined references in .log file
- No multiply defined labels in .log file
- Single WFF definition in bimodal section (grep count = 1)
- Single task semantics treatment (grep count = 1)
- Single logical consequence definition in metatheory (grep count = 1)
- All problem sets present (manual count matches original)

## Documentation Requirements

### Inline Documentation
- Add organizational metadata comment at top of unified sec:Bimodal documenting structure and content sources (as specified in Recommendation 4 of research report)
- Add inline comments explaining task coherence constraint in semantics subsection
- Preserve all existing LaTeX comments from source sections

### Commit Message
```
Reorganize bimodal section to follow standard pattern

Consolidate three redundant bimodal sections into single unified
sec:Bimodal with four subsections: Syntax, Semantics, Proof Theory,
and Metalogic. Move extensions to separate sec:BimodalExtensions.

Eliminates redundancy:
- 3 WFF definitions → 1
- 2 task semantics treatments → 1
- 3 logical consequence definitions → 1

Preserves all task semantics content (task frames, world histories,
coherence constraints) and perpetuity principles with proofs.

Follows pattern established in First-Order Logic and Tense Logic
sections for consistency.
```

### Change Log Entry
Document reorganization in CHANGELOG.md (if exists) or add comment in LogicNotes.tex header:
```
% 2025-12-02: Reorganized bimodal section (sec:Bimodal) to follow standard
% four-part pattern (Syntax, Semantics, Proof Theory, Metalogic). Consolidated
% three separate sections, eliminated redundancy, preserved all task semantics
% content. Extensions moved to sec:BimodalExtensions.
```

## Dependencies

### External Dependencies
- LaTeX distribution with standard packages (assumed installed)
- pdflatex compiler for testing
- Custom LaTeX packages: notation.sty, proof_styles.sty (located in /home/benjamin/Documents/Philosophy/Teaching/LogicNotes/assets/)

### Content Dependencies
- Original sections must remain unchanged until respective phases complete
- Backup must be created before any modifications (Phase 1 prerequisite)
- Phase dependencies enforce sequential execution (no parallel phases)

### Cross-Reference Dependencies
- Any external references to sec:TenseModality must be updated to sec:Bimodal
- Internal cross-references within bimodal material must be verified after reorganization
- Problem set references to subsections must be updated if numbering changes

## Risk Mitigation

### Risk 1: Content Loss During Reorganization
- **Mitigation**: Timestamped backup created in Phase 1
- **Mitigation**: Incremental verification after each phase using grep checks
- **Mitigation**: Final comparison in Phase 6 confirms all content preserved

### Risk 2: Broken Cross-References
- **Mitigation**: Explicit label management (retain sec:Bimodal, remove sec:TenseModality)
- **Mitigation**: Search for all references to sec:TenseModality before removal
- **Mitigation**: Multiple LaTeX compilation passes to resolve cross-references

### Risk 3: LaTeX Compilation Errors
- **Mitigation**: Test compilation after each phase
- **Mitigation**: Use .log file analysis to identify specific errors
- **Mitigation**: Backup enables rollback if unrecoverable errors occur

### Risk 4: Mathematical Notation Corruption
- **Mitigation**: Copy-paste preservation of complex LaTeX environments (proofs, derivations)
- **Mitigation**: Visual PDF inspection in Phase 6
- **Mitigation**: Verify custom package imports (notation.sty, proof_styles.sty) remain intact

## Notes

### Organizational Philosophy
This reorganization prioritizes pedagogical clarity and structural consistency over preserving the historical development of the material. The standard four-part pattern (Syntax → Semantics → Proof Theory → Metalogic) aids student learning by establishing predictable organization across modal logic topics.

### Task Semantics as Core Framework
The task semantics approach is theoretically distinctive and should remain central to the bimodal logic presentation. This reorganization does not change the semantic framework—it only reorganizes how that framework is presented to eliminate redundancy and improve clarity.

### Extensions as Advanced Material
Moving extensions to a separate section clearly marks them as advanced material while preserving their pedagogical value. Students can complete the core bimodal logic material before engaging with extended operators (Inevitably, Openpast, Openfuture).

### Incremental Approach Benefits
The phase-by-phase approach with verification at each step reduces risk and enables precise error localization. If compilation errors occur, the most recent phase can be isolated and debugged without affecting earlier work.
