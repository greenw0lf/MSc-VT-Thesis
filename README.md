# MSc-VT-Thesis

This repository contains the scripts and CSV files that I used throughout my master's thesis for training and testing ASR models, as well as analyze the datasets. The master's I completed is the M.Sc. Voice Technology at Rijksuniversiteit Groningen - Campus Fryslân in June 2023.

## Prerequisites
- `Python 3.9.6` (this is the version used in experiments and guaranteed to work, other `3.9.x` versions may also work, as well as newer ones such as `3.10`, but I have not experimented with those)

## Usage
The scripts are contained within Jupyter Notebook files (`.ipynb`). Therefore, Jupyter Notebook must be installed. In a high-performance computing (HPC) cluster setting (Linux environment), this can be done by first creating a Python virtual environment:
```
python -m venv name_of_venv
```
Then, activate the newly created environment:
```
source /path/to/name_of_venv/bin/activate
```
in Windows:
```
/path/to/name_of_venv/Scripts/activate
```
If you want to install Jupyter and the dependencies from all notebooks, you can run:
```
pip install -r requirements.txt
```
If not, then you can first install Jupyter Notebook:
```
pip install jupyter
```
Then install the dependencies you need by running the first cell of the notebook you are editing.
