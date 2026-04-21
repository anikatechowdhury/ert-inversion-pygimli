# ert-inversion-pygimli

![Python](https://img.shields.io/badge/Python-3.8+-blue)
![pyGIMLi](https://img.shields.io/badge/pyGIMLi-1.5+-orange)
![License](https://img.shields.io/badge/License-MIT-green)
![Status](https://img.shields.io/badge/Status-Complete-brightgreen)

A Python-based geophysical inversion workflow for subsurface resistivity characterisation using pyGIMLi. Implements two standard electrical resistivity methods — 1D Vertical Electrical Sounding (VES) and 2D Electrical Resistivity Tomography (ERT) — applied to a shallow aquifer investigation scenario.

---

## Overview

Electrical resistivity methods are among the most widely used geophysical techniques for non-invasive subsurface characterisation. This project demonstrates a complete Python inversion pipeline using pyGIMLi — from synthetic data generation through forward modelling, inversion, and geological interpretation.

The geological scenario simulates a shallow alluvial aquifer system with a clay aquitard overlying a saturated sand layer and weathered basement, representative of hydrogeological settings in the Indo-Gangetic Plain and Bengal Basin.

---

## Modules

### Module 1 — 1D VES Inversion (Schlumberger Array)
- Synthetic apparent resistivity data generation with 5% noise
- pyGIMLi `VESManager` 4-layer inversion
- Apparent resistivity curve with observed vs calculated fit
- Inverted resistivity–depth model with layer annotation
- χ² misfit reporting

### Module 2 — 2D ERT Inversion (Wenner Array)
- 24-electrode Wenner array geometry (5 m spacing, 115 m profile)
- Forward model with clay / saturated sand / basement / resistive anomaly
- pyGIMLi `ERTManager` 2D inversion
- Apparent resistivity pseudosection
- Inverted 2D resistivity section with geological annotation
- Model coverage / sensitivity distribution

---

## Geological Scenario

| Unit | Resistivity (Ω·m) | Interpretation |
|---|---|---|
| Topsoil / Dry alluvium | 80 | Shallow unsaturated zone |
| Clay / Silt aquitard | 15 | Low-permeability confining layer |
| Saturated sand aquifer | 80–120 | Target aquifer zone |
| Resistive anomaly | 350 | Buried structure / dry zone |
| Weathered basement | 200 | Regional basement |

---

## Inversion Parameters

| Parameter | VES | ERT |
|---|---|---|
| Array | Schlumberger | Wenner |
| Regularisation (λ) | 20 | 30 |
| Noise level | 5% | 3% |
| Inversion type | 1D layered | 2D smooth |

---

## Project Structure

```
ert-inversion-pygimli/
│
├── ert_ves_inversion.py     # Main inversion script (VES + ERT)
└── README.md
```

---

## Dependencies

| Library | Purpose |
|---|---|
| `pygimli` | Geophysical inversion framework (VES + ERT) |
| `numpy` | Numerical operations |
| `pandas` | Data export to CSV |
| `matplotlib` | Plotting and visualisation |

```bash
pip install pygimli numpy pandas matplotlib
```

---

## Usage

```bash
python ert_ves_inversion.py
```

All outputs are saved to `outputs/`.

---

## Outputs

| File | Description |
|---|---|
| `ves_inversion.png` | Apparent resistivity curve + inverted 1D depth model |
| `ert_2d_section.png` | Pseudosection + inverted 2D resistivity section |
| `ert_coverage.png` | Model coverage / sensitivity distribution |
| `ert_true_model.png` | True forward model (for comparison) |
| `ves_data.csv` | VES apparent resistivity data |
| `ert_data.csv` | ERT electrode configuration and apparent resistivity data |

---

## Key Results

**VES** — 4-layer inversion converges with χ² = 0.004, clearly resolving the clay aquitard (low resistivity) overlying the sand aquifer (high resistivity).

**ERT** — 2D inversion recovers the general resistivity architecture including the resistive anomaly at ~60 m horizontal distance and ~12 m depth. Coverage plot confirms good sensitivity in the upper 20 m.

---

## Author
Anikate Chowdhury  
ORCID: https://orcid.org/0009-0004-5580-2470

---

## Citation
If you use this methodology or implementation logic in academic or technical work,
please cite this repository. 

DOI: https://doi.org/10.5281/zenodo.19686771
