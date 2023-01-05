# Example of using Quarto with SAS (via `sas_kernel`)

## Prerequisites

1. Install a Java Runtime Environment (required by `sas_kernel`), and add it to your system's `PATH` variable.
1. Put SAS's `SASHome\SASFoundation\9.4\core\sasext` in your system's `PATH` variable.
1. Install [Quarto](https://quarto.org/).
1. Use Python and Pipenv to install the packages listed in the included `Pipfile`. Usually `pipenv install --dev` should do the trick.
1. Check that `jupyter kernelspec list` lists the "sas" kernel.
1. For an operating system other than Windows, edit `sascfg_personal.py` to select your SAS configuration.

## Building the Quarto output

From shell prompt:

1. `pipenv shell`
1. `quarto render sas-example.qmd`

## Troubleshooting

### Verify that Jupyter is set up correctly

1. `jupyter nbconvert check-python.ipynb --to html --execute`
1. `quarto check jupyter`

### Check that quarto and python work with the pure Python version

1. `quarto render check-python.qmd --debug`

### Try the saspy version

1. `quarto render check-saspy.qmd --debug`

### Keep intermediate artifacts

1. `quarto render sas-example.qmd --debug`

### Render in stages

1. `quarto convert sas-example.qmd`
1. Inspect `sas-example.ipynb`.
1. `quarto render sas-example.ipynb`

## TODO
