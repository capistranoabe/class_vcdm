
# CLASS-Gen4 VCDM
CLASS-Gen4 VCDM -- Modified CLASS Implementation  Compatible with CLASS 3.3.4 Prepared for CosmoVerse Cosmology Compilation Group (CCG) . This contains a modified version of the Boltzmann solver CLASS (Cosmic Linear Anisotropy Solving System), implementing the Gen4 VCDM cosmological model.

## Overview

This repository contains a modified implementation of the Boltzmann solver CLASS (Cosmic Linear Anisotropy Solving System), extended to support the **Gen4 VCDM model**. The modifications introduce new background dynamics and perturbation behavior while maintaining full compatibility with the standard CLASS structure. Moreover, the implementation is built such that it reduces to **flat ΛCDM** in the appropriate parameter limit.

---

## Code Attribution

This project is based on:

* CLASS — Cosmic Linear Anisotropy Solving System
* Authors: Julien Lesgourgues, Thomas Tram, Nils Schoeneberg, and collaborators

Original repository:
https://github.com/lesgourg/class_public

If you use this code, you **must cite the original CLASS papers**, in particular:

* *CLASS II: Approximation schemes* (Lesgourgues & Tram, 2011)

---

## Implemented Model: Gen4 VCDM

The Gen4 VCDM model introduces modifications at both the **background** and **linear perturbation** levels.

### Primary Parameters

* `log10b_VCDM` — Characteristic scale
* `b2_bar_VCDM` — Background amplitude parameter
* `a1_VCDM` — Transition scale factor
* `alpha_VCDM` — Evolution steepness

### Derived Quantities

* `b2_VCDM`
* `Lambda_s0`

---

## Code Modifications

All modifications are implemented directly within the CLASS codebase.

### Modified Modules

* **Input Handling**

  * `source/input.c`
  * Parsing and validation of VCDM parameters
  * Computation of derived quantities

* **Background Evolution**

  * `include/background.h`
  * `source/background.c`
  * Inclusion of VCDM energy density in the Friedmann equations

* **Perturbations**

  * `source/perturbations.c`
  * Extension of scalar perturbation equations (Newtonian gauge)
  * Stable behavior across superhorizon and subhorizon regimes

* **Python Interface**

  * `python/cclassy.pxd`
  * `python/classy.pyx`
  * Full support for VCDM parameters in the Python wrapper

---

## Installation

The installation procedure follows standard CLASS compilation.

```bash
git clone <your-repo-url>
cd <repo>
make -j
```

If needed, adjust compiler and flags in the `Makefile`.

For detailed instructions, see the official CLASS documentation:
https://github.com/lesgourg/class_public/wiki/Installation

---

## Usage

Run the code with a VCDM input file:

```bash
./class vcdm.ini
```

You may also combine with precision files:

```bash
./class vcdm.ini cl_permille.pre
```

---

## Model Validation

* The implementation is constructed to recover **ΛCDM** in the appropriate parameter limits
* A reference input file (`vcdm.ini`) is provided for testing

---

## Citation

If you use this repository in scientific work, please cite:

1. The original CLASS papers
2. Your corresponding Gen4 VCDM publication (when available)

---

## License

This project is licensed under the GNU General Public License v3.0

---

## Acknowledgments

We acknowledge the original CLASS developers and contributors for providing a robust and extensible cosmological Boltzmann solver.

---

## Contact / Contributions

* For upstream issues: use the CLASS GitHub repository
* For VCDM-specific issues: open an issue in this repository

Contributions are welcome, provided they remain compatible with GPL-3.0.
