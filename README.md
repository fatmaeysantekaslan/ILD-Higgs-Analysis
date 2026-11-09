# ILD Reconstruction Performance: ILC vs FCC-ee v02

This repository contains comparing of the reconstruction performance of the **International Large Detector (ILD)** in the **ILC** and **FCC-ee v02** detector configurations.

The study uses simulated \(e^+e^- \to ZH\) events with \(Z \to \mu^+\mu^-\) and investigates the invisible Higgs final state \(H \to ZZ^* \to 4\nu\). The same set of **25,250 generated events** is reconstructed with both detector configurations to compare the two-muon selection, additional particle-flow activity, and the reconstructed Z and Higgs recoil-mass distributions.

## Analysis notebook

- [`ilc_v02.ipynb`](ilc_v02.ipynb) — event reconstruction comparison, angular acceptance, selection scans, cumulative cutflows, truth-matched signal efficiency and purity, and final mass distributions.

## Input data

All input files are stored in [`data/`](data/):

| File | Description |
| --- | --- |
| `ild_ilc_zh_25250_reco.root` | Reconstructed events using ILD@ILC. |
| `ild_fccee_v02_zh_25250_reco.root` | Reconstructed events using ILD@FCC-ee v02. |
| `zh_25250_truth_angles.csv` | Generator-level muon polar angles for all 25,250 events. |
| `zh_25250_truth_4nu.csv` | Truth information identifying the 1,002 \(H \to ZZ^* \to 4\nu\) events. |

## Selection

The analysis applies these cuts sequentially:

1. Exactly two reconstructed muons.
2. Generator-level minimum folded muon polar angle \(\theta_{\min} > 25^\circ\).
3. No additional charged particle-flow objects (PFOs).
4. At most two additional neutral PFOs.
5. Total additional PFO energy below 20 GeV.

## Final selection results

| Quantity | ILD@ILC | ILD@FCC-ee v02 |
| --- | ---: | ---: |
| Selected events | 663 | 656 |
| Selected truth \(4\nu\) events | 663 | 655 |
| Truth \(4\nu\) efficiency (out of 1,002) | 66.17% | 65.37% |
| Truth \(4\nu\) purity in the selected sample | 100.00% | 99.85% |

## Running the notebook

Use a Python environment with **PyROOT, uproot, awkward, NumPy, pandas, Matplotlib, and Jupyter**. Git LFS is needed to retrieve the ROOT files.

```bash
git lfs install
git lfs pull
jupyter notebook ilc_v02.ipynb
```

Run Jupyter from the **repository root**, since the notebook reads input files using relative `data/` paths.
