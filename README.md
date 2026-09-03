# Deep-learning potential for high-entropy pyrochlores

Research data, a trained Deep Potential (DP) model, and representative simulation
workflows accompanying the manuscript:

> Yuxuan Wang, Huicong Chen, Guoqiang Lan, and Jun Song, **"A Deep-learning
> Potential for Predicting Thermal and Physical Properties of High-entropy
> Pyrochlores,"** submitted to *Computational Materials Science*.

This repository provides the data used to train, validate, and test the DP model,
the frozen model, and representative LAMMPS/phonopy inputs. It is an archival
research release, not a turnkey package or a complete archive of every
intermediate file used to prepare every manuscript figure.

## Repository scope

The release is designed to support three practical uses:

1. inspect the DeepMD-format training, validation, and test datasets;
2. reuse or evaluate the archived frozen DP model; and
3. understand representative workflows used for the property calculations.

The repository does **not** claim bit-for-bit reproduction with current software
or complete regeneration of every panel in the manuscript. See
[`REPRODUCIBILITY.md`](REPRODUCIBILITY.md) for the precise scope and known
limitations.

## Contents

| Directory | Contents |
| --- | --- |
| [`DP_model_training/`](DP_model_training/) | DeepMD-kit configuration, training/validation/test data, loss history, test predictions, frozen model, and analysis notebook |
| [`Elastic_constants/`](Elastic_constants/) | Representative LAMMPS finite-deformation workflow for La2Zr2O7 |
| [`Phonon_dispersion/`](Phonon_dispersion/) | Representative LZO phonopy/LAMMPS workflow, 132 displaced supercells and force outputs, assembled `FORCE_SETS`, and plotting files |
| [`thermal_conductivity11/`](thermal_conductivity11/) | Representative NEMD input, structures for the investigated compositions, an LZO profile dataset, and analysis notebook |
| [`Thermal_expansion/`](Thermal_expansion/) | Representative LAMMPS thermal-expansion input and structures for the investigated compositions |

## Software

The archived workflows used the following software families:

- DeepMD-kit, including the DPA-1 descriptor;
- LAMMPS with DeePMD support;
- phonopy; and
- Python/Jupyter packages listed in [`requirements.txt`](requirements.txt).

The exact historical software versions are no longer recoverable. No versions
have been invented or inferred. Current releases may require minor syntax or API
adjustments. This limitation does not affect access to the archived numerical
data or frozen model, but it prevents a guarantee of bit-for-bit reruns.

## Downloading the data

The repository contains approximately 3.17 GiB of files. NumPy arrays, frozen
models, images, and DP test outputs are managed with Git LFS. Install Git LFS
before cloning or committing:

```bash
git lfs install
git clone https://github.com/Dreamer-bug/HEPyrochlore-DP.git
cd HEPyrochlore-DP
git lfs pull
```

After cloning, verify that the `.npy`, `.pb`, and large test-result files contain
binary data rather than unresolved LFS pointer text.

## Python environment

The unpinned dependency list intentionally describes required package families,
not the unavailable historical environment:

```bash
python -m venv .venv
# Linux/macOS: source .venv/bin/activate
# Windows: .venv\Scripts\activate
python -m pip install -r requirements.txt
jupyter lab
```

## Basic usage

### Inspect or retrain the DP model

Run from `DP_model_training/`. The archived `input.json` retains the original
calculation paths (`../LNSEGY_all/...`). Adjust those paths to the local
`train_data/` and `valid_data/` directories before attempting a new training
run. The archived input was intentionally kept unchanged.

Typical commands are:

```bash
dp train input.json
dp freeze -o graph.pb
```

The model used by the supplied examples is `graph_LNSEGY_revised.pb`.

### Run a representative LAMMPS calculation

Run an input from its own directory so relative paths resolve correctly:

```bash
cd Thermal_expansion
lmp_mpi -in in.CTE.lmp
```

Read the directory-specific README first. Input parameters and element-type
numbering must be checked before substituting a different structure.

### Inspect the phonon workflow

The LZO example includes all 132 displaced supercells and matching force outputs,
the assembled `FORCE_SETS`, phonopy YAML files, and a plotting notebook. See
[`Phonon_dispersion/README.md`](Phonon_dispersion/README.md).

## Integrity checks performed for this release

- The training, validation, and test splits each contain the same 36 systems.
- The splits contain 201,600, 25,200, and 25,200 configurations, respectively.
- All 540 NumPy arrays were readable, dimensionally consistent, and free of
  detected NaN/Inf values at the time of the repository audit.
- The 132 phonon supercells have 132 matching force-output files.
- All five copies of `graph_LNSEGY_revised.pb` have the same SHA-256 digest:
  `ab60b048357dbfd1e6db75a16590487c5e9f2242cc731e54fad9b742aee9212b`.
- All three notebooks are valid JSON documents.

These checks validate file integrity and consistency; they do not replace
scientific validation with the original software environment.

## Citation

While the article is under review, cite the submitted manuscript and this
repository. GitHub can read [`CITATION.cff`](CITATION.cff) and display a
ready-to-copy citation. Add the DOI, volume, article number, and publication year
after acceptance.

Repository: <https://github.com/Dreamer-bug/HEPyrochlore-DP>

## License

Copyright (c) 2026 Yuxuan Wang, Huicong Chen, Guoqiang Lan, and Jun Song.

This repository uses two licenses:

- Source code, notebooks, LAMMPS/phonopy input scripts, configuration files,
  and documentation are licensed under the [MIT License](LICENSE).
- Research datasets, the frozen DP model, archived numerical results, and
  figures are licensed under the [Creative Commons Attribution 4.0
  International License](DATA_LICENSE.md).

See [`DATA_LICENSE.md`](DATA_LICENSE.md) for the exact scope, attribution
requirements, and third-party-material exception.

## Contact

Corresponding authors:

- Yuxuan Wang: [yuxuan.wang3@mail.mcgill.ca](mailto:yuxuan.wang3@mail.mcgill.ca)
- Jun Song: [jun.song2@mcgill.ca](mailto:jun.song2@mcgill.ca)

Department of Mining and Materials Engineering, McGill University, Montreal,
Quebec H3A 0C5, Canada.
