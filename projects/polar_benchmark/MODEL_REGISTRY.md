# Model registry

`MODEL_REGISTRY.csv` lists every committed `*.model` file with its size and
sha256. It is regenerated (hashes only) by

```bash
uv run python projects/polar_benchmark/script/build_manifest.py
```

The columns `role, source_url, version, license, training_config, training_log, notes`
are filled in **by hand** and are preserved when the script is re-run. Every
`TODO` must be resolved before any result from that model goes into a paper.

| Path | What we believe it is | Status |
| --- | --- | --- |
| `model/mace-mh-1.model` | MACE-MH-1 multi-head foundation model (heads: `matpes_r2scan`, `mp_pbe_refit_add`, `spice_wB97M`, `oc20_usemppbe`, `omol`, `omat_pbe`); neutral baseline | Source URL / version / license: **to confirm** |
| `data/2_global_embedding/Charge_embedded_MACE/MACE_vse1_five_wb_swa_e1000.model` | Walsh group's charge-embedded MACE (categorical `total_charge`, 5 classes), V_Se1 HSE06 | **Verified**: byte-identical to Zenodo 22756145 (CC-BY-4.0). External baseline, not trained here |
| `data/3_MF/MF/MF_MACE/VSe1_neu/Training/MACE_vse1_neu.model` | Walsh group's multi-fidelity (PBE/HSE) MACE, neutral V_Se1 | **Verified**: Zenodo 22756145. External baseline |
| `data/3_MF/MF/MF_MACE/VSe1_pl1/MACE_vse1_pl1.model` | Same as above for V_Se1 q=+1 | **Verified**: Zenodo 22756145. External baseline |
| MACE-Polar checkpoint(s) | Not committed yet | **Missing**: add the checkpoint key/URL (e.g. `polar-1-s`) and sha256 |
| Fine-tuned MACE-Polar models (5 runs, Yile) | Not committed yet; no fine-tuning by this project exists in the repo history | **Missing**: add base checkpoint, which Walsh subset was used, configs, logs, seeds and sha256 |

> The three `data/**/*.model` files and their `run*.sh` scripts were trained and released by the Walsh group (Wang, Mosquera-Lois & Walsh, arXiv:2603.05238). They are **external baselines** to compare our fine-tuned models against, not results of this project. The paths in `run*.sh` (`/home/mmm0798`, `-A Imperial_Mat`) refer to the authors' cluster.
