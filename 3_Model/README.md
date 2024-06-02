# Model Definition and Evaluation

## Pipeline creation

### 1. Stage - Import, prepare base data

Use preapare Jupyter Notebooks for kiwo,sales and waetherdata in folder "0_DataPreparation" to export every datasets into pickle export files into folder "exported_data".

This stage do the following:
- Load dataset from .csv files out of folder "bakery_sales_data"
- Convert datatype in better usable types eg. datetime for dates
- Merge every file with prepared "base_datarange_data" frame to get a timeseries for the whole needed time
- Add missing data
- Calculate new data fields or group data 
- export preapared panda dataframes to pickle files into folder "exported_data"

### 2. Stage - Add more data and combine to one Dataframe

Here we use Jupyter Notebook "DataAddAndMerge.ipynb" in folder "0_DataPreparation" to merge all datasets and add more data from external sources and import full created dataframe into folder "exported_data".

This stage do the following:
- Load the prepared pickle datasets out of folder "exported_data" and merge them into on dataframe
- Add more data from external source out of CSV files in folder "bakery_sales_data"
- Export Full dataframe into folder "exported_data" 

### 3. Stage - Split the dataset

Script "SplitDataset.ipynb" for this stage is located in folder "0_DataPreparation"

This stage do the following:
- splits the datasets into three sets
- remove "Umsatz" and "Warengruppe" from test_set to allow later merge with test.csv data and prediction values
- merge the test.csv content to test set to get dates and Warengruppe for needed later kaggle submission

### 4. Stage - Create and optimize the Model

Baseline model is calculated in file "BaselineModel.ipynb" in folder "2_Baselinemodel" and uses to create a first running prediction by using linear regression and see what features might have impact to prediction and what features not. 

### 5. Stage validation of the model

Check how the model will behave under validation data it has not used to train the model.

### 6. Stage - Fill test dataset with predictiondata of created model 

Use the Model, created in Stage 4. and reduce dataset only to needed prediction values and remove all columns except "id" and "Umsatz" to make a upload to kaggle possible. 