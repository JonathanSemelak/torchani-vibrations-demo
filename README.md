# torchani-vibrations-demo

A short tutorial notebook that walks through how a Machine Learning Interatomic
Potential (MLIP) — here, [TorchANI](https://github.com/aiqm/torchani) — can be
used to:

1. predict the energy of a molecule given its 3D structure,
2. take first derivatives of that energy to get forces, and use them to relax
   a structure to its equilibrium geometry,
3. take second derivatives to get the Hessian, from which the vibrational
   frequencies that show up in an infrared (IR) spectrum can be obtained.

The worked example is gas-phase water with the ANI-1x model.

## Installation

The notebook depends on `torchani`, `pytorch`, `ase`, `py3dmol`, `numpy`,
`matplotlib`, and `jupyterlab`. All of them are available on
[conda-forge](https://conda-forge.org/), so the environment is fully
conda-installable.

You'll need a working conda (or mamba/micromamba) installation. If you don't
have one yet, [Miniforge](https://github.com/conda-forge/miniforge) is the
simplest option and ships with conda-forge configured by default.

### Create the environment

```bash
git clone git@github.com:JonathanSemelak/torchani-vibrations-demo.git
cd torchani-vibrations-demo
conda env create -f environment.yaml
conda activate torchani-vibrations-demo
```

If you have `mamba` available, replace `conda env create` with
`mamba env create` — it's significantly faster.

### CPU vs GPU

The notebook runs on CPU (`device = torch.device("cpu")`), so a CPU-only
PyTorch build is enough. Conda will pick the right `pytorch` build for your
platform automatically. If you want GPU support, install a CUDA-enabled build
of `torchani` explicitly:

```bash
conda install -c conda-forge "torchani=*=cuda*"
```

## Running the notebook

```bash
jupyter lab vibration_analysis.ipynb
```

The notebook is self-contained and runs end-to-end in well under a minute on
a laptop CPU.
