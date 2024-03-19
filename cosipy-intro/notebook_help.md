# Running the tutorial notebooks

The cosipy library can be installed from source or using `pip`, as described in the [main installation instructions](https://cositools.github.io/cosipy/install.html).

There are multiple ways to build a setup that will allow you to run the Jupyter notebooks shipped with this data challenge. Advanced users can pick their favorite methods. Here we described one simple way that works for beginners:

## Install conda

Conda allows you to create virtual Python environments, independent from each other. You might already have conda installed on your machine (try `conda -h`). If not, this is how you can install [miniconda]([https://docs.anaconda.com/free/miniconda](https://docs.anaconda.com/free/miniconda/#quick-command-line-install)), a light version of conda. Open a terminal, `cd` to the directory where you want to install it, and run:

macOS
```
mkdir -p ~/miniconda3
curl https://repo.anaconda.com/miniconda/Miniconda3-latest-MacOSX-arm64.sh -o ~/miniconda3/miniconda.sh
bash ~/miniconda3/miniconda.sh -b -u -p ~/miniconda3
rm -rf ~/miniconda3/miniconda.sh
```

Linux
```
mkdir -p ~/miniconda3
wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh -O ~/miniconda3/miniconda.sh
bash ~/miniconda3/miniconda.sh -b -u -p ~/miniconda3
rm -rf ~/miniconda3/miniconda.sh
```

## Create a new conda environment

This creates a new environment called "cosipy_env" (you can change the name), and install JupyterLab.

```
conda create -n cosipy_env -c conda-forge jupyterlab python=3.10 pip
```

Note: currently cosipy is not compatible with Python 3.11 and 3.12.

After it finishes, activate the environment:

```
conda activate cosipy_test  
```

Note: make sure to re-activate your environment every time you start a new session.

## Install cosipy

With your environment activated, run:

```
pip install cosipy
```

## Download the notebooks

You can download them using the links [here](https://cositools.github.io/cosipy/tutorials/index.html), or by cloning the whole repository by running `git clone git@github.com:cositools/cosipy.git` (they are in the docs/tutorials folder)..

## Start a Jupyter session

`cd` either to your home directory or to the directory where you downloaded the notebooks.

Then, with your environment activated, start a new Jupyter session by running in the terminal:

```
jupyter lab
```

This will open a new tab in your web browser. Use the File Browser on the left to navigate to the location where you have your notebook and open one.

## Running the Jupyter notebook

Use the options from the "Run" menu to run the code. Feel free to modify it and play with it! You can't break anything, and if you find something that is broken please [let us know](https://github.com/cositools/cosipy/issues)!
