# Access to Green Space in Scotland

Using datasets derived from historic Scottish Household Surveys, the intention of the project was to address levels of local access to green spaces among the Scottish population. In particular, the following 3 Business Questions were addressed:

1. Are there certain groups that have local access to green space? Are there groups that are lacking access?
2. Are there any differences between rural and urban areas?
3. How do people in neighbourhoods with good access to green space differ from those who have no good access? Are there differences in how they rate their neighbourhoods? Are there differences in how they rate their communities?

# Datasets

3 main datasets were used to answer the above questions. The data contained within the datasets derived from previous years Scottish Household Surveys and were accessed via the statistics.gov.scot website. The specific data cube slices accessed were:

1. [Distances to Green or Blue Space - SHS](https://statistics.gov.scot/resource?uri=http%3A%2F%2Fstatistics.gov.scot%2Fdata%2Fgreen-or-blue-space-shs)

2. [Neighbourhood rating - SHS](https://statistics.gov.scot/slice?dataset=http%3A%2F%2Fstatistics.gov.scot%2Fdata%2Fneighbourhood-rating---shs&http%3A%2F%2Fstatistics.gov.scot%2Fdef%2Fdimension%2Fgender=http%3A%2F%2Fstatistics.gov.scot%2Fdef%2Fconcept%2Fgender%2Ffemale)

3. [Community belonging - SHS](https://statistics.gov.scot/resource?uri=http%3A%2F%2Fstatistics.gov.scot%2Fdata%2Fcommunity-belonging---shs)

## Issues with the data

There were three main issues that I had when dealing with the above datasets:

1. Only one characteristic variable could be sub-divided at a time. i.e age or gender but not both (no figures for Males over 65 years old for example)

2. Although these variables could be sub-divided by local authority and year, some figures were missing

3. All numeric values were in the form of percentages. i.e. the percentage of Males in Edinburgh that reported living 10 minutes from green spaces.

![Example of selection page for data][

![Example of data once read into R][
