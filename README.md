# CATCH
Crime Analysis over Time in the City of Houston (CATCH)

## Motivation
On 11/05/19, the city of Houston residents mobilized to the polls to vote on the city's next Mayor. The race's front-runners, incumbent Mayor Sylvester Turner and challenger Tony Buzbee, have engaged in debate over a range of topics, with Houston's crime rate prominent among them. Buzbee, in particular, has made crime a focal point of his campaign. The move has certainly not hurt his chances, as the two are now headed into a runoff election to conclude the race.

<p align="center">
  <img src="https://www.dailyinterlake.com/apps/pbcsi.dll/storyimage/DI/20191105/AP/311059900/AR/0/AR-311059900.jpg" width="300" height="219">
  <sub><i><br>Incumbent Houston Mayor Sylvester Turner (right) and attorney Tony Buzbee on September 2, 2019 at a Houston, TX<br> mayoral candidate forum. (Karen Warren/Houston Chronicle via AP)</i></sub>
</p>

Local Houston, Texas news sources have taken up the task of reporting 2018 FBI crime statistics that were released in January of 2019.
A [crimereport.org article](https://thecrimereport.org/2019/10/10/houston-murders-up-crime-a-mayors-race-issue/) clarifies that there is nuance to the reported numbers. Although violent crime went up by 6%, nonviolent crime dropped 9% in the same period. The overall rate of crime fell a total of 6%. Under accusations of using fear-mongering tactics following a Houston Chronicle fact-check, Buzbee doubled down.

> “I reject the notion that crime is down in this city.”  
> “We need police officers and I'm going to put more police officers on the street.”

Adding to the confusion of voters are various articles surfacing during election season such as ["Texas colleges with the most violent crime in 2018, according to the FBI"](https://www.chron.com/neighborhood/article/Texas-colleges-violent-crimes-2018-FBI-14535987.php) and ["New FBI data shows the Houston-area suburbs with the most property crimes in 2018"](https://www.chron.com/neighborhood/article/FBI-data-Houston-cities-property-crimes-2018-14501393.php). Such headlines have even spurred backlash from [Rice University's Thresher Editorial Board](https://www.ricethresher.org/article/2019/10/take-pride-in-houston), citing ignorance to the methods of disproportionate policing that can result in poor communities being labeled "dangerous", as well as the city's diversity of cultures. All of this still doesn't account for potential underlying issues with the reporting changes. The FBI publishes official crime data compiled by the Uniform Crime Reporting (UCR) program. UCR, having previously used the Summary Reporting System (SRS) format, is undergoing a transition through the year 2021 solely to a new format known as National Incident Based Reporting System (NIBRS). On [their website](https://www.houstontx.gov/police/cs/Monthly_Crime_Data_by_Street_and_Police_Beat.htm), the Houston police department annotates their data with the following:

>PLEASE NOTE: In accordance with the national shift in crime data collection and reporting methods, the Houston Police Department has just completed transitioning from UCR to NIBRS. While transitioning to the new method can be somewhat costly, and—because of the greater level of reporting specificity in NIBRS—it can initially appear that an agency has higher levels of crime after switching to NIBRS, the new system will provide more useful statistics, promoting constructive discussion, measured planning, and informed policing.

<p align="center">
  <img src="https://www.fbi.gov/image-repository/nibrs-logo-1.jpg/@@images/image/high" width="500" height="179">
  <sub><i><br>NIBRS Banner</i></sub>
</p>

Basically, the numbers may appear to signal an increase in crime as an artefact of the transition, rather than a matter of fact. Details on how the switch affects numbers can be found [here](https://ucr.fbi.gov/nibrs/2014/resource-pages/effects_of_nibrs_on_crime_statistics_final.pdf). For the sake of context, some informative statements in the report are as follows:

>According to the Hierarchy Rule[...]If, for example, a murder and rape occur within the same incident, only the murder is counted in
the SRS. Further, if an aggravated assault occurs in the same incident as a burglary, the burglary is not counted. 
>
>As previously discussed, the apparent increase is simply due to the difference between how crimes are counted in NIBRS versus the SRS and its application of the Hierarchy Rule. Further, none of the increases amount to a change greater than 2.7 percent.
>
>Reporting NIBRS data does not actually increase crime within jurisdictions, even though there is
a slight, but visible, effect on crime rates.
>
>When this change is eventually made, a similar 2.1 percent increase in the number of reported crimes should be expected for agencies transitioning from SRS to NIBRS data. 

While the FBI reported numbers are available, I have not been able to find any efforts to independently reproduce the FBI numbers, or demonstrate changes in crime over this period of time in a digestible fashion. Also, as a former Houstonian myself, I am aware of the concern for the crime rate within the city. Mayor Turner assumed his position in 2016. His predecessor, Annise Parker, held the title from 2010-2016. I intend to gather the available crime data for the city from 2009 until as recent as possible into 2019. With this data, I will look to not only see if the most recent numbers bear out, but attempt to track the rate of crime change with respect to reported city populations in a time series. Also, in regards to the position that more police officers is the solution, I will seek to chart police officer employment over the same time period. The hope is to uncover the trends of crime rate, population, and staffing of police officers from 2009 through 2019. The goal will be to bring an independent investigation into the conversation and visualize relevant trends in order to help contextualize the issue of crime in the city of Houston.


## Data

Unless stated otherwise, the data to be used for this analysis is made available for use under the U.S. Public Domain under the category of U.S. Government Works, found at [https://www.usa.gov/government-works](https://www.usa.gov/government-works).

### Crime Data

**[2019 Houston Crime Data](https://www.houstontx.gov/police/cs/xls/NIBRSPublicView.Jan1-Sep30-FINAL.xlsx)**  
**[2009-2018 Houston Crime Data](https://www.houstontx.gov/police/cs/crime-stats-archives.htm)**  
**[Future-proof Link for All Houston Crime Data](https://www.houstontx.gov/police/cs/Monthly_Crime_Data_by_Street_and_Police_Beat.htm)**
**[Data Dictionary as of 5/9/19](https://www.houstontx.gov/police/cs/NIBRS_Public_Data_Dictionary_050919.pdf)**

| Variable | Data Type | Description |
| :--- | :---: | :--- |
| Occurrence Date | Date | Date offense occurred. If the offense date is unknown or occurred within a date range, this variable represents the earliest date. |
| Occurrence Hour | Time | Hour offense occurred. [Military Time] |
| NIBRS | Description | Text Offense type. https://ucr.fbi.gov/nibrs/2011/resources/nibrs-offense-codes/view |
| Offense Count | Number | Number of offenses committed. Quantified by NIBRS rules. |
| Beat | Text | Beat where the offense occurred. https://www.houstontx.gov/police/pdfs/hpd_beat_map.pdf |
| Premise | Text | Type of location where the offense occurred. |
| Block Range | Number | Hundred block for address where offense occurred. |
| Street Name | Text | Street name where offense occurred. |
| Street Type | Text | Identifiers of street names. {e.g. R=Road, ST=Street, DR=Drive, AVE-Avenue} |
| Suffix [Streets] | Text | Directional identifiers for streets. {e.g., E=East, W=West, S=South, N=North} |

The data is the Houston police department published data under the NIBRS format. It will be the dataset of choice since it is the same official source reported for use by the FBI. As can be gathered from the data dictionary above, the data contains detailed information regarding crimes commited in the city. Information pertaining to time and location will not be used and there will be no effort to tie the data to any officer beats, criminal records, or any other data sources that may implicate groups or individuals. This will help to minimize ethical concerns with the data that will be processed.

### Population Data

**[Houston Population Estimates [2010-2018]](https://factfinder.census.gov/faces/tableservices/jsf/pages/productview.xhtml?src=bkmk)**  
**[Houston Population Estimates [2010-2018] Alternate Source](http://worldpopulationreview.com/us-cities/houston-population/)**  
**[Source of 2009 Houston Population Estimate](https://www.google.com/publicdata/explore?ds=kf7tgg1uo9ude_&ctype=l&strail=false&bcs=d&nselm=h&met_y=population&scale_y=lin&ind_y=false&rdim=country&idim=place:4835000:4819000&ifdim=country&hl=en&dl=en&ind=false)**

The population data was retrieved using the U.S. Censu Bureau's factfinder tool. I opted to use this data because the U.S. Census Bureau is the official and most trusted source for population-based data. This information will be used to contextualize crime statistics by year. As these are the most reliable available estimates, there are minimal concerns of ethical problems with using this data.

There are some future concerns with the population data and one concern with the data to be used. The factfinder tool is being phased out and most (potentially not all) data is being moved to [data.census.gov](data.census.gov). However, I was unable to locate the desired information on the new website. As I am not currently able to determine if the data will appear there, I listed an alternative source for the same data for retrieveal purposes only. It is not the source from which analysis is being done. Information regarding the transition can be found [here](https://www.census.gov/data/academy/webinars/2019/transition-data-census.html).

The other issue pertains to the population estimate for the year 2009. Since I could not locate an official estimate, I opted to use numbers provided via Google, which rounds out to 2,118,600. Should an U.S. Census Bureau estimate be located at some other time, it is recommended to those looking to replicate this work to use that number instead.

### Police Employment Data

**[Houston Police Employment Records](https://www.houstontx.gov/police/department_reports/department_reports_archives.htm)**  
**[Secondary Source for Houston Police Employment Data](https://www.governing.com/gov-data/safety-justice/police-officers-employment-data-by-city-department.html)**

The Houston government website has a publicly available archive of monthly operational summaries starting in 2012. For the purposes of this analysis, useful information contained within these reports is the number of paid employees, officer and citizen, as well as population estimates and officer-population ratio statistics. As these appear to be the reports delivered to UCR, they are fit for use in the analysis. The count of police officers will help to contextualize the yearly crime statistics to determine if there is a correlation with either crime or population size. 

It is imporant to note that the UCR database is frozen each fall to generate its reports for two reasons. First, there are gaps for numerous months of each year in the police employment data. Second, the annual numbers reported for police department employment appear to lineup with final numbers for October. Therefore, employment numbers used for each year will be selected for months available closest to October.

Since the data here is recorded for federal government reporting purposes and is being interpreted in this analysis for that specific data, the ethical ambiguity for using this data is minimized.

The secondary data source cites UCR reported data as its source, but also displays employment numbers for years not available in the primary source (2009-2011). A few sampled years match the data recorded in the primary source's reports, which will alleviate some doubt for years where the secondary source is the only resource.

## Dependencies

The availability of data sources is a primary concern with this project. The UCR and US Census Bureau are both undergoing transitions, which may put some APIs in flux. Also, while much of the data has been located, it is not guaranteed that all sources will be uniform in their structure. This could impact the data collection, cleaning, processing, and interpretation steps of the analysis. In the event some of the aforementioned issue arise, backup plans are in place for some of these scenarios.

## Sources
* https://www.fbi.gov/services/cjis/ucr/nibrs (accessed 11/6/2019)
* https://www.houstonpublicmedia.org/articles/news/politics/2019/11/06/350955/incumbent-mayor-sylvester-turner-challenger-tony-buzbee-head-to-runoff/ (accessed 11/6/2019)
* https://thecrimereport.org/2019/10/10/houston-murders-up-crime-a-mayors-race-issue/ (accessed 11/6/2019)
* https://www.houstonchronicle.com/news/houston-texas/houston/article/Houston-mayoral-foes-debate-city-finances-14501858.php (accessed 11/6/2019)
* https://ucr.fbi.gov/crime-in-the-u.s/2018/crime-in-the-u.s.-2018/topic-pages/tables/table-6 (accessed 11/6/2019)
* https://www.ucrdatatool.gov/faq.cfm (accessed 11/7/2019)
