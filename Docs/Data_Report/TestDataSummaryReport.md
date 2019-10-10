# General summary of the data

Unlabeled dataset collected for the purpose of analysing the clickbait classifiers performance.<br><br>

It was collected from Almeta news feed + other titles collected from the URLs in the sitemaps of some news outlets websites.<br><br>

**The size of the dataset**: ~14,000 samples

## The data sources

1. [Aljazeera](https://www.aljazeera.net)
2. [Alarabyia](https://www.alarabiya.net)
3. [BBC Arabic](https://www.bbc.com/arabic)
4. [DW Arabic](https://www.dw.com/ar/)
<br>
Where none of these domains were used to collect the training data.
<br>
Following is the distribution of the samples density over the source news outlets:
![](img/test/outlets_dist.png)

## Dataset Fields Description

The dataset is provided in .csv format, where each record is composed of the following fields:

|Field|Description|
|-----|-----------|
|url|A URL to the article|
|outlet|The news outlet where the title comes from|
|title|The title of the news article|

