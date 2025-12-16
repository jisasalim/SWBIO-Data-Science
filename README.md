# Building a machine learning model to predict the optical density of Acinetobacter baumannii
This project utilises supervised machine learning to predict the growth of Acinetobacter baumannii isolates grown in media supplemented with and without glucose. 

# Experimental Design 
Organism: Acinetobacter baumannii
Isolates:
- NCTC 12156 - Wild-type
- ATCC 1710 - Human isolate
- SM37212 - Clinical isolate
- SM55869 - Clinical isolate
- SM52892 - Clinical isolate

Growth conditions:
- Tryptic soy broth + 1% (v/v) glucose
- Tryptic soy broth only (no glucose)

Measurement: OD @ 600nm
Duration: OD taken every hour for 48-hours. Time is measured in seconds (s)    

# Dataset information
**File:** `glucose_growth_curves_48h.csv
The dataset consists of OD readings taken from a growth curve assay. Each row is a single OD measurement at a specific time point. 

**Columns:**
- `isolate` – bacterial isolate identifier
- `glucose_vv` – glucose concentration (% v/v)
- `experiment_repeat` – experimental repeat number
- `well_id` – microplate well identifier
- `time_s` – time in seconds
- `OD` – optical density (target variable)

## Dependencies 
This project requies Python 3 and the following libraries:
- pandas 
- numpy
- seaborn
- matplotlib
- scikit-learn

## Methodology

**Data Cleaning:**
Removed NaN values 
Converted categorical variables (`isolate`, `glucose_vv`, `experiment_repeat`, `well_id`)
- Time (`time_s`) is treated as a numerical feature.

**Feature Engineering:**
Selected features: `isolate`, `glucose_vv`, `experiment_repeat`, `well_id`, `time_s`  
Target variable: `OD` 

**Modeling:**
RandomForestRegressor 
GradientBoostingRegressor
Model trained on 80% and tested on 20%)

**Model evaluation:** 
Root mean squared error (RMSE)
Coeffiecient of determination (R²)

5-fold cross-validation on training set 
Predicted vs actual OD values plotted using scatter plots

## Machine Learning Models
The models are implemented in Python using `scikit-learn`.  
Pipelines include pre-processing steps:

- **One-hot encoding** for categorical variables  
- **RandomForestRegressor** with 500 trees  
- **GradientBoostingRegressor** with 500 estimators and learning rate 0.05

**Prediction example:**

```python
# Predict OD at 5 hours for a specific isolate and condition 
predict_OD(rf_pipeline, "NCTC12156", 1, 1, "A1", 18000) 

## Usage 
1. Clone the repository 
git clone https://github.com/jisasalim/SWBIO-Data-Science.git
cd SWBIO-Data-Science
2. Open Jupyter notebook 
juypter notebook acinetobacter_v2.ipynb
3. Follow notebook instructions to:
   - Load the dataset  
   - Train machine learning models  
   - Evaluate model performance  
   - Generate OD predictions for specific isolates


 
# Built With

- [Python 3.x](https://www.python.org/)  
- [pandas](https://pandas.pydata.org/)  
- [numpy](https://numpy.org/)  
- [matplotlib](https://matplotlib.org/)  
- [seaborn](https://seaborn.pydata.org/)  
- [scikit-learn](https://scikit-learn.org/stable/)  
- [JupyterLab](https://jupyter.org/)  

    