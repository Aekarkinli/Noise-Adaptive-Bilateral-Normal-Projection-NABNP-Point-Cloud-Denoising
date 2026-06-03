# Release Manifest

This directory is a cleaned GitHub-ready reproducibility package.

Included:

- NABNP implementation.
- Deterministic benchmark scenario generator.
- Learning-free comparison baselines.
- Five clean PCPNet benchmark PLY files used by the experiments.

Excluded:

- Tuning scripts, ablation-only scripts, draft plotting scripts, Python cache
  files, and draft-writing assets.
- Large generated scenario caches and intermediate PLY outputs. They are
  reproducible from the included clean point clouds and scripts.
- Precomputed metric/result tables.

Recommended GitHub upload root:

```text
github/
```
