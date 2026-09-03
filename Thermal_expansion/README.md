# Thermal expansion

Representative LAMMPS thermal-expansion workflow and starting structures for the
investigated pyrochlore compositions.

## Contents

- `in.CTE.lmp`: NPT temperature scan and volume averaging.
- `graph_LNSEGY_revised.pb`: frozen DP model.
- `lmp.{La,Nd,Sm,Eu,Gd,Yb}_con333.conf`: single-component structures.
- `lmp.LEG_con333.conf`: medium-entropy structure.
- `lmp.LNSEGY*-1_con333.conf`: high-entropy structures.

The archived input currently reads `lmp.La_con333.conf` and scans 100-1600 K in
20 K increments at nominal zero pressure:

```bash
lmp_mpi -in in.CTE.lmp
```

All supplied structures use the frozen model's atom-type order:
`La, Nd, Sm, Eu, Gd, Yb, Zr, O`. The current `pair_coeff * *` command therefore
uses consistent type numbering when another supplied structure is selected.

The directory contains representative inputs and structures, not the complete
temperature-volume outputs used for all panels of manuscript Figure 4. Those
processed results may be added later but are not required for the stated archival
scope unless requested by the journal or reviewers.
