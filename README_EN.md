# svd

Utilizando SVD para prever avaliações de filmes

If you are going to *develop* from this repository, go to the [development guide](README_DEV.md).

## Installing svd:

Remember to follow these instructions from within your preferred virtual environment:

    conda create -n svd python=3.11
    conda activate svd

The first way is to clone the repository and do a local installation:

    git clone https://github.com/henriquebrnetto/svd.git
    cd svd
    pip install .

The second way is to install directly:

    pip install git+https://github.com/henriquebrnetto/svd.git

To uninstall, use:

    pip uninstall svd

## Usage

To find all implemented commands, run:

    svd-cli --help
