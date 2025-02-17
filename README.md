# Hackathon KRICT: Formation energy prediction

# Project overview
This project was conduced for the 2024 KRICT ChemDX Hackathon hosted from the 6-8 November 2024. Using the dataset from the Chemical Data Explorer (ChemDX) database, we aimed to predict the formation energy of crystalline materials.

# Authors
- Dr. Hoje Chun (Massachusetts Institute of Technology , USA)
- Dr. Chiho Kim (Georgia Institute of Technology, USA)
- Gaheun Shin (Pusan National University, Republic of Korea)

# Objective
Predict formation energy of crystalline materials using materials foundation model.
We compare its efficacy by comparing with the model trained with handcrafted features. Model

# Dataset
The MatDX dataset from ChemDX, which is in `dataset/raw/MatDX_EF.csv`, was used for training and evaluation. 
Starting from 5,000 data points, we filter out outliers that do not contain structure information or that have formation energy greater than 3.5 eV/atom or less than -3.5 eV/atom.
Final dataset is composed of 4,452 data points.

# Moel
We compare two models
- Model 1: Using atomic representation from a foundation model of [MACE-MP0](https://github.com/ACEsuit/mace-mp)
- Model 2: Using the physical data of symetry and density information projected to a high dimensional vector.

# Usage
## Environment settings
```bash
conda create -n krict python=3.10
conda activate krict
```
## Install pytorch mace
[pytorch](https://pytorch.org/)
[mace](https://github.com/ACEsuit/mace)

## Preprocessing data
- Filtering by runing the script `data_reform.py`
```bash
python data_reform.py
```
- Extracting structure infomration and save it to pickle file (Refer to `get_inputs.ipynb`)

## Training:
- Refer to `experiments.ipynb`
## Key features
- Use of minimal required user inputs to simplify the ML model's usability
- Features from foundation model can be used as a baseline models for upcoming ML models

## Future work
- Add the cross-validation step
- Hyperparameter tuning
- Combine two feature sets to train a model
- Use other related properties for multi-task modeling
- Feature importance analysis to gain more insight about the descriptors

# Acknolwedgements
This work was supported by Korea Research Institute of Chemical Technology (KRICT) as part of the 2024 KRICT ChemDX Hackathon, which provided a platform for collaborative research and machine learning applications in materials science.