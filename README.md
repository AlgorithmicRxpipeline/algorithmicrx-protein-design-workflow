# AlgorithmicRx Protein Design Workflow

A modular computational workflow for **sequence-to-structure analysis, protein design, stability/quality assessment, structural filtering, docking/functional evaluation, and candidate ranking**.

> **Status:** Public workflow scaffold / research documentation. This repository is intended to document the computational architecture and reproducible workflow used to support AlgorithmicRx protein-design and structure-guided discovery work. Proprietary models, unpublished targets, confidential datasets, and production IP are intentionally excluded.

## Workflow at a glance

```text
Sequence / Target Input
        │
        ▼
MSA & Sequence Analysis
        │
        ▼
Protein Structure Prediction
(AF3 / OpenFold / Boltz-2)
        │
        ▼
Sequence / Design Generation
        │
        ▼
Stability & Quality Assessment
        │
        ▼
Structural Filtering
        │
        ▼
Docking / Functional Evaluation
        │
        ▼
Candidate Ranking
```

## Pipeline stages

### 1. Sequence / target input

Inputs may include:

- Protein sequences in FASTA format
- Target or complex definition
- Domain boundaries / functional regions
- Optional sequence annotations
- Optional literature-derived constraints

**Output:** normalized input sequences and target metadata.

### 2. MSA & sequence analysis

The workflow can integrate multiple-sequence alignment (MSA) and sequence-level annotations to support evolutionary and structural analysis.

Typical components include:

- Sequence cleaning and normalization
- MSA generation
- Conservation analysis
- Domain / motif annotation
- Evolutionary feature extraction

**Output:** aligned sequences and sequence-derived features.

### 3. Protein structure prediction

Predicted structures can be generated or evaluated using modern structure-prediction systems, including:

- **AlphaFold 3 (AF3)**
- **OpenFold**
- **Boltz-2**

The choice of model depends on the target, input modality, and research question.

**Output:** predicted structures, confidence metrics, and structural metadata.

### 4. Sequence / design generation

Candidate sequences can be generated or prioritized using protein-design methods appropriate to the target and research objective.

Possible approaches include:

- Sequence optimization under structural constraints
- Mutation and variant generation
- Stability-aware sequence design
- Protein language-model or structure-conditioned design methods
- Rosetta-family workflows
- **ThermoMPNN**-informed stability assessment / design exploration

**Output:** a candidate sequence set with provenance and design metadata.

### 5. Stability & quality assessment

Candidate sequences are evaluated using computational quality and stability criteria before more expensive downstream analysis.

Potential metrics include:

- Predicted folding confidence
- Structural consistency
- Stability-related scores
- Sequence plausibility
- Conservation / constraint compatibility
- Aggregation or developability-related flags, where applicable

**Output:** assessed candidates with standardized metrics.

### 6. Structural filtering

Candidates that fail predefined structural or quality criteria are removed before docking or functional evaluation.

Filtering can consider:

- Fold consistency
- Confidence thresholds
- Structural clashes
- Domain integrity
- Geometry / interface quality
- Constraint satisfaction

**Output:** filtered candidate set.

### 7. Docking / functional evaluation

Selected candidates can be evaluated using structure-based computational methods, such as:

- Protein-protein docking
- Protein-ligand docking
- Interface analysis
- Binding-pose comparison
- Functional-site compatibility assessment

This stage is designed to provide **prioritization evidence**, not experimental confirmation.

**Output:** docking poses, interaction metrics, and functional-evaluation features.

### 8. Candidate ranking

Candidates are ranked using a transparent, multi-factor scoring framework.

Example ranking dimensions:

| Dimension | Example purpose |
|---|---|
| Structural confidence | Assess predicted structural reliability |
| Stability | Prioritize structurally plausible candidates |
| Constraint satisfaction | Preserve required biological features |
| Interaction / docking evidence | Evaluate structural compatibility |
| Sequence plausibility | Reduce implausible designs |
| Developability flags | Support downstream prioritization |

The final ranking is intended to support **research prioritization and experimental hypothesis generation**.

## Suggested project structure

```text
algorithmicrx-protein-design-workflow/
├── README.md
├── docs/
│   ├── workflow.md
│   └── methodology.md
├── configs/
│   └── example_config.yaml
├── data/
│   ├── input/
│   ├── msa/
│   ├── structures/
│   ├── designs/
│   ├── assessment/
│   ├── filtered/
│   ├── docking/
│   └── ranking/
├── src/
│   └── README.md
└── results/
    └── README.md
```

## Reproducibility principles

1. Keep every candidate linked to its original input sequence.
2. Record model/tool name and version for each prediction.
3. Record configuration and key parameters used for each stage.
4. Preserve intermediate outputs where licensing permits.
5. Separate public demonstration data from proprietary AlgorithmicRx data.
6. Keep ranking criteria explicit and auditable.
7. Distinguish **computational prediction** from **experimental validation**.

## Example candidate record

```yaml
candidate_id: ARX_DEMO_001
input_sequence: data/input/example.fasta
msa: data/msa/example.a3m
structure_model: AF3
structure_file: data/structures/ARX_DEMO_001.cif
design_method: structure_constrained_sequence_design
stability_assessment: ThermoMPNN
structural_filter: passed
docking_method: TBD
functional_evaluation: TBD
ranking_status: pending
```

## Scope

This repository documents a modular research workflow for computational protein design and structure-guided discovery. It is **not** a claim that every module is currently deployed as a production system, nor does it disclose proprietary AlgorithmicRx target data or unpublished therapeutic candidates.

## Future extensions

- Automated workflow orchestration
- Model/version tracking
- Candidate provenance database
- Multi-objective ranking
- Single-cell validation interface
- Integration with multi-omics target prioritization
- Experimental validation feedback loop

## Organization

**AlgorithmicRx Inc.**  
AI + Deep Biology for rare-disease drug discovery

https://www.algorithmicrx.com


