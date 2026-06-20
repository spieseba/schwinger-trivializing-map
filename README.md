# Pure U(1) gauge theory in 2D (a.k.a. quenched Schwinger model)

This repo contains my Master thesis code from 2021, archived as-is. No tests or efficiency numbers are provided.
The code depends on [https://github.com/lehner/gpt](https://github.com/lehner/gpt) and is meant to be read more than run.

The interesting/relevant file is `wf_hmc.py`. It samples 2D U(1) gauge theory (the quenched Schwinger model) by running 
the HMC algorithm on a Wilson-flowed version of the gauge field. This field transformation is essentially a 
physics-informed normalizing flow, serving as a *trivializing map*. The idea is to make the sampling distribution *trivial* 
to reduce autocorrelations and topological freezing near the continuum limit.

All other scripts serve to establish baseline simulations (e.g. `hmc.py` is the plain-HMC baseline), run simulations,
or define the measured observables.

## Running it

With GPT importable, from the repo root:

```
python run_wf_hmc.py      # trivializing-map HMC
python run_hmc.py         # plain HMC
python run_metropolis.py
python run_heatbath.py
```

Each script produces 10 trajectories on a 16×16 lattice at beta = 3 and prints the plaquette and
topological charge per trajectory. Parameters are hard-coded at the top of each `run_*.py`.
