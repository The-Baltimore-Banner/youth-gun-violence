# 2023 Youth Gun Violence
================
 - [Overview](#overview)
 - [Data](#data)
 - [Methodology](#method)
 - [Limitations](#limitations)
 - [License](#license)

## Overview

High-school-age teens in Baltimore continue to be shot in record numbers this year, even as overall, nonfatal shootings and homicides are down, according to an analysis by The Baltimore Banner.

Last year was a record year for children being shot in Baltimore, a disturbing trend first reported by the Banner in September. That year ended with 84 juvenile shooting victims. But since then, the situation has gotten worse.

January had the most high shcool-aged teenage victims of gun violence of any month since 2015, the first year with reliable publicly available data. The two most violent weeks since 2015 occurred this year: the first week of January and the second week of February. The increase in youth victims of gun violence reflects a national trend, but the problem is especially acute in Baltimore.

School zones have become a dangerous place for Baltimore’s youth. Twenty-three school-age children and young adults, ages 13 to 18, have been shot near a Baltimore City school during the school day this academic year. Winter has been especially violent. More than half of all of the victims were shot since the winter break.

The Banner had initially focused its analysis on people 17 and under, but further analysis made clear the central role schools are playing in the increase in violence. Nearly 1 in 4 juvenile gunshot victims were shot near a school this academic year, and 18-year-olds were shot near schools at similar rates as 17-year-olds. Very few children 12 and under are shot in Baltimore, and the rate is actually down significantly since 2015.

Read the story: [Nearly one in three people shot in 2023 were 18 or under as gun violence flares near schools](www.thebaltimorebanner.com/article/teenage-shootings-gun-violence-UFHVSE7HWVDGPB6YEFXLN4HQPQ/).

<a id="data"></a>
## Data

### More high school-aged teens, 13 to 18, have been shot in the first 7 weeks of 2023 than any prior year over the same period
age_range | 2015 | 2016 | 2017 | 2018 | 2019 | 2020 | 2021 | 2022 | 2023
--- | --- | --- | --- | --- | --- | --- | --- | --- | ---
high school teen | 8 | 6 | 14 | 6 | 7 | 5 | 6 | 20 | 29
19 and older| 58 | 65 | 126 | 71 | 88 | 108 | 97 | 113 | 71
child | 1 | 1 | 0 | 0 | 1 | 0 | 0 | 0 | 1

### More high school-aged teens, 13 to 18, have been shot this school year than in any other since 2015
age_range | 2015/2016  | 2016/2017 | 2017/2018 | 2018/2019 | 2019/2020 | 2020/2021 | 2021/2022 | 2022/2023
--- | --- | --- | --- | --- | --- | --- | --- | --- | ---
high school teen | 79 | 82 | 71 | 73 | 99 | 87 | 95 | 122
19 and older | 846 | 916 | 866 | 891 | 991 | 918 | 954 | 834
child | 10 | 6 | 3 | 5 | 5 | 2 | 4 | 2


Where to get the data you need:

Put CSV in the data folder:
[Baltimore Police Part 1 Crimes Database](https://data.baltimorecity.gov/datasets/part-1-crime-data-/explore)

Put shapefile in shapefiles folder:
[Baltimore Neighborhoods](https://data.baltimorecity.gov/datasets/neighborhood-1/explore?location=39.284818%2C-76.620500%2C11.86)
[Baltimore Real Properting Information](https://data.baltimorecity.gov/datasets/real-property-information-2/explore)

<a id="method"></a>

## Methodology
### How we analyzed BPD violent crime data

This analysis of Open Baltimore Part 1 crime victims database defines shooting victims differently than the Baltimore Police Department. The database defines shooting victims as someone who was shot but was not killed. This analysis includes both those shooting victims and homicide victims who were killed with a firearm. It relies on a version of the Part 1 Crimes Database generated on Feb. 22, 2023. Subsequent versions may return slightly different results because crimes are sometimes reclassified by BPD.

This analysis spatially joins school address latitude and longitude coordinates to real property polygons in order to determine the location of school property parcels.

One hundred and thirty-five school parcels were included in this analysis, although there are more than 135 schools in the city. In some cases, multiple schools were located at a single parcel, causing duplicate geometries. In these situations, one unique record for the parcel was kept by distincting on the address in the real property data, and a column indicating how many high schools were located at the parcel was created by grouping and counting these duplicate addresses.

We removed five high schools from our analysis, including virtual schools, vocational “P-Tech” schools and schools that serve juveniles that are incarcerated.

We include incidents that occurred between 7 am and 7 pm, reasoning that students might still be at school or at after school programs during the hours between 3 and 7 pm, even when school has officially ended. We include 18 year old victims in our definition of juvenile, because some 18 year olds are still in high school.

Academic years are defined in two different ways as part of this analysis. When comparing shootings near schools, we estimated academic years to be between Sept. 1 and June 15 in an attempt to identify shootings that happened while school was in session. When counting shootings anywhere in the city, we defined the school year as June 16 to June 15.

When counting shootings within an X number of blocks of a shapefile, we counted 100 meters for each block in addition to 50 meters for the immediate street. In some parts of the city, this may not a literal block.

While reviewing this analysis, it is important to focus on the difference between the number of crimes and the number of victims. The data includes one row for every victim of a Part 1 crime. To get distinct crimes, we grouped them by time and location. In some cases, a shooting event led to multiple victims, some who were homicide victims and others who were shooting victims. Our analysis counts this as one shooting crime, but multiple shooting victims.

High school-aged teens are ages 13 to 18. Eighteen-year-olds were included in an initial analysis of juvenile gunshot victims after further analysis made clear the central role schools are playing in the increase in violence. Nearly 1 in 4 juvenile gunshot victims were shot near a school this academic year, and 18-year-olds were shot near schools at similar rates as 17-year-olds. Very few children 12 and under are shot in Baltimore, and the rate is actually down significantly since 2015.

a id="limitations"></a>

## Limitations
### Missing entries and errors we overcame to tell this story

There are known errors in the public Part 1 Crimes Database. The database is also frequently changing. Crimes that were once classified as homicides are often reclassified, making it difficult to recreate mid-year BPD reports at the end of the year. A slight variation is to be expected.

Not every year in the database is reliable. In response to previous questions from The Banner, BPD admitted that shooting data before 2014 should not be relied on. They have never said why. Further analysis has led The Banner to question data in 2014 as well, leaving only the last seven years for analysis.

The geocoded coordinates may not be exact locations. Some shootings may have literally taken place just inside or just outside the ranges where The Banner looked, but have locations in the data that included or excluded them in error.

Some entries in the Part 1 Crimes data list impossible ages such as negative numbers or very large numbers. The error is less common in shootings and homicides. There are 52 shooting victims who do not have an age listed or have a negative age. About half of these errors are from years before 2017. The number of ageless victims went up in 2022. There were six recorded ageless victims this year, making up 12% of all ageless victims. All ages that were lower than 0 or higher than 100 were mutated to “NA” to reduce the impact of incorrect ages skewing the mean values of victims per crime.

<a id="license"></a>

## License

Copyright 2023, The Venetoulis Institute for Local Journalism

Redistribution and use in source and binary forms, with or without modification, are permitted provided that the following conditions are met:

1. Redistributions of source code must retain the above copyright notice, this list of conditions and the following disclaimer.

2. Redistributions in binary form must reproduce the above copyright notice, this list of conditions and the following disclaimer in the documentation and/or other materials provided with the distribution.

3. Neither the name of the copyright holder nor the names of its contributors may be used to endorse or promote products derived from this software without specific prior written permission.

THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS "AS IS" AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT HOLDER OR CONTRIBUTORS BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.
