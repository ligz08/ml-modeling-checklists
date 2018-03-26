# ml-modeling-checklists
Machine Learning Modeling Checklists

## Load
- Basic packages
```python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

%matplotlib inline
```

- [`pd.read_csv()`](https://pandas.pydata.org/pandas-docs/stable/generated/pandas.read_csv.html)
(useful options: `use_col`, `parse_dates`)

## Explore
- Shape: observations, features  
- Missing values  
- Cat features: check distribution -- bar plot  
- Num features: check distribution -- 
    [violin plot](https://seaborn.pydata.org/generated/seaborn.violinplot.html)  
- Target feature: check distribution/patterns, imbalanced?
- Correlations between...
    - Num & num: scatter plot
    - Num & cat: violin plot
    - Cat & cat: mosaic plot

## Clean
- Missing values


## Feature Engineering
- DateTime → year, month, weekday, day of year...
- String → extract info with regex


## Preprocessing
### Preprocessing categorical features
- [LabelEncoder](http://scikit-learn.org/stable/modules/generated/sklearn.preprocessing.LabelEncoder.html)
- Bins to number (e.g. bin → mean or mode / bin → lower&uper bound)
- Combine labels (e.g. 95616 → 956) (e.g. rare levels → ‘other’)
- Cat → {0,1} encoding: [`pd.get_dummies()`](https://pandas.pydata.org/pandas-docs/stable/generated/pandas.get_dummies.html)
  / [One-hot encoder](http://scikit-learn.org/stable/modules/generated/sklearn.preprocessing.OneHotEncoder.html)

### Preprocessing continuous features
- Binning?
- Check skewness
- Transform
- Normalize
- Make new features? (e.g. height & weight → BMI)
- Outliers?
- [Dimension reduction / PCA](Dimension%20Reduction.md) / Factor analysis?


## Modeling
### Model Choice
- [Train-test split](http://scikit-learn.org/stable/modules/generated/sklearn.model_selection.train_test_split.html)
- [Model choice](http://scikit-learn.org/stable/tutorial/machine_learning_map/index.html)

### Model Tuning
- Use cross validation if possible

### Ensembling

## Evaluation
- `sklearn.metrics`  
    - `metrics.accuracy_score`  
    - `metrics.confusion_matrx`  
    - `metrics.recall_score`, `metrics.precision_score`  
    - `metrics.roc_curve`
    - `metrics.roc_auc_scroe`  
    - `metrics.classification_report`
- `sklearn.cross_validation`  
    - `cross_val_score`
