# General summary of the data

Unlabeled dataset fetched from the web for the purpose of annotating a training dataset for the clickbait classification problem.<br><br>

## The data sources

The following table summarizes the data sources and the amount of the fetched data from each source domain:

|Source domain|Data type|Data amount|
|:-----------:|:-------:|:---------:|
|[ra2ej](https://www.ra2ej.com/)|clickbait|~35,000 Articles|
|[yemensaeed](https://www.yemensaeed.com)|clickbait|~200 Articles|
|[arageek](https://www.arageek.com/)|clickbait|~19,000 Articles|
|[mawdoo3](https://www.mawdoo3.com)|not clickbait|~30,000 Articles|
|[almayadeen](https://www.almayadeen.net)|not clickbait|~35,000 Articles|

## Dataset Fields Description

The data was fetched using the [Scrapy](https://scrapy.org/) library in Python. And was organized in .json format, with the following fields for each data item:

|Field|Description|
|-----|-----------|
|id|An automatically generated idintifier|
|url|A URL to the article|
|title|The title of the article|
|publish_date|The date when the article was published|
|meta_description|A brief description of the article, was taken from the meta data of the page|
|main_img|The URL of the lead image in the page|
|content|The content of the article|

