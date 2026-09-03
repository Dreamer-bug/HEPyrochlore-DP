# Phonon dispersion

Complete archived LZO finite-displacement example using phonopy, LAMMPS, and the
frozen DP model.

## Contents

- `LZO_prim.conf`: 22-atom primitive LZO structure.
- `band.conf`: phonopy supercell, band path, mesh, and PDOS settings.
- `supercells/`: 132 displaced supercells.
- `forces/`: 132 corresponding LAMMPS force outputs.
- `FORCE_SETS`: assembled finite-displacement force dataset.
- `phonopy.yaml` and `phonopy_disp.yaml`: phonopy metadata/results.
- `graph_LNSEGY_revised.pb`: frozen DP model.
- `in.force`: single-point LAMMPS force input.
- `Phonon-dispersion.ipynb`: plotting notebook.
- `phonon_band_merged.png`: archived LZO dispersion figure.

Example for one displaced supercell:

```bash
lmp_mpi -var DATA supercells/supercell-001 \
        -var OUT forces/phonopy_001.out \
        -in in.force
```

The supercells use eight declared model atom types, with LZO atoms occupying
types 1 (La), 7 (Zr), and 8 (O). The model file and `pair_coeff * *` command are
present.

This directory reproduces the archived LZO workflow. It does not contain the
full DPMD and DFT source archive for the LEG and LSEGY panels in manuscript
Figure 5. Those additional files are optional unless complete panel-level
reproduction is required.
