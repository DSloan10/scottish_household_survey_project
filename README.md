# Access to Green Space in Scotland

Using datasets derived from historic Scottish Household Surveys, the intention of the project was to address levels of local access to green spaces among the Scottish population. In particular, the following 3 Business Questions were addressed:

1. Are there certain groups that have local access to green space? Are there groups that are lacking access?
2. Are there any differences between rural and urban areas?
3. How do people in neighbourhoods with good access to green space differ from those who have no good access? Are there differences in how they rate their neighbourhoods? Are there differences in how they rate their communities?

<br />

## Datasets

Three main datasets were used to answer the above questions. The data contained within the datasets derived from previous years Scottish Household Surveys and were accessed via the statistics.gov.scot website. The specific data cube slices accessed were:

1. [Distances to Green or Blue Space - SHS](https://statistics.gov.scot/resource?uri=http%3A%2F%2Fstatistics.gov.scot%2Fdata%2Fgreen-or-blue-space-shs)

2. [Neighbourhood rating - SHS](https://statistics.gov.scot/slice?dataset=http%3A%2F%2Fstatistics.gov.scot%2Fdata%2Fneighbourhood-rating---shs&http%3A%2F%2Fstatistics.gov.scot%2Fdef%2Fdimension%2Fgender=http%3A%2F%2Fstatistics.gov.scot%2Fdef%2Fconcept%2Fgender%2Ffemale)

3. [Community belonging - SHS](https://statistics.gov.scot/resource?uri=http%3A%2F%2Fstatistics.gov.scot%2Fdata%2Fcommunity-belonging---shs)

<br />

## Issues with the data

There were three main issues that I had when dealing with the above datasets:

1. Only one characteristic variable could be sub-divided at a time. i.e gender or age but not both (no figures for Males over 65 years old for example)

2. Although these variables could be sub-divided by local authority and year, some figures were missing

3. All numeric values were in the form of percentages. i.e. the percentage of Males in Edinburgh that reported living 10 minutes from green spaces.

![Example of selection page for data](https://github.com/DSloan10/scottish_household_survey_project/blob/main/presentation_pngs/Database%20Screenshot.png)

<br />

![Example of data once read into R](https://github.com/DSloan10/scottish_household_survey_project/blob/main/presentation_pngs/R%20Example.png)

<br />

## Useful definitions

There are a few definitions useful when considering the data and the resulting insights:

* All percentages refer in some way or another to adults, classed as over the age of 16, between the years 2013 and 2019.
* Green and Blue Space is described in the Scottish Household Survey as comprising ‘public green or open spaces in your local area, for example a park, countryside, wood, play area, canal path, riverside or beach’.
* The walking-distance responses detailed are purely subjective. It seems quite a good measure to capture the desired information (i.e psychological rather than necessarily physical).

<br />

## Q1: Do certain groups that have more/less access to green space?

In addressing the first of these questions, it was important to decide on a suitable meausure of "local access". Two potential measures were available through the data set, after wrangling. The first was for those that lived within a 10-minute walk of green space, the second for those that lived within a 5-minute walk.

I decided to start by assertaining whether any sustained gaps were evident amongst different groups of the Scottish population. To do this, I took mean percetages from across the years addressed (2013 and 2019) for these different groups.

In terms of the 10-minute measure, dividing the population by categories and then sub groups produced a fairly homogenous picture, with the majority of groups having 80% of respondents or higher. The exception to this pattern was those labeled as of "Non White Ethnicity", and the first sign of a fairly worrying trend in the data:

<br />

![](https://github.com/DSloan10/scottish_household_survey_project/blob/main/presentation_pngs/graph_1_final.png)

After checking [National Performance indicators that the Scottish Government had previously used](https://nationalperformance.gov.scot/access-green-and-blue-space), I also decided to look at the differences among groups in 5-minute access:

<br />

![](https://github.com/DSloan10/scottish_household_survey_project/blob/main/presentation_pngs/graph_2_final.png)

Casting aside the urban/rural divide (more on this in Q2), it seemed apparent that 3 particular gaps grew in 3 different categories between the two distances:

1. The gap between White and Non-White Ethnicity widened from 8 percentage points (pp) to 13 pp (87% vs 79%, 67% vs 54%)

2. The gap between those with and outstanding Mortgage/Domestic Loans and those in Social Renting accommodation widened from 5 pp to 9 pp (89% vs 84%, 71%vs 62%

3. The gap between the 80% least deprived and the 20% most deprived widened from 4 pp to 8 pp (87% vs 83%, 68% vs 60%)

<br />

### Further analysis of differences between these groups

95% confident intervals were included within the datasets for each percentage reported. Along with these intervals, I plotted the percentages across the years being addressed to establish whether I could be confident that a sustained gap between the groups was evident:

<br />

![](https://github.com/DSloan10/scottish_household_survey_project/blob/main/presentation_pngs/graph_3_final_ethnicity_plot_n5s.png)

Although, the confidence intervals where fairly wide for the "Non-White Ethnicity" group, it was clear that even with this wide interval applied, a sustained gap existing over all but one year. To me, this suggested that there was a sustained inequality between the two groups in their level of access across the years addressed.

<br />

![](https://github.com/DSloan10/scottish_household_survey_project/blob/main/presentation_pngs/graph_4_final_tenure_plot_n5s.png)

With the 95% confidence intervals applied, a sustained gap in 5-minute access is shown between those with a mortgage and those in social rented accomodation. Interestingly, the gap seemed to narrow between the two groups in the most recent year that figures are available. I will be interesting to see if this is a sustained trend or if it merely a blip on the more general gap. 

<br />

![](https://github.com/DSloan10/scottish_household_survey_project/blob/main/presentation_pngs/graph_5_final_simd_plot_n5s.png)

Once again, a gap is maintained across the years addressed when looking at the most and least deprived members of Scottish society. The gap once again narrows in 2019, suggested a degree of correlation between the second and third inequalites addressed here, although this should be more thoroughly evidenced if it is to be stated with great confidence.

<br />

## Q1 Extra. SG - Estimating Statistically Significant Change 

To retrospectively access the level of statistical significance in any reported change, the Scottish Government sometimes use a methodology combining point estimates and 95% confidence intervals.

<br />

**_Method_**

Check the following:

1.	The difference between a and b is greater than or equal to the sum of the magnitude of the intervals 

**if False**

2.  The difference between a and b is smaller than the larger interval of the two points

**if False**

3. The difference between a and b is greater than or equal to the square root of the sum of the squares of the two magnitudes

**if none of the above are True, no statistical significance**

<br />

I applied this method to the different sub-groups for which percentages where available across the Scottish population. Percentages reported in 2013 were taken as **a** and percentages reported in 2019 taken as **b**:

<br />

![](https://github.com/DSloan10/scottish_household_survey_project/blob/main/presentation_pngs/graph_6_final.png)

This tells an interesting story in terms of some of the groups we have previously addressed. The main takeaway from the analysis however is that, amongst those group that there is a statistically significant change, all have seen have seen a drop in percentages reflecting access since 2013.

<br />

## Q2. Urban vs Rural Access

Multiple definitions of what constitutes Urban or Rural living used in Scottish Government data gathering. The definition used in the SHS is 2-fold, defined as follows:

**Urban** - areas of settlement with 10,000 people or more.

**Rural** - areas of settlement with less than 10,000 people. 

This seems quite a strict dichotomy:

<br />

![](https://github.com/DSloan10/scottish_household_survey_project/blob/main/presentation_pngs/00533574.jpg)

Returning to the 95% confidence intervals, the most consistent gap between two groups across the datasets presents itself. In many ways this seems like an unsurprising and intuititive insight.

Taking a single year (2019) as an example, we can see there is perhaps more variation in access at a local authority level than simple population density would suggest:

<br />

![](https://github.com/DSloan10/scottish_household_survey_project/blob/main/presentation_pngs/5-min_map_with_shet.png)

<br />

![](https://github.com/DSloan10/scottish_household_survey_project/blob/main/presentation_pngs/pop_dens_with_shet.png)

Returning to mean figures between 2013 and 2019, I decided that it would be appropriate to explore differences between local authorities(LAs):

<br />

![](https://github.com/DSloan10/scottish_household_survey_project/blob/main/presentation_pngs/graph_9a_by_local_authority_final.png)

Addressing each of the LAs in relation to the all Scottish mean, it is clear that many 'all city' authorities fall well below the Scottish average in terms of local access, with Glasgow City and Dundee City reporting particuarly low average percentages. It is intesting to note the position of some LAs that I would first have thought would be higher or lower e.g. Orkney Islands lower, City of Edinburgh higher. This showcases the fact that there are certainly exceptions to the Rural = Good Access, Urban = Bad Access rule. Equally, it demonstrates that just because individuals are surrounded by green space, it does not necessarily mean that such individuals feel like they have access to it. 

<br />

![](https://github.com/DSloan10/scottish_household_survey_project/blob/main/presentation_pngs/graph_9_b_electoral_regions_final.png)

Grouping these LAs into Electoral Regions demonstrates the impact that surrounding authorities can have on lower percentages of access in some urban areas. Those living in Aberdeen and Dundee, when grouped in the overall Grampian and Tayside regions, are part of groups with far more positive levels of access. In comparison, Glasgow as an Electoral Region in its own right has by far the lowest level of access amongst this grouping.

<br />

## Q2 Extra. Gender Divide?: Four largest cities 

Looking in some more detail at the percentages of access reported in individual cities, some more interesting insights on become apparent:

<br />

![](https://github.com/DSloan10/scottish_household_survey_project/blob/main/presentation_pngs/graph_10_final.png)

The impetus to investigate the gender divides within the four largest cities came from the fact that, when reviewing the data, the lowest percentage of 5-minute access reported across all groups was that of Females in Dundee in 2014 (43%). Looking at comparisons between different years and between cities, this looks like is could be a bit of an anomoly, although it certainly merits further investigation.

In general, we see percentages reporting local access to green spaces generally being lower amongst emales that amongst males in cities, although the differences are neglible for most years. What is clear is that in Aberdeen and Dundee, female and male genders both have falling percentages reporting local access, with the trend particualtly pronounced in Aberdeen since 2014. In comparison, both Edinburgh and Glasgow appear to have relatively stable access for both male and female genders, although the former has consistently higher access than the latter.

<br />

## Differences in Neighbourhood and Community Belonging Ratings - by Walking Distance

The datasets providing neighbourhood and community belonging ratings also included detail on respondents access to green spaces. However, only two options were provided to respondents: **less than 10 minutes** to nearest green space; or **more than 10 minutes** to nearest green space. As we have been addressing mostly percentages for respondents living within a 5-minute walk of green space, this unfortunately means we have a degree of inconsistency within the overall analysis. Nevertheless, the relationship between these ratings and 10-minute access is worth exploring:

<br />

![](https://github.com/DSloan10/scottish_household_survey_project/blob/main/presentation_pngs/graph_11_neigh_extra_final.png)

With a majority of respondents in Scotland reporting either "fairly good" or "very good" neighbourhood ratings, I decided to focus only on differences in terms of more or less access amongst these two groups. It seems clear from the above graph that only a negligible difference exists. 

<br />

![](https://github.com/DSloan10/scottish_household_survey_project/blob/main/presentation_pngs/graph_12_comm_extra_final.png)

With reference to the community belonging ratings, once again the majority of people reported positive sentiments in the form of "very strongly" or "fairly strongly" feeling part of their community. The same very small difference seems appartent between those with more or less access to green spaces. With only the ±10-minute measure avaiable, it seems that there is no clear correlation betwen local access and the neigbourhood/community belonging ratings.


##Q3 Extra. NR vs CBR - by Walking Distance








