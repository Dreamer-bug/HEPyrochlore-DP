# Deep Potential model training

This directory contains the complete archived DeepMD-format datasets and the
principal artifacts used to train and evaluate the model.

## Contents

- `input.json`: archived DeepMD-kit model/training configuration.
- `graph_LNSEGY_revised.pb`: frozen model used by the downstream examples.
- `lcurve.out`: training loss history.
- `DP_LNSEGY_ADP1_training_analysis.ipynb`: model-analysis notebook.
- `train_data/`: 36 systems and 201,600 configurations.
- `valid_data/`: 36 systems and 25,200 configurations.
- `test_data/`: 36 systems and 25,200 configurations.
- `test_results/`: archived energy/force/virial prediction outputs.

The datasets use the element labels `La`, `Yb`, `Sm`, `Eu`, `Gd`, `Zr`, `O`,
and `Nd`. DeepMD-kit uses the names in each system's `type_map.raw` to reconcile
local data type indices with the model type map.

## Archived path convention

`input.json` points to the original location
`../LNSEGY_all/{train_data,valid_data}/...`. The same 36 named systems are present
locally under `train_data/` and `valid_data/`. Update the prefix before
retraining, or reproduce the original parent-directory layout. The archived
input remains unchanged so it accurately records the original run configuration.

## Typical commands

```bash
dp train input.json
dp freeze -o graph.pb
```

Exact historical package versions are unavailable. The input and model are
provided as archival artifacts; current DeepMD-kit releases may require minor
compatibility changes.
