# CATCH
Crime Analysis over Time in the City of Houston (CATCH)

## Motivation
On 11/05/19, the city of Houston residents mobilized to the polls to vote on the city's next Mayor. The race's front-runners, incumbent Mayor Sylvester Turner and challenger Tony Buzbee, have engaged in debate over a range of topics, with Houston's crime rate prominent among them. Buzbee, in particular, has made crime a focal point of his campaign. The move has certainly not hurt his chances, as the two are now headed into a runoff election to conclude the race.

<p align="center">
  <img src="https://raw.githubusercontent.com/adrianmt18/CATCH/master/turner-buzbee.jpg" width="300" height="219">
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


## Research Questions

This analysis will attempt to answer five specific questions. 

**RQ1.** To date, has the overall crime rate in Houston, TX increased or decreased since Mayor Turner's appointment in 2016?  
**RQ2.** To date, has the violent crime rate in Houston, TX increased or decreased since Mayor Turner's appointment in 2016?  
**RQ3.** Has the trend in overall crime rate in Houston, TX inverted during Mayor Turner's tenure?  
**RQ4.** Has the trend in violent crime rate in Houston, TX inverted during Mayor Turner's tenure?  
**RQ5.** Have fluctuations in police officer to population ratios correlated with violent crime rate trends?

It is important to note that the FBI's UCR definition of violent crime will be applied, which includes the four specific offenses listed below.

| UCR Offense Code | Offense Description | Crime Against |
| :---: | :--- | :--- |
| 13A | Aggravated Assault | Person |
| 11A | Forcible Rape | Person |
| 09A | Murder & Nonnegligent Manslaughter | Person |
| 120 | Robbery | Property |

No coverage of the mayoral race to date has cited any observation that more police has historically induced reduced crime in the city. Buzbee is on record stating that crime is up and that more police officers will address that issue, thereby making the city safer. I interpret that logic would imply an assumption that the officer:population ratio has dropped below some threshold. I intend to let the reported numbers make a case here.


## Related Work

Published independent research into crime and policing within Houston is sparse. UCR reported numbers are the deferred-to source in most reporting, outside of where city officials provide statements on the record. A [2018 article](https://www.chron.com/houston/article/Houston-police-unveil-March-on-Crime-with-policy-12624886.php) cited Mayor Turner saying "I think we can all agree that HPD is understaffed," during a press conference. The same article mentions that Houston's 5100 officers is 300 more than the city had a decade prior.

An [article by Samantha Ketterer of the Houston Chronicle](https://www.chron.com/news/houston-texas/houston/article/Houston-police-to-announce-2018-crime-rate-13566844.php) published in late January of 2019 goes on to make similar claims to the FBI report to conclude that crime had dropped in the city. 

>Violent crime decreased in Houston by about 10.4 percent last year despite a slight increase in homicides, police said.
>
>The reduction marks a continuing downward movement of murders, rapes, robberies and aggravated assaults over the past five years.
>
>Acevedo also touted double digit decreases in robberies and aggravated assaults in 2018, as well as reductions in nonviolent crimes, although to less drastic extents. Burglaries, thefts and auto thefts declined by a combined 2.8 percent from 2017 to 2018.

Police Chief Art Acevedo was also quoted as saying “We might not get them all, but I promise in the long-term, we’re trending in the right direction.” Later statements in the piece would also imply a shortage of officers.

Of the research freely available on this subject, a [2001 paper by Anthony A. Braga Ph.D.](https://www.jstor.org/stable/1049870) reviewed hot spot policing methods used in various parts of the U.S. The paper references a quasi-experiment<sup>1</sup> in Houston where the hot spots were defined as the seven highest crime beats. A summary of that quasi-experiment can be found at [https://cebcp.org/evidence-based-policing/the-matrix/neighborhood/neighborhood-caeti-1999/](https://cebcp.org/evidence-based-policing/the-matrix/neighborhood/neighborhood-caeti-1999/). Braga advises a cautionary interpretation of the Houston Targeted Beat Program results as, for one reason, "the analyses did not directly measure whether observed changes in treatment beats were significantly different from observed changes in control beats." Simplifying the caveats, success in reducing index crimes was observed using high-visibility patrol treatments, while mixed results were observed using zero-tolerance policing treatments. The paper offered the following overall interpretation of the results:

>Nevertheless, the results of this study can be broadly taken to support the position that focused police enforcement efforts can be effective in reducing crime at hot spots.  

To summarize this section, a nearly 20-year-old assessment found certain policing strategies effective for crime reduction, though it is not affirmed if said strategies require more officers to implement than traditional strategies. It implies that more targeted use of officer hours was applied to high-crime areas. Statements from city officials have cited a shortage of officers, yet claim crime has overall been decreasing for atleast 5 to 6 years. This evidence would lead me to expect to see crime rates dropping while officer:population ratios do not increase, all while overall officer employment increases.

## Data

Unless stated otherwise, the data to be used for this analysis is made available for use under the U.S. Public Domain under the category of U.S. Government Works, found at [https://www.usa.gov/government-works](https://www.usa.gov/government-works).

### Crime Data

**[Houston Crime Data](https://www.houstontx.gov/police/cs/Monthly_Crime_Data_by_Street_and_Police_Beat.htm)**  
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

The population data was retrieved using the U.S. Censu Bureau's factfinder tool. I opted to use this data because the U.S. Census Bureau is the official and most trusted source for population-based data. This information will be used to contextualize crime statistics by year. As these are the most reliable available estimates, there are minimal concerns of ethical problems with using this data. Information on the data source follows.

>Annual Estimates of the Resident Population: April 1, 2010 to July 1, 2018  
>Source: U.S. Census Bureau, Population Division  
>Note:  
>The estimates are based on the 2010 Census and reflect changes to the April 1, 2010 population due to the Count Question Resolution program and geographic program revisions. See Geographic Terms and Definitions at http://www.census.gov/programs-surveys/popest/guidance-geographies/terms-and-definitions.html for a list of the states that are included in each region and division.

More details on the data source can be found in the text document under the population data folder in this repository.

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


## Methodology

The population data will amount to 10 integers retrieved from the U.S. Census Buerau. The details and challenges around gathering this data are covered in the relevant section above. Likewise, the specific challenges around the gathering the police employment data are present in the relevant section above. The data will be recorded manually.

The crime data are archived by month in publically accessible excel files. Each of these monthly files will be aggregated by year and only a limited amount of information will be extracted for analysis. The only fields intended for use are the Offense Type, the year and month portion of the date, and the count of offenses per occurence.

The analysis strategy is to take place over phases. The first phase will process each month of each year individually by grouping all crimes by their type, and their counts will be summed. Each crime will also be given a binary indicator as either violent or non-violent. From here, all crimes will again be aggregated by their violent-indicator in a second phase. Violent crime will be assessed as an independent group from another group that considers overall crime. Once, for instance, all of the numbers for 2018 are aggregated, the month column will be discarded. In the final phase, the resulting 10 data points for violent crime and the 10 for overall crime will be plotted over a time series by their year. Since the research questions center around crime trends over time, a time series is the ideal approach to communicate the findings. 

The manually recorded population and police employment numbers will also be presented as annual numbers. Each will be shown in individual trends, but an additional measure will combine the two into a ratio. The ratio will be presented as the number of employed officers over every 1,000 citizens. For example, 2,000 officers for a population of 1,500,000 people will be recorded as 1.33. The math follows:

>2000/(1500000/1000) = 2000/1500 = 1.33

This ratio aligns with how the Houston Police Department records their ratio and also provide a single number to track over time. Hopefully, this will make the information simpler to digest.


## Sources & References
* https://www.fbi.gov/services/cjis/ucr/nibrs (accessed 11/6/2019)
* https://www.houstonpublicmedia.org/articles/news/politics/2019/11/06/350955/incumbent-mayor-sylvester-turner-challenger-tony-buzbee-head-to-runoff/ (accessed 11/6/2019)
* https://thecrimereport.org/2019/10/10/houston-murders-up-crime-a-mayors-race-issue/ (accessed 11/6/2019)
* https://www.houstonchronicle.com/news/houston-texas/houston/article/Houston-mayoral-foes-debate-city-finances-14501858.php (accessed 11/6/2019)
* https://ucr.fbi.gov/crime-in-the-u.s/2018/crime-in-the-u.s.-2018/topic-pages/tables/table-6 (accessed 11/6/2019)
* https://www.ucrdatatool.gov/faq.cfm (accessed 11/7/2019)
* https://en.wikipedia.org/wiki/Crime_in_the_United_States (accessed 11/15/2019)

[1] Caeti, T. J. (1999). Houston’s targeted beat program: A quasi-experimental test of police patrol strategies (Doctoral dissertation, Sam Houston State University)
