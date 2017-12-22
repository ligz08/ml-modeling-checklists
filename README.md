# ml-modeling-checklists
Machine Learning Modeling Checklists

## Load Data
- [`pd.read_csv()`](https://pandas.pydata.org/pandas-docs/stable/generated/pandas.read_csv.html)
(useful options: `use_col`, `parse_dates`)

## Check data
- Check shape  
- Check missing values  
- (Cat features) check label counts split (train vs. test) -- bar plot  
- (Cont features) check distribution -- violin plot  
- (Target feature) check distribution/patterns, imbalanced?

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
- [Train-test split](http://scikit-learn.org/stable/modules/generated/sklearn.model_selection.train_test_split.html)
- [Model choice](http://scikit-learn.org/stable/tutorial/machine_learning_map/index.html)

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
