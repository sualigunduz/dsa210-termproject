## dsa210-termproject

This is my term project for the course, DSA210: Introduction to Data Science, in the 2024-25 Spring term.

# Project Proposal

In this project, I will be exploring some essential factors and their relation to **housing prices**, which will serve as an analog for the general demand of living in a specific place. Among these factors are:

- **Air quality**, crucial in the future of someone's health and quality of life.
- **Unemployment rate**, which determines the chances of a person being able to make a livelihood where they live.
- **Environmental risk**, something increasingly vital in an uncertain future riddled with climate change.

## Motivation

My interest in putting together this project started with considering my life in university, and in the future. Sabancı University's campus in Tuzla, İstanbul, is in close proximity to an **'Organized Industrial Zone'**, an area of land designated by public authorities for industrial facilities. While this type of zoning can help industry work effectively and efficiently, it also brings lots of pollution as a side effect of the waste produced by these facilities.

Students at our university often complain about the quality of the air, bad odors, and trouble breathing as a result of living and studying so close to the pollution. This situation has made me think more carefully about the qualities of where I will want to live and work after I graduate, especially the quality of the air everyone has to breathe. I want to find out whether people have also taken air quality, among other things, into account when buying houses. This led to the idea for this project.

## Plan

My plan is to analyze if and how the main variable of interest, **housing prices** is affected by other environmental and economic variables which are: the **Air Quality Index (AQI)** (an indicator developed by agencies specializing in the environment to make the pollution in the air easily quantifiable and understandable), **environmental risk** (which is also developed by environmental agencies), and the **rate of unemployment** by small administrative units covering a large geographical area: the United States.

### Data to be Used

Currently, I intend to use the following data in the United States of America over a **per-county basis** (counties are the next largest level of administrative unit after the states.):

- **Housing prices**
- **AQI** (an indicator developed by agencies specializing in the environment to make the pollution in the air easily understandable)
- **Unemployment rate**
- **Environmental risk** (presented by environmental and disaster management agencies)

I will combine the relevant data so that every county is an object with the above data assigned to each of them as distinct variables.

### Plans on Collecting Data

I plan to obtain this data through publicly-available online datasets and websites created by companies and organizations specializing in the relevant areas. The organizations and services I intend on collecting this data from are as follows:

1. **Housing**

- **Zillow**: A real-estate marketplace company in the U.S. that shares its meticulous data in various forms, including adjusted housing prices for research. This can be used for housing data. [Datasets are available here.](https://www.zillow.com/research/data/)

- **Redfin**: A real-estate broker firm that also shares similar data. This can also be used for housing data. [Datasets are available here.](https://www.redfin.com/news/data-center/)
  
  Either one of these sources, or both, can be used for housing data.

2. **Air Quality**
- **United States Environmental Protection Agency (EPA)**: Shares AQI recordings on an annual basis for every county (the administrative division one level below the state). This can be used for air quality data. [Datasets are available here.](https://aqs.epa.gov/aqsweb/airdata/download_files.html#Annual)
  
- **IQAir**: A private Swiss air quality technology company that records and shares AQI data globally. This can also be used for air quality data. Datasets are available here. [(1)](https://www.iqair.com/usa) and [(2)](https://www.iqair.com/world-most-polluted-cities?continent=59af928f3e70001c1bd78e4f&country=7KEznm2wS6Zk3chh2&state=&sort=-rank&page=1&perPage=50&cities=)

  Either one of these sources, or both, can be used for housing data.

3. **Unemployment Rate**

- **United States Bureau of Labor Statistics**: A government organization that collects and shares data on the number of employed and unemployed people. This can be used for unemployment rate data. [Datasets are available here.](https://www.bls.gov/cew/downloadable-data-files.htm)

4. **Environmental Risk**

- **United States Federal Emergency Management Agency (FEMA)**: Develops a measure of environmental risk, known as the **Environmental Risk Index**, which is available for each individual county. [Datasets are available here.](https://hazards.fema.gov/nri/data-resources#csvDownload)
   
