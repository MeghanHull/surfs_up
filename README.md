# Surfs Up Analysis
## Project Overview
<!-- W. Avy likes your analysis, but he wants more information about temperature trends before opening the surf shop. Specifically, he wants temperature data for the months of June and December in Oahu, in order to determine if the surf and ice cream shop business is sustainable year-round. -->
As a supplement to the business plan for *Surf n' Shake*, the potential investor W. Avy has requested an analysis of weather for Oahu, Hawaii.  Specifically, analysis of temperature data for the months of June and December was requested, to gauge if the surf and ice cream shop business is sustainable year-round

## Purpose
<!-- The purpose of the analysis is well defined. (3 pt) -->
Analyze the temperature trends for the months of June and December in Oahu, in order to evaluate the year-round sustainability of a surf and ice cream shop business.

## Resources
### Data Sources
1. [hawaii.sqlite](hawaii.sqlite)

### Software
***Table 1: Software Versions***
| Software | Version |
| :--- | :---: |
| Python | 3.7 |
| Conda | 4.13.0 |
| Jupyter Notebook | 6.4.8 |
| Pandas | 1.4.2 |
| SQLite | 3.38.5 |
| SQLAlchemy | 1.4.32 |
| NumPy | 1.21.5 |

# Results
<!-- There is a bulleted list that addresses the three key differences in weather between June and December. (6 pt) -->
Analysis of the temperature data for the months of June and December in Oahu shows:

***Table 2: Observed Temperatures for Oahu, Hawaii***
| Statistic | June | December |
| :--- | :---: | :---: |
| **Count** | 1700 | 1517 |
| **Mean** | 74.944118 | 71.041529 |
| **STD** | 3.257417 | 3.745920 |
| **Minimum** | 64.00 | 56.00 |
| **25% Qtr** | 73.00 | 69.00 |
| **50% Qtr** | 75.00 | 71.00 |
| **75% Qtr** | 77.00 | 74.00 |
| **Maximum** | 85.00 | 83.00 |

<sup>**Note:** Statistics generated using [SurfsUp_Challenge.ipynb](SurfsUp_Challenge.ipynb) </sup>

The key differences in the weather between June and December are:
- The average temperature for June is approximately 5 degrees warmer than December.
- The quartiles are 3-4 degrees higher for June than December.
- The extremes show more variation; the minimum for June is 8 degrees higher, while the maximum for June is only 2 degrees higher.

# Summary
<!-- There is a high-level summary of the results and there are two additional queries to perform to gather more weather data for June and December. (5 pt) -->
The temperatures in December are slightly lower than June, but should still be suitable for a surf and ice cream shop business for the majority of the time.  

In addition to the temperature analysis, further weather data analysis is recommended to assess year-round sustainability with respect to precipition.  In particular, the following queries should be analyzed:
- Total precipitation levels
  ```
  session.query(Measurement.date, Measurement.prcp).filter(extract('month', Measurement.date) == 6).all()
  session.query(Measurement.date, Measurement.prcp).filter(extract('month', Measurement.date) == 12).all()
  ```
- Amount of precipitation at the most active station, USC00519281 (found during a previous analysis)
  ```
  session.query(Measurement.prcp).filter(Measurement.station == 'USC00519281').filter(extract('month', Measurement.date) == 6).all()
  session.query(Measurement.prcp).filter(Measurement.station == 'USC00519281').filter(extract('month', Measurement.date) == 12).all()
  ```
