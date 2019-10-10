# Data and Feature Definitions

This document provides a central hub for the raw data sources, the processed/transformed data, and feature sets. More details of each dataset is provided in the data summary report. 

For each data, an individual report describing the data schema, the meaning of each data field, and other information that is helpful for understanding the data is provided. If the dataset is the output of processing/transforming/feature engineering existing data set(s), the names of the input data sets, and the links to scripts that are used to conduct the operation are also provided. 

For each dataset, the links to the sample datasets in the _**Data**_ directory are also provided. 


## Raw Data Sources


| Dataset Name | Link to Report |
| ---: | -----: |
| Raw Fetched Data | [Report](https://github.com/almeta-io/Azure-TDSP-ProjectTemplate/blob/clickbait_doc/Docs/Data_Report/RawDataSummaryReport.md) |


## Processed Data
| Processed Dataset Name | Input Dataset(s)   | Data Processing Tools/Scripts | Link to Report |
| ---:| ---: | ---: | ---: | 
| Processed Annotated Dataset | [Raw Fetched Data](https://github.com/almeta-io/Azure-TDSP-ProjectTemplate/blob/clickbait_doc/Docs/Data_Report/RawDataSummaryReport.md) | [Normalization](https://github.com/almeta-io/almeta-clickbait/blob/w2v_version/clickbait_detector/preprocessing.py#L7), [Tokenization](https://github.com/almeta-io/almeta-clickbait/blob/w2v_version/clickbait_detector/preprocessing.py#L33) | [Report](https://github.com/almeta-io/Azure-TDSP-ProjectTemplate/blob/clickbait_doc/Docs/Data_Report/PreprocessedDataSummaryReport.md)|

* Processed Annotated Dataset summary: The data was sampled from the input data, then the samples were manually annotated. 

## Feature Sets

| Feature Set Name | Input Dataset(s)   | Feature Engineering Tools/Scripts | Link to Report |
| ---:| ---: | ---: | ---: | 
| Simple Feature Set | [Processed Annotated Dataset](https://github.com/almeta-io/Azure-TDSP-ProjectTemplate/blob/clickbait_doc/Docs/Data_Report/PreprocessedDataSummaryReport.md) | [Features Extractors](https://github.com/almeta-io/almeta-clickbait/blob/dev/clickbait_detector/features_extractors.py) | [Report](https://github.com/almeta-io/Azure-TDSP-ProjectTemplate/blob/clickbait_doc/Docs/Data_Report/SimpleFeaturesModelingDataSummaryReport.md)|
| Wor2Vec Feature Set | [Processed Annotated Dataset](https://github.com/almeta-io/Azure-TDSP-ProjectTemplate/blob/clickbait_doc/Docs/Data_Report/PreprocessedDataSummaryReport.md) |[W2VTransformer](https://github.com/almeta-io/almeta-clickbait/blob/w2v_version/clickbait_detector/features_extractors.py#L53) | [Report](https://github.com/almeta-io/Azure-TDSP-ProjectTemplate/blob/clickbait_doc/Docs/Data_Report/W2VModelingDataSummaryReport.md)|
