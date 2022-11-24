# TomoATT Documentation

This repository contain source codes of [TomoATT Documentation]() powered by Sphinx with [Pydata theme](https://pydata-sphinx-theme.readthedocs.io/en/stable/index.html).

## Build a environment

1. Create a conda environment

```
conda create --name tomoatt-docs --channel conda-forge
```

Then activate the virtual environment

```
conda activate tomoatt-docs
```

2. Install dependence

```
conda install sphinx sphinx-copybutton sphinx-design myst-nb pydata-sphinx-theme
```

## Build the documentation

1. Clone this repository

```
git clone https://github.com/MIGG-NTU/TomoATT-docs.git
cd TomoATT-docs
```

2. Compile and generate documentation in HTML format

```
make html
```

3. The generated documentation is located in the build/html/ directory and can be previewed locally by directly opening build/html/index.html with a browser.