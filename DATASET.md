# Dataset

This repository includes the five clean PCPNet benchmark point clouds used in
the benchmark scripts:

- Fandisk
- Bunny
- Dragon
- Armadillo
- Boxunion

Synthetic benchmark inputs are generated deterministically from these clean
point clouds by `nabnp.synthetic.generate_scenario`.

Protocol:

- Gaussian noise: sigma in `{0.005, 0.01, 0.015, 0.02, 0.025}` scaled by the
  bounding-box diagonal.
- Outliers: `{1%, 2%, 5%, 10%}` uniformly sampled in a 1.2x expanded bounding
  volume, with additional Gaussian noise `sigma=0.005`.
- Sparsity: keep ratios `{75%, 50%, 25%}` after Gaussian noise `sigma=0.01`.
- Rotation: random two-axis rotation with Gaussian noise `sigma=0.01`.
- Seeds: 1 to 10 for each model and scenario.

Please keep the original PCPNet dataset citation when using or redistributing
these benchmark models.
