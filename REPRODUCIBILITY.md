# Reproducibility scope and known limitations

## What this repository supports

This release contains the full archived DeepMD-format training, validation, and
test datasets, the training configuration and loss history, test predictions,
the frozen model, and representative downstream property-calculation inputs.
This is sufficient for model inspection, independent model evaluation, and
understanding the principal computational workflows described in the manuscript.

## What is not required for the stated release

The repository does not need to contain every large trajectory, restart file,
LAMMPS dump, scheduler log, or redundant intermediate generated during the
original calculations. Such files are costly to store and are normally omitted
when the processed data, model, representative inputs, and methodology are
available.

Likewise, complete raw source data for every manuscript panel are not included.
Large trajectories, restart files, and dumps are not necessary for the stated
release. If stronger panel-level reproducibility is requested, the preferred
addition is a small set of processed CSV tables plus the plotting scripts for
the thermal-expansion, elastic-property, phonon, and thermal-conductivity
figures - not the full raw simulation archive.

## Minimum release versus expanded release

The current scientific content is suitable for a **model-and-workflow release**:
it makes the complete model-development datasets, configuration, frozen model,
test predictions, and representative downstream inputs available.

For a stronger **figure-reproduction release**, add only compact processed data:

- temperature, lattice constant, and CTE values used in manuscript Figure 4;
- elastic-property values used in manuscript Table 1;
- plotted phonon frequencies for the Figure 5 panels not already represented by
  the LZO archive; and
- temperature and final thermal-conductivity values used in manuscript Figure 6.

These additions would be much smaller than the existing training dataset. They
are recommended for transparent peer review but do not require uploading all
raw trajectories or intermediate simulation files.

## Historical software environment

The exact DeepMD-kit, LAMMPS, phonopy, Python, and library versions used for the
original study are no longer recoverable. The repository therefore records only
the software families and archived input syntax. Users should expect possible
compatibility adjustments when using current releases. No unverified version
numbers are reported.

## Archived versus ready-to-run inputs

- `DP_model_training/input.json` preserves the original dataset paths and must be
  adapted to the local repository layout for retraining.
- The elastic-constant files preserve the supplied workflow. The transition from
  NPT equilibration to NVE sampling should be reviewed in the target LAMMPS
  version because the include files define separate integration fixes.
- `Thermal_expansion/in.CTE.lmp` and `thermal_conductivity11/TC_NEMD.in.lammps`
  are representative single-structure inputs. Select the desired structure and
  verify its element-type numbering before use.
- All supplied LAMMPS structure files use the frozen model's atom-type order:
  `La, Nd, Sm, Eu, Gd, Yb, Zr, O`.
- The phonon directory is a complete archived LZO example, not the complete raw
  archive for every phonon panel in the manuscript.

## Recommended citation and availability wording

A suitable manuscript data-availability statement is:

> The training, validation, and test datasets, trained deep-learning potential,
> and representative simulation input files supporting this study are available
> at https://github.com/Dreamer-bug/HEPyrochlore-DP. Large files are distributed using Git
> LFS. Additional data are available from the corresponding authors upon
> reasonable request.
