# Protein Design Workflow

## End-to-end flow

```text
[1] Sequence / Target Input
      ↓
[2] MSA & Sequence Analysis
      ↓
[3] Structure Prediction
      ├── AlphaFold 3
      ├── OpenFold
      └── Boltz-2
      ↓
[4] Sequence / Design Generation
      ↓
[5] Stability & Quality Assessment
      ├── Structural confidence
      ├── Stability-related metrics
      └── Sequence / constraint checks
      ↓
[6] Structural Filtering
      ↓
[7] Docking / Functional Evaluation
      ↓
[8] Candidate Ranking
```

## Design philosophy

The workflow is designed as a **funnel**: inexpensive sequence-level analysis is performed first, followed by increasingly expensive structural and functional evaluation. This reduces unnecessary computation and creates a traceable path from raw input to prioritized candidate.

## Data provenance

Each candidate should maintain a stable identifier across all stages:

```text
candidate_id
  ├── input sequence
  ├── MSA
  ├── predicted structure(s)
  ├── design method
  ├── assessment metrics
  ├── filtering decision
  ├── docking / functional metrics
  └── final rank
```
