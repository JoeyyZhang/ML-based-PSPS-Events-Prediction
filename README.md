# Machine Learning-Based PSPS Events Prediction in California

**Course:** ER131 - Data, Environment, and Society (Fall 2025)  
**Department:** Energy & Resource Group (ERG)  
**University of California, Berkeley**

## Overview

This project develops machine learning models to predict Public Safety Power Shutoff (PSPS) events in California at the county level, providing critical insights for emergency preparedness and resource allocation. By forecasting PSPS occurrence, impact, and duration one week in advance, this work enables local officials to proactively deploy resilience resources and mitigate public health risks.

## Project Objectives

Our models predict three key outcomes for PSPS events:

1. **Occurrence Prediction**: Whether a PSPS event will occur in a given county on a given day
2. **Impact Forecasting**: Number of customers affected by a PSPS event
3. **Duration Estimation**: Whether the maximum outage duration will exceed 24 hours

These predictions support:
- Emergency resource allocation (generators, batteries)
- Community resilience hub activation
- Traffic management and emergency response planning
- Protection of medically vulnerable populations

## Key Results

### Model Performance

- **PSPS Occurrence (Logistic Regression)**: 70.7% test recall - valuable for early preparedness actions
- **Customer Impact (Random Forest)**: 60% R² on test set - provides directional guidance for resource allocation
- **Customer Impact Categories (Extra Trees)**: 77% test recall for High-Medium-Low classification
- **Duration Prediction**: 95.3% test recall and 79% test accuracy for predicting outages exceeding 24 hours

## Methodology

### Data Sources

Our analysis integrates multiple geospatial and temporal datasets:

- **PSPS Records**: California Public Utilities Commission (CPUC) historical PSPS data
- **Weather Data**: 
  - Temperature & precipitation from NASA's DAYMET V4
  - Wind data from ECMWF's ERA-5 Land Dataset
- **Vegetation**: U.S. Drought Monitor's Drought Severity and Coverage Index (DSCI)
- **Infrastructure**: CPUC utility ignition data, California land use planning data
- **Geographic**: U.S. Census Bureau county shapefiles and census tract data

### Feature Engineering

- Spatial joining of PSPS events to county boundaries using census tract GEOIDs
- Temporal disaggregation into daily observations
- Generation of non-event rows for complete dataset
- Integration of lagged weather variables for predictive modeling
- Extraction of residential land use metrics per county

### Machine Learning Models

Models tested include:
- Logistic Regression
- Random Forest
- AdaBoost
- Gradient Boosting
- Extra Trees

Hyperparameter optimization conducted using GridSearchCV with custom scoring metrics optimized for recall and precision based on use case requirements.

## Technical Implementation

**Language**: Python (Jupyter Notebook)

**Key Libraries**:
- Data Processing: `pandas`, `geopandas`, `numpy`
- Machine Learning: `scikit-learn`
- Visualization: `matplotlib`, `seaborn`
- Geospatial: `shapely`, Google Earth Engine (`ee`)

**Workflow**:
1. Data extraction and cleaning from multiple sources
2. Spatial joins and temporal alignment
3. Feature engineering and correlation analysis
4. Model training with cross-validation
5. Hyperparameter tuning and model evaluation
6. Performance visualization and interpretation

## Research Context

California's increasing wildfire frequency has led utilities to implement PSPS as a fire mitigation strategy. While effective in reducing fire risk, PSPS events can:

- Leave vulnerable communities without power for days
- Endanger medically dependent populations
- Disrupt critical infrastructure and services
- Impact disproportionately rural and low-income communities

Current utility frameworks for PSPS decisions vary by region and rely on localized interpretation of weather forecasts, vegetation conditions, and grid infrastructure. This variability creates uncertainty for policymakers and communities, limiting their ability to prepare effectively.

## Resource Allocation & Policy Implementation

Our predictive models enable:

- **Resource Pre-Positioning**: Deploy generators and batteries to critical facilities before outages
- **Resilience Hub Activation**: Community centers with backup power, cooling/heating, and essential services
- **Medical Support**: Proactive outreach to medically vulnerable populations
- **Economic Planning**: Business continuity and school closure coordination
- **Traffic Management**: Emergency response and traffic light backup systems

## References

Key research informing this work:

1. California Public Utilities Commission. "Public Safety Power Shutoffs (PSPS)." (2025)
2. Warner, Callaway & Fowlie. "Dynamic Grid Management Technologies Reduce Wildfire Adaptation Costs." (2025)
3. Abatzoglou et al. "Population exposure to pre-emptive de-energization aimed at averting wildfires." (2020)
4. Burrows, et al. "De-energization as maladaptation: Uneven residential exposure to wildfire PSPS and compound heat." (2025)
5. Lesage-Landry et al. "Optimally Scheduling Public Safety Power Shutoffs." (2022)

## Future Work

Potential extensions include:
- Finer spatial resolution (census tract or utility service territory level)
- Real-time integration with weather forecasts
- Socioeconomic vulnerability indexing
- Cost-benefit analysis of different resilience strategies
- Integration with utility-specific decision frameworks

## License & Usage

This project was completed as part of ER131 coursework at UC Berkeley. For questions or collaboration opportunities, please contact the team members.

---

**Institution**: University of California, Berkeley  
**Department**: Energy & Resource Group (ERG)  
**Course**: ER131 - Data, Environment, and Society  
**Term**: Fall 2025
