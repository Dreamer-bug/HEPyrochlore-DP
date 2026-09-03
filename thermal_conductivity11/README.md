# Thermal conductivity (NEMD)

Representative LAMMPS inputs and structures for non-equilibrium molecular-
dynamics thermal-conductivity calculations with the frozen DP model.

## Contents

- `TC_NEMD.in.lammps`: hot/cold-region NEMD workflow.
- `graph_LNSEGY_revised.pb`: frozen DP model.
- `lmp.*.conf`: LZO, single-component, LEG, and LNSEGY structures.
- `La/data_TC/profile_*K.txt`: archived LZO temperature profiles from 300 to
  1500 K.
- `La/plot_whole.ipynb`: profile processing and thermal-conductivity analysis.
- `La/LZO.png`: archived LZO result image.

The supplied input currently reads `lmp.La_con24.conf` and defaults to 300 K:

```bash
lmp_mpi -in TC_NEMD.in.lammps
```

All structure files in this directory now declare the model element order
`La, Nd, Sm, Eu, Gd, Yb, Zr, O`. When changing `read_data`, also verify the hot
and cold region coordinates against the selected cell length.

The LZO profiles constitute the processed example dataset. Complete trajectories,
dumps, and per-temperature profiles for every composition in manuscript Figure 6
are not included; they are optional unless full panel-level reproduction is
required.
