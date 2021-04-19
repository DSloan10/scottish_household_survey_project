# Access to Green Space in Scotland

Using datasets derived from historic Scottish Household Surveys, the intention of the project was to address levels of local access to green spaces among the Scottish population. In particular, the following 3 Business Questions were addressed:

1. Are there certain groups that have local access to green space? Are there groups that are lacking access?
2. Are there any differences between rural and urban areas?
3. How do people in neighbourhoods with good access to green space differ from those who have no good access? Are there differences in how they rate their neighbourhoods? Are there differences in how they rate their communities?

## Datasets

Three main datasets were used to answer the above questions. The data contained within the datasets derived from previous years Scottish Household Surveys and were accessed via the statistics.gov.scot website. The specific data cube slices accessed were:

1. [Distances to Green or Blue Space - SHS](https://statistics.gov.scot/resource?uri=http%3A%2F%2Fstatistics.gov.scot%2Fdata%2Fgreen-or-blue-space-shs)

2. [Neighbourhood rating - SHS](https://statistics.gov.scot/slice?dataset=http%3A%2F%2Fstatistics.gov.scot%2Fdata%2Fneighbourhood-rating---shs&http%3A%2F%2Fstatistics.gov.scot%2Fdef%2Fdimension%2Fgender=http%3A%2F%2Fstatistics.gov.scot%2Fdef%2Fconcept%2Fgender%2Ffemale)

3. [Community belonging - SHS](https://statistics.gov.scot/resource?uri=http%3A%2F%2Fstatistics.gov.scot%2Fdata%2Fcommunity-belonging---shs)

## Issues with the data

There were three main issues that I had when dealing with the above datasets:

1. Only one characteristic variable could be sub-divided at a time. i.e age or gender but not both (no figures for Males over 65 years old for example)

2. Although these variables could be sub-divided by local authority and year, some figures were missing

3. All numeric values were in the form of percentages. i.e. the percentage of Males in Edinburgh that reported living 10 minutes from green spaces.

![Example of selection page for data](https://github.com/DSloan10/scottish_household_survey_project/blob/main/presentation_pngs/Database%20Screenshot.png)

<br />

![Example of data once read into R](https://github.com/DSloan10/scottish_household_survey_project/blob/main/presentation_pngs/R%20Example.png)

## Useful definitions

There are a few definitions useful when considering the data and the resulting insights:

* All percentages refer in some way or another to adults, classed as over the age of 16, between the years 2013 and 2019.
* Green and Blue Space is described in the Scottish Household Survey as comprising ‘public green or open spaces in your local area, for example a park, countryside, wood, play area, canal path, riverside or beach’.
* The walking-distance responses detailed are purely subjective. It seems quite a good measure to capture the desired information (i.e psychological rather than necessarily physical).

##Q1: Do certain groups that have more/less access to green space?

In addressing the first of these questions, it was important to decide on a suitable meausure of "local access". Two potential measures were available through the data set, post wrangling. The first was for those that lived within a 10-minute walk of green space, the second for those that lived within a 5-minute walk.

I decided to start by assertaining whether any sustained gaps were evident amongst different groups of the population. To do this, I took mean percetages from across the years addressed (2013 and 2019) for these different groups.

In terms of the 10-minute measure, dividing the population by categories and then sub groups produced a fairly homogenous picture, with the majority of groups having 80 per cent of respondents or higher. The exception to this pattern was those labeled as of "Non White Ethnicity", and the first sign of a fairly worrying trend in the data:

![](https://github.com/DSloan10/scottish_household_survey_project/blob/main/presentation_pngs/graph_1_final.png)





