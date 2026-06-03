# NABNP Point Cloud Denoising

This repository contains a compact reproducibility package for
**Noise-Adaptive Bilateral Normal Projection (NABNP)**, a learning-free point
cloud denoising method.

## Contents

- `src/nabnp/algorithm.py`: clean implementation of the NABNP equations.
- `src/nabnp/synthetic.py`: deterministic generation of stress scenarios.
- `src/nabnp/metrics.py`: MSE, Chamfer Distance, and HD95 metrics.
- `src/nabnp/baselines.py`: LMF, LMedF, NBF, and WLOP baselines for reproduction.
- `scripts/run_nabnp.py`: run NABNP on one PLY file.
- `scripts/run_benchmark.py`: run the benchmark protocol.
- `data/pcpnet_clean/`: clean PCPNet benchmark point clouds used by the scripts.

## Installation

```bash
python -m venv .venv
```

On Windows PowerShell:

```powershell
.\.venv\Scripts\python -m pip install -e .
```

On Linux/macOS:

```bash
./.venv/bin/python -m pip install -e .
```

## Run NABNP on One Model

The command below generates a `Noise_0.01` test case from the clean Fandisk
model, saves the noisy input, denoises it with NABNP, and prints metrics against
the clean ground truth.

```bash
python scripts/run_nabnp.py --input data/pcpnet_clean/fandisk/fandisk_clean.ply --scenario Noise --parameter 0.01 --seed 1 --save-noisy outputs/fandisk_noise001_seed01.ply --output outputs/fandisk_noise001_seed01_nabnp.ply
```

## Run the Benchmark

Run the proposed method and noisy-input baseline:

```bash
python scripts/run_benchmark.py --methods nabnp,noisy
```

Run the full learning-free comparison:

```bash
python scripts/run_benchmark.py --methods all
```

This evaluates 5 models, 13 scenarios, and 10 seeds. The full run can take a
long time because it executes 650 trials per method.

## Default NABNP Parameters

The default parameters in `DEFAULT_PARAMETERS` are:

| Parameter | Value |
| --- | ---: |
| `k` | 35 |
| `iterations` (`T`) | 2 |
| `lambda_s` | 1.0 |
| `sigma_n` | 0.5 |
| `r0` | 0.0334758913 |
| `r1` | 0.1628921788 |
| `q` | 0.7355901032 |
| `gamma` | 0.95 |
| `gamma_n` | 0.35 |
| `tau_s` | 1.0 |
| `beta` | 0.9 |

Generated benchmark outputs are written under `outputs/` by default. The
repository does not include precomputed metric tables.
