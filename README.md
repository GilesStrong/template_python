<!-- [![CI-tests](https://github.com/[username]/[pkg_name]//actions/workflows/CI.yml/badge.svg)](https://github.com/[username]/[pkg_name]/actions) -->

# template_python

## Starting checklist

1. Add `LICENSE` file
1. Rename `name` directory
1. Rename `name.code-workspace`
1. Update and uncomment badges in this readme, and correct installation instructions
1. Correct name in environment.yml and adapt
1. Adapt requirements.txt
1. Adapt and fill setup.py
1. Adapt `.gitignore` as necessary
1. Once tests are added, uncomment test CI in `.github/workflows/CI.yml`
1. For sphinx documentation, update and adapt:
    - `docs/source/conf.py`
    - `docs/run-sphinx-api-doc`
    -  `docs/requirements.txt` -- make sure to include all package requirements

## Installation

Minimum python version is 3.8. Recommend creating a virtual environment, e.g. assuming your are using [Anaconda](https://www.anaconda.com/products/individual)/[Miniconda](https://docs.conda.io/en/latest/miniconda.html) (if installing conda for the first time, remember to restart the shell before attemting to use conda, and that by default conda writes the setup commands to `.bashrc`):

```
conda activate root
conda install nb_conda_kernels
conda env create -f environment.yml
conda activate pkg_name
```

Otherwise set up a suitable environment using your python distribution of choice using the contents of `environment.yml`. Remember to activate the correct environment each time, via e.g. `conda activate pkg_name`.

Install package and dependencies
```
pip install -e .
```

Install pre-commit git-hooks:

```
pre-commit install
pre-commit run --all-files
```

## Testing

Testing is handled by `pytest` and is set up to run during pull requests. Tests can be manually ran locally via:

```
pytest tests/
```

to run all tests, or, e.g.:

```
pytest tests/test_my_pkg.py
```

## Docs building

1. CD to `docs`
1. Run `run-sphinx-api-doc`, and adjust source files as necessary
1. Run `make html`
`. View local docs by opening `_build/html/index.html` in browser