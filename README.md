# Increasing Temperatures and Related Health Impacts

## Introduction
Our planet is getting warmer. This summer has [set records](https://www.washingtonpost.com/news/capital-weather-gang/wp/2018/07/03/hot-planet-all-time-heat-records-have-been-set-all-over-the-world-in-last-week/?utm_term=.117468c8c1a6) in the Northern Hemisphere, from [Europe to Japan to North America](https://www.cnn.com/2018/07/23/world/global-heatwaves-climate-change-wxc/index.html),  and it is going to be one of the [hottest summers on record](https://www.cnn.com/2018/07/28/us/2018-global-heat-record-4th-wxc/index.html). Increasing temperatures more frequent and longer heat waves have clear impacts on human health. It is important to understand how temperatures are expected to change and how many people could potentially be at risk so adequate measures can be taken to: raise awareness of the dangers of high temperatures, ensure electric grid reliability to power air conditioners, ensure ample capacity for hospitals and medical facilities to treat patients, etc.

## Project Overview
This project will explore the relationships between heat-related hospitalizations in the United States and a number of heat-related climate variables, including:
- Average High Temperature
- Extreme Heat Events
- Heat Wave Incidents

## Data Sets and Sources
### Heat-Related Hospitalizations
Number of hospitalizations for heat stress per year by state
- Center for Disease Control and Prevention's [National Environmental Public Health Tracking Network](https://ephtracking.cdc.gov/DataExplorer/#/)
- Data are based on the date of admission, which is limited to between May 1 and September 30 for each year. Data represent number of admissions rather than number of individuals (individual can be admitted more than once). Blanks or missing data were either not collected, not provided to the CDC, or were incomplete or did not meet data quality standards.
- Citation: Centers for Disease Control and Prevention. Environmental Public Health Tracking Network. State Hospital Inpatient Discharge data. Accessed From Environmental Public Health Tracking Network: www.cdc.gov/ephtracking. Accessed on 08/18/2018

### Climate Indicators
- [NASA Earth Exchange Global Daily Downscaled Projections (NEX-GDDP)](https://cds.nccs.nasa.gov/nex-gddp/)
- The compressed NEX-GDDP dataset is 12 terabytes -- it's massive. It contains only three elements: daily maximum temperature, daily minimum temperature, and precipitation. The data is quite unweildy and complex to work with (NetCDF format), so there are several initiatives to make it more accessible for climate adaptation and resilience planning. 
    - One is [PREPdata](https://www.prepdata.org/) from the Partnership for Resilience and Preparedness (for which I manage the platform). We provide decadal and 30-year summaries for several climate indicators derived from the processed data. 
    - Another source is the [Azavea Climate API](https://climate.azavea.com/), which provides point-by-point data for 22 climate indicators for 1000+ locations across the U.S. The data is available through queries to the API (though there are rather low rate limits, as I've found)
    
**Using the Climate API**

The API accepts GET, POST, PUT, PATCH, and DELETE HTTP requests. For GET requests that accept parameters, required parameters are specified in the path. Optional parameters are accepted as an HTTP query string parameter:

`https://app.climate.azavea.com/api/climate-data/1/RCP45/indicator/average_high_temperature/?years=2050&units=C`

In the above, the `city` is represented by `1`, the `climate scenario` is `RCP 4.5`, and the `indicator` is `Average High Temperature`. The querystring also contains additional elements, including `years` as `2005` and `units` as `degrees Celsius`. 


**Selected climate indicators**
- **Average High Temperature**: Average High Temperature is calculated by aggregating daily average high temperatures. It is an appropriate metric for probable long term temperature trends.
- **Extreme Heat Events**: Extreme Heat Events counts the total times the daily average maximum temperature is above some percentile of historic observations. The percentile defaults to 99, referring to the hottest percentile of historic daily temperatures. It is an appropriate indicator for understanding deviations from normal climatic extremes. 
- **Heat Wave Incidents**: Heat Wave Incidents counts the days the daily high temperature exceeds 5˚C above historic average high temperature norms for at least 5 consecutive days. This indicator is closely paired with heat wave duration index and, similarly, provides a concrete and palpable metric to the impacts of global warming. Frequency, duration, and intensity predictions of heat waves are very important for health and emergency services planning.
