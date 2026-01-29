## Data processing, calibration, and analysis for dispersed PurpleAir datasets ##
This folder contains multiple Python Jupyter Notebooks for processing, calibrating and analyzing different style of PurpleAir datasets. Datasets downloaded from SD cards 
and from the Purple Air website, as well as older datasets, have different formats to deal with. In this folder there are the following two Notebooks:
1. PupleAir_datainput&calibration.ipynb
   --> This Notebook allows input of various sources of Purple Air data and exports one csv file with all data [or two, if using an external file or if files are too large for processing]
   --> Within this code, there are sections for data quality thresholds for temperature, humidity, and percent and absolute error between PA channels A and B as well as a dictionary for renaming all disparate site
       names to a standardized list
   --> Datasets are then combined and standardized with only priority columns and contain standarized column names and timestamps
   --> Data is then filtered by quality thresholds and calibrated using calibrations from Barkjohn et al. (2022) including US EPA calibration, quadratic calibration and transitional calibration. The best calibration is
       selected based on raw PM2.5 values (see Barkjohn et al. 2022) and applied to column "PM2_5_corrected", which is the column used throughout the rest of the analysis
   --> Data is saved as a master csv file
2. PurpleAir_dataplotting.ipynb
   --> This Notebook takes datasets from PupleAir_datainput&calibration.ipynb, filtering by set date range, and steps through analysis used in Atwood et al. (2026)
   --> This includes heierarchal resampling based on time period data thresholding; change detection of time series and daily, weekly and annual analysis
   --> Datasets from S-NPP VIIRS were used for fire count data
