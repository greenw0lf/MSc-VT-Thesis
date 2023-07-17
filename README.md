# MSc-VT-Thesis

This repository contains the scripts and CSV files that I used throughout my master's thesis for training and testing ASR models, as well as analyzing the datasets. The master's I completed is the M.Sc. Voice Technology at Rijksuniversiteit Groningen - Campus Fryslân in June 2023.

The experiments were conducted on [Mozilla's Common Voice project](https://commonvoice.mozilla.org/). The version used is 8.0, and the language is Frisian, marked as `fy-NL` in the metadata.

## Link to thesis
*Coming soon*

## Prerequisites
- `Python 3.9.6` (this is the version used in experiments and guaranteed to work, other `3.9.x` versions may also work, as well as newer ones such as `3.10`, but I have not experimented with those)

## Installing dependencies
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
Then install only the dependencies you need by running the first cell of the notebook you are editing.

## Usage
Simply run a Jupyter instance:
```
jupyter notebook
```
Then access the notebooks via the browser.

## Files
- The `.ipynb` files that start with `XLS_R` are the training scripts I used throughout my research
  - `XLS_R_fine_tune_train_from_hf.ipynb` corresponds to the script used for experiment 1
  - `XLS_R_fine_tune_local_train.ipynb` corresponds to the scripts used for experiments 2-7
- `evaluation.ipynb` is the file used for evaluating the models
- `data_split_analysis.ipynb` is the file used for analyzing the datasets, as well as generating the splits for experiments 2-7
- Inside `cv-corpus-8.0-2022-01-19/fy-NL` you can find the `.csv` splits of experiments 3, 4, and 5 (10 hours, 1 hour, and 10 minutes of training data respectively), along with statistics grouped by age and sex of the speaker (marked by `_stats.csv` at the end)

## Hardware setup
The most important part to make the training and evaluation notebooks run without memory overflow issues is the GPU and the video RAM that it contains. The experiments were conducted on an Nvidia A100 GPU accelerator card with 40 GB of VRAM. There should also be a minimum amount of 20 GB of RAM (NOT VRAM) available. It is recommended to run them either through Google Colab (and a Pro subscription is a must to have access to the better GPUs) or through a high-performance cluster, if possible. If not, certain settings could be adjusted in order to allow the notebooks to not crash due to memory overflow.

The time required for training the models varies depending on the amount of data used and the hyperparameters related to checkpointing and the number of epochs. For testing, the time it takes is ~3.5 hours (using the `test` set from Common Voice 8.0) for XLS-R with 1 billion parameters.

## Research output
Here is a list of the XLS-R models fine-tuned throughout my thesis that were uploaded to Hugging Face (if the number of parameters is not mentioned, then it is 1B parameters):
- [Experiment 1](https://huggingface.co/greenw0lf/wav2vec2-large-xls-r-1b-frisian-cv-8) (train split of CV 8.0, 5 hours of data, training time: 4 hours)
- [Experiment 2](https://huggingface.co/greenw0lf/wav2vec2-large-xls-r-1b-frisian-cv-8-large-train) (41 hours of data, training time: 22 hours)
- [Experiment 3](https://huggingface.co/greenw0lf/wav2vec2-large-xls-r-1b-frisian-cv-8-10h) (10 hours of data, training time: 7.5 hours)
- [Experiment 4](https://huggingface.co/greenw0lf/wav2vec2-large-xls-r-1b-frisian-cv-8-1h) (1 hour of data, training time: 1.5 hours)
- [Experiment 5](https://huggingface.co/greenw0lf/wav2vec2-large-xls-r-1b-frisian-cv-8-10m) (10 minutes of data, training time: 45 minutes)
- [Experiment 6](https://huggingface.co/greenw0lf/wav2vec2-large-xls-r-300m-frisian-cv-8) (41 hours of data, XLS-R with 300M parameters, training time: 16 hours)
- [Experiment 7](https://huggingface.co/greenw0lf/wav2vec2-large-xls-r-2b-frisian-cv-8) (41 hours of data, XLS-R with 2B parameters, training time: 1 day)

## Contact
if you have any suggestions, feel free to create a PR with your changes and I'll review it as soon as possible.

If you have any questions, open an issue. Disclaimer: the more time it will pass, the less able I will be to respond to questions as I will most likely forget details. I apologize for that :)
