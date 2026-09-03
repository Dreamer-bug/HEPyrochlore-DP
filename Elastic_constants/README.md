# Elastic constants

Representative LAMMPS finite-deformation files for calculating the elastic
constant tensor of La2Zr2O7 with the archived DP model.

## Contents

- `in.elastic`: main workflow and elastic-property expressions.
- `init.in`: structure, temperature, deformation, and run parameters.
- `displace.in`: positive and negative finite deformations.
- `potential_npt.dp`: NPT equilibration potential/integration settings.
- `potential.dp`: NVE/thermostat potential/integration settings.
- `lmp.La_con333.conf`: 2,376-atom La2Zr2O7 structure.
- `graph_LNSEGY_revised.pb`: frozen DP model.

Run from this directory with a LAMMPS build supporting `pair_style deepmd`:

```bash
lmp_mpi -in in.elastic
```
