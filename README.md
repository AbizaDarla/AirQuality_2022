# Project 4
#### Landon, Abiza, Graham, Ed, Adi

Table of Contents:

Landon:
(Note: Due to size constraints the data could not be uploaded into the Github repo. To duplicate my results you may pull from the following websites:
- Data_orginization.ipynb
    - Initial merging of EPA data for the years 2016 through 2021.
    - Analysis on what data is best to keep.
- Merge_EJSCREEN_with_Energy_cost_Data.ipynb
    - Combines EPA data and LEAD data.
    - Performed analysis on data and created visualizations.

Abiza:
- Background_Info.ipynb
    - Exploration of relationships between health, poverty, and pollution 
    - Includes visuals 
- An OLS model predicting rate of ER admissions per 10,00 for cardiovascular disease using score of pollution 

Graham (Emissions Patterns):
- em_statewide_EDA.ipynb:
    - Visualizations of California state-wide emissions
    - Based on (and completes) formatting in em_statewide_formatting.ipynb
- em_county_EDA.ipynb:
    - Visualization tool for select California county-level emissions
    - Based on formatting in em_county_formatting.ipynb

Ed(Weather Insights):
- weather.ipynb:
    - Visualization and EDA on weather data from 1980 to 2022
    - Data source: https://www.visualcrossing.com/weather/weather-data-services
- wildfire.ipynb:
    - Visualization and EDA on wildfire and droughts data
    - Resources: 
        - https://www.fire.ca.gov/incidents/2018/
        - https://github.com/abarbour/FireHistory

Adi (Solar Energy)
- Solar_prod_data_col.ipynb
    - Webscraping of data from CA Dept. of Energy using Selenium
- Solar_prod_eda.ipynb
    - Visualization and analysis of PV and Thermal Solar energy production



## Main Purpose:
This data set is presented to show some of the inequalities concerning energy as measured by variations around pricing and environmental hazards.

## Data Assembly:
This data comes from two sources. The first part comes from the EPA. They have data for each census block across the country and measure various environmental hazards alongside demographic information. They have relevant data for the years 2016 through 2021. The actual data measured varies somewhat from year to year. So when I measured these data, I preserved only the data consistently recorded for each year. The data can be found [here](https://gaftp.epa.gov/EJSCREEN/).

Another dataset I used was the [LEAD tool](https://lead.openei.org/), a dataset about Low-Income Energy Affordability. This dataset has the average annual energy cost for households by Census Tract. A Census Tract includes census blocks, which constitute the rows of the other dataset. A Census block adds one number to the end of the census tract code. So I was able to merge the datasets on this code.

(Note: Due to size constraints, the data could not be uploaded into the Github repo. To duplicate my results, you may pull from the following websites:
EPA data:  Index of /EJSCREEN (epa.gov)
   1. From the 2016 directory pull:  EJSCREEN_Full_V3_USPR_TSDFupdate.csv
   
   2. From the 2017 directory pull: EJSCREEN_2017_USPR_Public.csv
 
   3. From the 2018 directory pull: EJSCREEN_StatePctile_2018.csv
   
   4. From the 2019 directory pull:  EJSCREEN_2019_StatePctiles.csv
   
   5. From the 2020 directory pull:  EJSCREEN_2020_StatePctiles.csv
   
   6. From the 2021 directory pull:  EJSCREEN_2021_StatePctiles.csv

The LEAD data can be pulled from:  LEAD Tool (openei.org)
   1. When  the website loads:
   
   2. Click go
   
   3. Search for California
   
   4. In the map-overlay window click view Census Tracts
   
   5. Download the data, there is an option right below the displayed map.)


## Data Dictionary:
Note: Each feature with an * actually represents 6 features measuring the same thing but for different years. We have data for the year 2021, 2020, 2019, 2018, 2017, and 2016. These descriptions are from the EPAs dictionary [here](https://www.epa.gov/ejscreen/ejscreen-map-descriptions#:~:text=Air%20Toxics%20Respirato,ry%20Hazard%20Index%20Air%20toxics%20respiratory,set%20by%2.%20EPA%20National%20Air%20Toxics%20Assessments).
|Feature|Type|Description|
|---|---|---|
|ID|code|The census block number for the area.|
|Geography ID| code| The census tract number for the area. The same as ID but without the last numeral.|
|Name|string|The name of the census tract the area is a part of.|
|County|code|The county the area is a part of.|
|Tribal Areas|string| The name of the tribe associated with this area and nan if there is no such tribe.|
|Avg. Annual Energy Cost|int| The average yearly cost of energy in the census block area. Measured in Dollars|
|Shape_Area|int| The land area of the Census Block. Measured in miles.|
|Shape_Length|int|The longest length within the Census Block. Measured in miles.|
|ACSTOTPOP_*|float| The total population in the Census Block.|
|CANCER_*|float|A generated value that describes the local cancer risk.|
|DSPLM_*|float| The amount of Diesel Particulate matter in the air, measured in micrograms per cubic meter.|
|LESSHSPCT_*|float| The percent of the population with less than a High-school education.
|LINGISOPCT_*|float| The percentage of the population that is linguistically isolated.
|LOWINCPCT_*|float| Percent of the population with low income.|
|MINORPCT_*|float| Percent of the population that is part of a minority group.|
|OVER64PCT_*|float| The percent of the population over the age of 64.|
|OZONE_*|float| The amount of ozone in the lower atmosphere, measured in parts per billion.|
|PM25_*|float| The amount of atmospheric particulate matter that has a diameter of 2.5 micrometers or less. Measured in micrograms per cubic meter.|
|PNPL_*|float| Gives the relative proximity of superfund sites. These are sites the EPA is commited to decontaminate.|
|PRE1960PCT_*|float| The percent of the housing stock built before 1960.|
|PRMP_*|float| Gives the relative proximity of facilities regestired with the risk management peogram. These facilities are required to have an action plan if public becomes endangered by chemicals or volitale compounds they store.|
|PTRAF_*|float| Gives the relative amount of traffic in the area. Measured in daily vehicles per meter.|
|PTSDF_*|float| Gives the relative amount of local waste water discharge. Measured in facilities per kilometer.|
|PWDIS_*|float| Provides the relative amount of local hazardous waste. Measured in toxicity-weighted concentration per meter.|
|RESP_*|float| Air toxics respiratory hazard index (the sum of hazard indices for those air toxics with reference concentrations based on respiratory endpoints, where each hazard index is the ratio of exposure concentration in the air to the health-based reference concentration set by the EPA). (Direct quotation from the above [website](https://www.epa.gov/ejscreen/ejscreen-map-descriptions#:~:text=Air%20Toxics%20Respiratory%20Hazard%20Index%20Air%20toxics%20respiratory,set%20by%20EPA%29.%20EPA%20National%20Air%20Toxics%20Assessments).)
|UNDER5PCT_*|float| The percentage of the population under the age of 5.|

## Data Visualizations and Conclusions:
I visualized the data by grouping according to county. I found that counties with more poverty did not have cheaper energy available. It cost at least $2000 dollars annual. Many of the more prosporous counties had cheaper costs. Ozone pollution was also corralted to higher energy costs, demonstrating that more expensive energy was related to worse environmental hazards.

## Future Work:
Fundamentally this data shows that there are injustices related to energy pricing. However, there are many confounding variables when looking at data like this. This includes population, the extent the location is rural, and how low income communities are geographically distributed. I would like to perform more work to untangle these variables. This future work may include finding more data to link these data to where energy is produced and the local energy mix consumed.



