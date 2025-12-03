# Section Restructuring Research Report

## Metadata
- **Date**: 2025-12-02
- **Agent**: research-specialist
- **Topic**: Section restructuring - move sec:FirstOrder to additional.tex, replace sec:Bimodal with sec:TenseModality content
- **Report Type**: codebase analysis
- **Complexity**: 3

## Executive Summary

This research analyzes the structural differences between sec:Bimodal and sec:TenseModality to enable systematic replacement of sec:Bimodal's content with sec:TenseModality's material while preserving sec:Bimodal's presentation style. The key finding is that sec:TenseModality follows a pedagogically-rich presentation including axiomatic systems, proof sketches, and task semantics (approximately 280 lines), while sec:Bimodal uses a concise definition-focused style emphasizing semantic foundations without proofs (approximately 150 lines). The replacement will require selective extraction from sec:TenseModality to match sec:Bimodal's focus on definitions and exercises while omitting detailed proofs.

## Findings

### Section Location and Structure Analysis

**sec:FirstOrder (First-Order Logic: Syntax)**
- **Location**: LogicNotes.tex:1191-1389 (approximately 198 lines)
- **Structure**: Four major subsections covering Syntax, Proof Theory, Semantics, and Metalogic
- **Content Type**: Complete first-order logic treatment with syntax definitions, proof rules, semantic clauses, and problem sets
- **Current Status**: Currently in main LogicNotes.tex, targeted for relocation to additional/additional.tex
- **Dependencies**: No internal cross-references to other sections; self-contained

**sec:Bimodal (Propositional Bimodal Logic: Task Semantics)**
- **Location**: LogicNotes.tex:1041-1183 (approximately 142 lines total)
- **Structure**: Two main sections:
  1. Task Semantics (lines 1041-1100): Core bimodal logic with task-based world histories
  2. Extensions (lines 1104-1180): Extended system with inevitability operators
- **Presentation Style**: Enumerate-based definitions with minimal prose, NO proofs or proof sketches
- **Key Features**:
  - Uses enumerate environment with `[leftmargin=1.2in]` formatting
  - Definitions presented in bold labels (e.g., `\item[\bf Well-Formed Sentences:]`)
  - Semantic clauses in itemize with `[leftmargin=.15in]\small` formatting
  - Problem sets following each major subsection
  - Focus on countermodel exercises rather than derivations

**sec:TenseModality (Bimodal Logic: Tense and Modality)**
- **Location**: LogicNotes.tex:1396-1674+ (approximately 280+ lines)
- **Structure**: Three major subsections:
  1. TM Logic: Syntax (lines 1409-1530): Language, well-formed sentences, abbreviations, and informal interpretations
  2. TM Logic: Axiomatic System (lines 1452-1530): Complete axiomatization with propositional, modal (S5), temporal, and interaction axioms, INCLUDES two proof sketches (P1 and P2)
  3. TM Logic: Task Semantics (lines 1632-1674+): Formal semantic framework with task frames, world histories, and validity definitions
- **Presentation Style**: Mixed format with prose introductions, enumerate definitions, Hilbert-style proof environment
- **Key Features**:
  - Natural language motivation at beginning
  - Axiomatic system with detailed proof sketches using `\begin{hilbert}...\end{hilbert}` environment
  - Two complete problem sets (TM Syntax and TM Derivations)
  - Task semantics section with sophisticated mathematical definitions
  - Uses custom commands: `\TMproves`, `\TMmodels`, `\taskframe`, `\worldhist`

### Content Comparison: What Must Be Preserved vs. Adapted

**Style Elements to Preserve from sec:Bimodal:**
1. Enumerate-based definition lists with `[leftmargin=1.2in]`
2. Bold labels for definition types (e.g., `\item[\bf Language:] `, `\item[\bf Frame:]`)
3. Minimal prose - definitions proceed directly without motivational paragraphs
4. NO proof sketches or derivations in main body
5. Problem sets focus on countermodels and semantic evaluation, NOT axiomatic derivations
6. Semantic clauses in compact itemize format with `[leftmargin=.15in]\small`

**Content to Extract from sec:TenseModality:**
1. **Syntax definitions** (lines 1411-1450):
   - Language definition with operators
   - Well-formed sentence grammar
   - Abbreviations (keep concise, consolidate)
   - Operator scope conventions
2. **Task semantics definitions** (lines 1632-1674):
   - Task frame structure
   - World history definition with convexity
   - Task model and interpretation
   - Truth conditions (semantic clauses)
   - Validity and logical consequence
3. **Problem Set: TM Syntax** (lines 1531-1582): Adapt for exercises

**Content to EXCLUDE from sec:TenseModality:**
1. Natural language motivation paragraph (lines 1399-1407)
2. Complete axiomatic system section (lines 1452-1530)
3. All Hilbert-style proof sketches (P1, P2, etc.)
4. Perpetuity principles as theorems (can mention as exercises)
5. Problem Set: TM Derivations (lines 1584-1630) - focuses on axiomatic proofs

### Notation and Styling Consistency

**Custom Commands Used in Both Sections:**
- From notation.sty:
  - `\BL` - Bimodal language (line 231 in notation.sty)
  - `\Past`, `\Future` - Temporal operators (lines 208-210)
  - `\Box`, `\Diamond` - Modal operators
  - `\always`, `\sometimes` - Compound temporal operators (lines 146-147)
  - `\Inevitably`, `\inevitably` - Inevitability operators (lines 215-216)
  - `\metaA`, `\metaB` - Metavariables (lines 267-269)
  - `\MLmodels[]` - Logical consequence symbol (line 155)

**Commands Specific to sec:TenseModality:**
- From notation.sty (lines 180-192):
  - `\TML` - TM Language
  - `\TMproves` - TM provability
  - `\TMmodels` - TM semantic consequence
  - `\TMSystem` - TM formal system
  - `\taskrel`, `\worldhist`, `\worldhistset` - Task semantics notation

**Formatting Conventions:**
- Section headers use `\section*{\sc Title}` with small caps
- Problem set headers use `\section*{\it Problem Set: Topic}`
- Enumerate lists have consistent leftmargin settings
- Semantic clauses use compact itemize with small font

### Additional Materials File Structure

**Current additional/additional.tex Structure:**
- **Location**: /home/benjamin/Documents/Philosophy/Teaching/LogicNotes/additional/additional.tex
- **Purpose**: Supplementary sections on alternative semantic approaches
- **Current Contents** (144 lines):
  1. sec:Indeterminacy (lines 14-78): Propositional Tense Logic with branching time histories
  2. sec:Cartesian (lines 82-142): Propositional Bimodal Logic using Cartesian product semantics
- **File Format**: Includes TEX root directive, header comments, consistent with LogicNotes.tex style
- **Integration**: Ready to receive sec:FirstOrder content

## Recommendations

### Recommendation 1: Structured Content Extraction Strategy

**Action**: Create a content extraction mapping that identifies which subsections from sec:TenseModality align with sec:Bimodal's structure.

**Mapping**:
- sec:Bimodal "Well-Formed Sentences" ← sec:TenseModality "Language" + "Well-Formed Sentences" (consolidate)
- sec:Bimodal "Abbreviation" ← sec:TenseModality "Abbreviations" (keep concise)
- sec:Bimodal "Frame" ← sec:TenseModality "Task Frame" + constraints
- sec:Bimodal "Interpretation" ← sec:TenseModality "Task Model" (world state interpretation)
- sec:Bimodal "Model" ← sec:TenseModality "Task Model"
- sec:Bimodal "Possible World" ← sec:TenseModality "World History" (rename for consistency)
- sec:Bimodal "Semantics" ← sec:TenseModality "Truth Conditions"
- sec:Bimodal "Logical Consequence" ← sec:TenseModality "Logical Consequence"

**Rationale**: This preserves sec:Bimodal's definition-oriented structure while importing sec:TenseModality's more sophisticated task semantics framework.

### Recommendation 2: Proof and Derivation Exclusion Protocol

**Action**: Systematically exclude all proof-theoretic content from the replacement:
1. Remove natural language motivation paragraph (sec:TenseModality lines 1399-1407)
2. Completely omit "TM Logic: Axiomatic System" section (lines 1452-1530)
3. Remove Hilbert-style proof environment blocks (P1, P2 proofs)
4. Exclude "Problem Set: TM Derivations" (lines 1584-1630)
5. Remove all `\TMproves` and axiomatic references

**Rationale**: sec:Bimodal's pedagogical approach focuses on semantic understanding through countermodels and frame analysis, not proof construction. This matches the request for "uniform presentation of definitions" without "proofs or sketches".

### Recommendation 3: Problem Set Adaptation Strategy

**Action**: Replace sec:Bimodal's current problem sets with adapted versions from sec:TenseModality:
1. Keep "Problem Set: Task Semantics" from current sec:Bimodal (focuses on countermodels)
2. Adapt selected exercises from "Problem Set: TM Syntax" (lines 1531-1582):
   - Well-formedness checking
   - Abbreviation expansion
   - Scope disambiguation
3. Create new countermodel exercises targeting:
   - Perpetuity principles (P1-P6) as semantic evaluation problems, NOT derivation problems
   - Modal-temporal interaction properties
4. Format consistently with `\begin{enumerate}[leftmargin=1.2in]` and multicols for space efficiency

**Rationale**: This maintains sec:Bimodal's emphasis on semantic reasoning while introducing exercises appropriate to the TM framework.

### Recommendation 4: Systematic File Relocation with Verification

**Action**: Move sec:FirstOrder to additional/additional.tex with the following procedure:
1. Extract lines 1191-1389 from LogicNotes.tex (complete sec:FirstOrder including all subsections and problem sets)
2. Append to additional/additional.tex after existing sec:Cartesian section (after line 142)
3. Verify label preservation: `\label{sec:FirstOrder}` remains accessible
4. Update table of contents if present
5. Maintain consistent formatting with additional.tex style (TEX root directive compatible)
6. Test compilation to ensure no broken cross-references

**Rationale**: sec:FirstOrder is self-contained with no cross-references to other sections, making relocation low-risk. Placement in additional.tex aligns with its role as foundational supplementary material.

### Recommendation 5: Notation Consistency Enforcement

**Action**: Ensure all custom commands used in the replacement are properly defined:
1. Verify all TM-specific commands (`\TMSystem`, `\taskrel`, `\worldhist`) are defined in notation.sty (lines 180-202)
2. Add any missing definitions to notation.sty before replacement
3. Use consistent metavariable conventions (`\metaA`, `\metaB` from lines 267-269)
4. Maintain uniform semantic clause formatting with itemize `[leftmargin=.15in]\small`
5. Preserve enumerate leftmargin settings `[leftmargin=1.2in]` throughout

**Rationale**: Notation consistency is critical for student comprehension and maintains the document's professional appearance. The notation.sty file already includes most necessary definitions for task semantics (added 2025-12-02).

### Recommendation 6: Incremental Implementation with Compilation Checkpoints

**Action**: Implement changes in distinct phases with compilation verification:
1. **Phase 1**: Move sec:FirstOrder to additional.tex, compile to verify
2. **Phase 2**: Create backup of current sec:Bimodal content
3. **Phase 3**: Replace sec:Bimodal syntax definitions with TenseModality syntax (preserving label sec:Bimodal)
4. **Phase 4**: Replace semantic definitions with task semantics framework
5. **Phase 5**: Adapt problem sets and compile final version
6. **Phase 6**: Verify all cross-references, labels, and page breaks

**Rationale**: Incremental implementation reduces risk of compilation errors and makes debugging easier. Each phase produces a compilable document, allowing rollback if issues arise.

## References

### Primary Source Files
- `/home/benjamin/Documents/Philosophy/Teaching/LogicNotes/LogicNotes.tex`
  - sec:FirstOrder: lines 1191-1389 (198 lines)
  - sec:Bimodal: lines 1041-1183 (142 lines)
  - sec:TenseModality: lines 1396-1674+ (280+ lines)

### Configuration and Style Files
- `/home/benjamin/Documents/Philosophy/Teaching/LogicNotes/assets/notation.sty`: lines 1-395
  - TM system commands: lines 180-192
  - Task semantics commands: lines 193-202
  - Bimodal operators: lines 230-248
  - Temporal operators: lines 204-224

- `/home/benjamin/Documents/Philosophy/Teaching/LogicNotes/assets/proof_styles.sty`: lines 1-481
  - Hilbert-style proof environment: lines 299-324
  - Axiom reference command: line 7

### Target Files
- `/home/benjamin/Documents/Philosophy/Teaching/LogicNotes/additional/additional.tex`: lines 1-144
  - Current sections: sec:Indeterminacy (lines 14-78), sec:Cartesian (lines 82-142)
  - Insertion point for sec:FirstOrder: after line 142

### Related Documentation
- Previous implementation: `.claude/specs/001_move_sections_improve_bimodal/`
  - Shows prior work on sec:Bimodal restructuring
  - Evidence of task semantics implementation completed 2025-12-02

## Implementation Status

- **Status**: Planning Complete
- **Plan**: [001-restructure-sections-bimodal-tense-plan.md](../plans/001-restructure-sections-bimodal-tense-plan.md)
- **Implementation**: [Will be updated by orchestrator]
- **Date**: 2025-12-02
