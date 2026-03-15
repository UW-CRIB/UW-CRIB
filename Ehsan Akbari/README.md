Surrogate Energy Modeling Project
=================================

Overview
--------
This project contains a notebook-based workflow for generating building simulation data,
preparing hourly energy datasets, training surrogate machine learning models, and evaluating
prediction accuracy.

The repository focus on surrogate modeling for building energy or HVAC-related
simulation outputs using three model families:
- Fully Connected ANN
- CNN
- Hybrid ANN-CNN

The main workflow uses Jupyter notebooks and shared intermediate files such as:
- input_parameters.csv
- dataout.csv
- hourly_data_3d.h5

Repository Structure
--------------------
Recommended cleaned structure:

project_root/
├── README.txt
├── requirements.txt
├── .gitignore
├── notebooks/
│   ├── Parametric IDF model- Data generation code.ipynb
│   ├── Evolv_1 clustering divided loads and index calculations .ipynb
│   ├── Evolv Hourly Energy Analysis.ipynb
│   ├── FC_ ANN K-fold for Surrogate model_R01.ipynb
│   ├── CNN K-fold for Surrogate model.ipynb
│   ├── Hybrid ANN-CNN K-fold for Surrogate model_R01.ipynb
│   └── MASE based on standablone hybrid model.ipynb
├── data/
│   ├── raw/
│   ├── processed/
│   └── hourly_data_3d.h5
├── models/
└── results/

Main Notebook Sequence
----------------------
1. Parametric IDF model- Data generation code.ipynb
   Purpose:
   - Generates simulation inputs and modified IDF-based cases
   - Runs or prepares EnergyPlus-style simulation outputs
   - Produces core tabular and hourly datasets

   Referenced outputs:
   - input_parameters.csv
   - dataout.csv
   - dataout_hourly.csv
   - hourly_data_3d.h5
   - geometry_samples.csv
   - simple_samples.csv
   - modified_inputs.csv

2. Evolv_1 clustering divided loads and index calculations .ipynb
   Purpose:
   - Performs clustering of divided loads
   - Computes load-related indices and grouped features
   - Prepares structured information for later analysis

3. Evolv Hourly Energy Analysis.ipynb
   Purpose:
   - Analyzes hourly energy behavior
   - Uses weather and solar-related inputs
   - Supports regression/fitting and hourly structure preparation

   Referenced external-style inputs:
   - Outside_ Temperature.csv
   - POA.csv
   - Solar Angles.csv

4. FC_ ANN K-fold for Surrogate model_R01.ipynb
   Purpose:
   - Trains a fully connected ANN surrogate model
   - Uses K-fold cross-validation
   - Works with shared project inputs

   Common inputs:
   - input_parameters.csv
   - dataout.csv
   - hourly_data_3d.h5

   Example outputs:
   - unified_model_complete.pth
   - fc_ensemble_predicted_hourly_consumption.csv
   - diagnostic plots (.png)

5. CNN K-fold for Surrogate model.ipynb
   Purpose:
   - Trains a CNN-based surrogate model
   - Uses K-fold cross-validation on structured hourly data

   Common inputs:
   - input_parameters.csv
   - dataout.csv
   - hourly_data_3d.h5

   Example outputs:
   - unified_model_complete.pth
   - cnn analysis plots (.png)

6. Hybrid ANN-CNN K-fold for Surrogate model_R01.ipynb
   Purpose:
   - Combines static/tabular inputs and hourly/structured inputs
   - Trains a hybrid surrogate model with K-fold validation
   - Produces ensemble model artifacts and comparative plots

   Common inputs:
   - input_parameters.csv
   - dataout.csv
   - hourly_data_3d.h5

   Example outputs:
   - ensemble_model_fold_1.pth to ensemble_model_fold_5.pth
   - unified_model_complete.pth
   - compressed_hourly_data.csv
   - full_predicted_hourly_consumption.csv
   - ensemble_predicted_hourly_consumption.csv
   - multiple evaluation plots (.png)

Data and File Dependencies
--------------------------
Core data:
- input_parameters.csv
- dataout.csv
- hourly_data_3d.h5

Optional or stage-specific files:
- dataout_hourly.csv
- modified_inputs.csv
- geometry_samples.csv
- simple_samples.csv
- compressed_hourly_data.csv
- features.csv
- X.csv

Model artifacts:
- unified_model_complete.pth
- ensemble_model_fold_1.pth
- ensemble_model_fold_2.pth
- ensemble_model_fold_3.pth
- ensemble_model_fold_4.pth
- ensemble_model_fold_5.pth

Recommended Execution Order
---------------------------
Run the notebooks in this order:

1. Parametric IDF model- Data generation code.ipynb
2. Evolv_1 clustering divided loads and index calculations .ipynb
3. Evolv Hourly Energy Analysis.ipynb
4. FC_ ANN K-fold for Surrogate model_R01.ipynb
5. CNN K-fold for Surrogate model.ipynb
6. Hybrid ANN-CNN K-fold for Surrogate model_R01.ipynb

Notes: Action items prior to execution 
------------------------------
1. Remove hard-coded local file paths
   Several notebooks reference machine-specific paths such as:
   - /Users/User/...
   - /Users/e3akbari/...

   Replace these with relative paths, for example:
   - data/raw/...
   - data/processed/...
   - models/...