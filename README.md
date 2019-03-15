# Project 1: Driving Licenses & Traffic Accidents Analysis

## Problem Statment

We would like to determine a way to reduce accidents on Saudi roads, our research will focus on two main points relating to this:
- whether there is a relationship between number of licenses issued and no. of accidents, and if we can utilize licenses as a predictor of accidents. If so, study causality, if any, and what actions can be taken in relation to license issuance to lower accidents
- study whether the new traffic fines imposed at the end of 2016 had an effect on accidents in 2017, and whether increasing fines is a viable tactic for accident reduction

## Executive Summary

We analyzed two datasets, one related to accident and casualty numbers per region of KSA in 2016-2017, the other with numbers on licenses issued per region, both found on KAPSARC's website. Our goal was to determine whether the number of licenses issued and the number of accidents had any relationship, and whether the new traffic fines introduced at the end of 2016 had any tangible effect on the number of accidents in 2017.

We noticed the distribution of both accidents and licenses were highly skewed when taken as absolute numbers per region thanks to the huge disparity in population between the three largest regions (Riyadh, Makkah and Eastern Province) and the other 10 regions of the Kingdom. To adjust for this, we sourced data from the stats.gov.sa portal on population per region in the target years, and adjusted the accident and license issuance numbers to be per thousand capita of elligible drivers (males over 15 years of age).

After this adjustment, we compared the license issuances to accidents to see if there was any correlation between them. The resulting scatter plot and pearson's r (-0.0083) indicated that there was no relationship and that license issuances would be a poor predictor of # of accidents on Saudi roads.

For our second task, we compared the total number of accidents in 2016 and 2017 and noticed a 14% drop year-over-year (530k in 2016 vs 460k in 2017). This looked promising for the traffic fines, and when comparing the mean accidents per thousand capita, the drop was even larger at 17%. To test whether this was purely by chance we hypothisized that there was no actual mean difference between the two years, and tested for this with a significance level of .05. Using the T-score produced a p-value of .37, due to the small sample size we decided to test also using the bootstrap method which also yielded a higher p-value than .05. Therefore we were unable to reject our hypothesis, and concluded that this difference between years was not statistically significant.

Our analysis was unable to produce any evidence that the new traffic fines had any effect on the number of accidents on the road the year after implementation, further research needs to be done to test its efficacy in reducing traffic accidents.

## Data Dictionary

|Feature|Type|Dataset|Description|
|---|---|---|---|
|**year**|*int*|Driving_Licenses/Traffic_Accidents|The year in which the observation happened, only 2 years in the accidents df, 25 years in the licenses| 
|**region**|*category*|Driving_Licenses/Traffic_Accidents|The administrative region in which the observation was conducted, 13 regions in KSA + country 'Total'| 
|**indicator**|*object*|Traffic_Accidents|The variable being measured in the observation, measures relating to accident and casualty numbers| 
|**value**|*int*|Traffic_Accidents|The integer value associated with the adjacent indicator|
|**driving_licenses**|*int*|Driving_Licenses|The number of driving licenses issued in each region category by year|
|**geo_point_2d**|*object*|Driving_Licenses/Traffic_Accidents|Representation of latitude and longitude of the geolocation of the region| 
|**geo_point_lat**|*object*|Traffic_Accidents|Represents latitude of regions geolocation| 
|**geo_point_long**|*object*|Traffic_Accidents|Represents longitude of regions geolocation| 

## Conclusions / Recommendations

- Licenses issued is not a good predictor for the number of accidents, as we saw no correlation after adjusting for population
- We were unable to see a statistically significant decrease in mean accidents across regions between 2016 and 2017
- Further research needs to be done to test the effect of the new traffic fines on accidents, if any