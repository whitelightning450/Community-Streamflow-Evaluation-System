
![Github_top](https://user-images.githubusercontent.com/33735397/206313977-e67ba652-3340-4a1b-b1d1-141d8d5001f2.PNG)

# Community Streamflow Evaluation System (CSES)

![GitHub](https://img.shields.io/github/license/whitelightning450/Community-Streamflow-Evaluation-System?logo=GitHub&style=plastic)
![GitHub top language](https://img.shields.io/github/languages/top/whitelightning450/Community-Streamflow-Evaluation-System?style=plastic)
![GitHub repo size](https://img.shields.io/github/repo-size/whitelightning450/Community-Streamflow-Evaluation-System?logo=Github&style=plastic)
![GitHub language count](https://img.shields.io/github/languages/count/whitelightning450/Community-Streamflow-Evaluation-System?style=plastic)
![GitHub commit activity](https://img.shields.io/github/commit-activity/m/whitelightning450/Community-Streamflow-Evaluation-System?style=plastic)
![GitHub Pipenv locked Python version](https://img.shields.io/github/pipenv/locked/python-version/whitelightning450/Community-Streamflow-Evaluation-System?style=plastic)
![GitHub branch checks state](https://img.shields.io/github/checks-status/whitelightning450/Community-Streamflow-Evaluation-System/main?style=plastic)
![GitHub issues](https://img.shields.io/github/issues/whitelightning450/Community-Streamflow-Evaluation-System?style=plastic)
![GitHub milestones](https://img.shields.io/github/milestones/closed/whitelightning450/Community-Streamflow-Evaluation-System?style=plastic)
![GitHub milestones](https://img.shields.io/github/milestones/open/whitelightning450/Community-Streamflow-Evaluation-System?style=plastic)
![GitHub milestones](https://img.shields.io/github/milestones/open/whitelightning450/Community-Streamflow-Evaluation-System?style=plastic)

A Novel Community Streamflow Evaluation System (CSES) to evaluate hydrological model performance using a standardized NHDPlus data model.
CSES evaluates modeled streamflow to a repository of over 5,000 in situ USGS monitoring sites, with interactive visualizations supporting an in-depth analysis.
![SupportLogo](./Images/SupportLogo.JPG)
## Application Overview
Given the launch of the Cooperative Institute for Research to Operations in Hydrology (CIROH) in April, 2020, CIROH scientists from 28 different academic, government, and private are working to improve the understanding of hydrologic processes, operational hydrologic forecasting techniques and workflows, community water modeling, translation of forecasts to actionable products, and use of water predictions in decision making. National-scale streamflow modeling remains a modern challenge, as changes in the underlying hydrology from land use and land cover (LULC) change, anthropogentic streamflow modification, and general process components (reach length, hydrogeophysical processes, precipitation, temperature, etc) greatly influence hydrological modeling. To benchmark model performance, characterize improvements in hydrological modeling formuations, and generate reproducible science, the team at the Alabama Water Institute (AWI) developed Community Streamflow Evaluation System (CSES) to originally characterize the water supply forecasting skill of the National Water Model v2.1 (NWM v3.0 coming soon!) in the Great Salt Lake Basin. The tool quickly scaled and with the support of the Earth Science Information Partners (ESIP), provided an opportunity to turn the tool into a novel evaluation platform for CONUS-wide applications. The package contains three key methods for evaluation: state-based LULC, HUC level analysis, and USGS station-based analysis. Below is a description of each method and application.
Designed to assess NWM version 2.1 retrospective performance, by using the exemplified data model the tool can evaluate other model predictions, with the motivation to improve regionally dominant hydrological modeling skill.
By using CSES, researchers can identify locations where a model may benefit from further training/calibration/parameterization or a need for new model processes/features (e.g., integration of reservoir release operations) to ultimately create new post-processing methods and/or hydrological modeling formulations to improve streamflow prediction capabilities with respect to modeling needs (e.g., stormflow, supply, emergency management, flooding, etc).   

## Streamflow Evaluation Options
Each streamflow evaluation method requires similar inputs, including a start date, end date, and model.
There are currently three different evaluation classes, each providing the user with a unique method for evaluating streamflow modeling performance:
- Class Eval_State(): Modeled Streamflow Evaluation by StreamStats
- Class HUC_Eval(): Modeled Streamflow Evaluation by Hydrologic Unit Code (HUC)
- Class Reach_Eval(): NHD - USGS Streamflow Evaluation

For all examples, the predictions are from the NWM v2.1 retrospective. 
Please see the Examples folder for more information on applying each specific class.

### State Evaluation Methods
To determine how LULC affects the predictive performance of streamflow models, Community Streamflow Evaluation System (CSES) uses StreamStats to categorize the watershed upstream of each USGS monitoring site by watershed characteristics.
Please see the** State Land Use - Land Cover Evaluation.md** readme to use the tool.

![LULC_mapping](https://user-images.githubusercontent.com/33735397/205775870-5efab8e2-57ce-4ecb-b6c1-012909ece220.PNG)


_Running the Community Streamflow Evaluation System LULC_Eval class loads, processes, and visualizes model performance for the state, category, and size of interest_

![LULC_mapping_highlight](https://user-images.githubusercontent.com/33735397/205776459-355507b4-2036-4eca-8bb3-fc88debbebef.PNG)

_By clicking on a marker a popup of the modeled vs. observed performance at the inputted temporal frequency will appear_

![LULC_holoviews](https://user-images.githubusercontent.com/33735397/205777709-65a8e6d8-0d7a-42e5-81b3-819462cb6e6a.PNG)

_The Community Streamflow Evaluation System supports an interactive engagement with model results_



### HUCid Evaluation Methods
The HUC_Eval class allows the user to evaluate modeled streamflow with observed in situ NWIS monitoring sites  for watershed(s) of interest. 
The user can input multiple watersheds (e.g., Great Salt Lake: ['1601', '1602'])
The user must enter a start date, end date, watersheds, and model to compare (NWM v2.1 is set up).
NWM retrospective data spans from 1980 - 2020, and USGS/NWIS data is location-dependent.

![LULC_HUC_GSL](https://user-images.githubusercontent.com/33735397/206265320-7c640b40-830e-41ed-8e3f-67a2b20984c5.PNG)

_The HUC_Eval class loads all USGS and colocated modeled NHD reaches for evaluation.
Color coding of the markers allows for quick identification of poor and well-performing reaches and clicking on the markers will put up a modeled vs. observed graph at the desired temporal resolution._

![LULC_holoviews_HUCEval](https://user-images.githubusercontent.com/33735397/206265779-5417343f-ed40-4704-b8bc-12ada2672259.PNG)

_Similar to the State_Eval class, the HUC_Eval class supports a more in-depth graphical analysis of the modeled vs. observed using the holoviews package_

### Reach Evaluation Methods

The Reach_Eval class allows the user to evaluate modeled streamflow with selected NWIS monitoring sites of interest. 
The user can input multiple USGS sites (e.g., ['02378780', '02339495', '02342500'])
Similar to the other classes, enter a start date, end date, and model to compare (NWM v2.1 is set up).
NWM retrospective data spans from 1980 to 2020, and USGS/NWIS data is location-dependent


![LULC_ReachEval_map](https://user-images.githubusercontent.com/33735397/206266617-f06c9836-0193-4f6f-94f9-11982272d34d.PNG)

_The Reach_Eval class quickly loads and maps the selected USGS streamflow monitoring locations, along with the colocated model predictions of NHD reaches.
The color code of the marker indicates the model performance at the respective USGS monitoring station site, and by clicking on a marker, the interactive map produces a graph at the desired temporal resolution._


![LULC_holoviews_Reach_Eval](https://user-images.githubusercontent.com/33735397/206267196-749bb94d-aa57-4d24-9b4e-97e7567e1fc0.PNG)

_Similar to the State_Eval and HUC_Eval classes, the Reach_Eval class supports a more in-depth graphical analysis of the modeled vs. observed using the holoviews package_

### Data Access
Community Streamflow Evaluation System (CSES) leverages USGS/NWIS observations from 1980-2020 and colocated and while all data is publically available through the respective agencies, we found the download time to be preventative for a timely model evaluation. 
The Alabama Water Institute at the University of Alabama hosts NWM v2.1 retrospective for all colocated USGS monitoring stations at a daily temporal resolution and provides the data free of charge via access to Amazon AWS S3 cloud storage.
CSES can quickly access observed and predicted data supporting a fast and repeatable tool for evaluating modeled streamflow performance.

## Dependencies (versions, environments)
Python: Version 3.9.12. 

### Required packages
The included requirements.txt file should set up the correct Community Streamflow Evaluation System (CSES) environment.
To use CSES, create a virtual Python environment and run the requirement.txt file to ensure all package versions are correct.
To get started, click the [Here](./Getting%20Started.md)

### Want to see your model in CSES?
Please reach out the AWI team so we can put your model results in our AWS S3 database. We currently have a simple data model and are looking into more computationally efficient methods to expedite interactivity and the overall hydrological model evaluation experience.

### Want to contribute?
Reach out to the AWI team and we can identify meaningful areas to grow Community Streamflow Evaluation System (CSES). Community is in the name for a reason and we intend to integrate more hydrological modeling components into the tool kit as funding allows. Specific areas of contribution include snow, atmospheric forcings, and other model outputs. Let's advance the community modeling paradigm together!

## Funding Acknowledgement
Funding to support this research was awarded to the Cooperative Institute for Research to Operations in Hydrology (CIROH) through the NOAA Cooperative Agreement with The University of Alabama (NA22NWS4320003). This work is based on CIROH's Community Streamflow Evaluation System (CSES) provided by the ESIP Lab with support from the National Aeronautics and Space Administration (NASA), National Oceanic and Atmospheric Administration (NOAA) and the United States Geologic Survey (USGS).
