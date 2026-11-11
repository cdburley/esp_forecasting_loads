# esp_forecasting_loads
This dataset was developed as part of the HydroWIRES D3 - Hydropower Operational Opportunities (75432) funded by 
the US DOE Office of Hydropower and Hydrokinetics (H2O).

## Contributors
Data was produced by Aowabin Rahman (aowabin.rahman@pnnl.gov) and Casey Burleyson (casey.burleyson@pnnl.gov). Both 
should be considered for co-authorship on any papers that leverage this dataset.

## Summary
Loads were produced using the machine-learning (ML) workflow that underpins the Total ELectricity laods (TELL) model.
We trained a unique ML model for each of 31 load areas in the western U.S. The approximate service territory for each 
of those load areas are plotted in the `/figures/load_area_service_territory` directory. These load areas are largely 
the recognized Balancing Authorities (BAs) except CISO which breaks their loads down into four zones within the BA: PGE, 
SCE, SDGE, and VEA. Note that TELL does not model BAs in Canada or Mexico so the total loads summed over the U.S. 
western interconnection are slightly lower than the reported values which reflect a handful of additional BAs outside 
the U.S.

The models were trained using historical hourly loads and meteorology from 2021-2022 with 2023 used 
as a validation year and 2024 as an evaluation year. The models perform reasonably well. The root hourly load data that 
we trained on came from the EIA-930 dataset and historical meteorology was derived from IM3's Thermodynamic Global 
Warming (TGW) simulations. Hourly meteorology was first spatially averaged within each county and then population-
weighted to create a single 8760-hr (8784-hr in leap years) time series of meteorology for each load area.

Once trained, we passed 45 years of historical weather (1980-2024) through the models. This is equivalent to asking 
"What if the weather of 1980, for example, impacted the system as it existed in 2021-2022?" The final data products are
hourly demands from 1980-2024 for each load area as well as an additional set of .csv files that sum the load areas to 
create time-series for the U.S. western interconnection as a whole. All times are in UTC. Non-leap years contain 
8760-hrs of loads while weather years that were leap years contain 8784-hrs.

The final dataset was passed to Nathalie Voisin on 11-Nov 2026 via Teams.

## Workflow
Use the following notebooks to recreate the visualizations shown in the `/figures`. The specific load areas the analysis 
uses are controlled in the `wecc_load_areas.csv` file in the `/data` directory.

| Notebook Order |           Script Name            |                                Description                                | 
|:--------------:|:--------------------------------:|:-------------------------------------------------------------------------:|
|       1        | plot_ba_service_territory.ipynb  |   Plots the service territory of the load areas used in this analysis.    |
|       2        | plot_wecc_load_variability.ipynb | Plots the variability in loads summed across the western interconnection. |

## Citations
Any use of this data in a publication, presentation, or report should use the following citations.
>
**Citation for the TELL model**
>
McGrath et al., (2022). tell: a Python package to model future total electricity loads in the United States. Journal of Open Source Software, 7(79), 4472, https://doi.org/10.21105/joss.04472
> 
**Citation for the underlying weather data**
>
Burleyson, C., Thurber, T., & Vernon, C. (2023). Projections of Hourly Meteorology by County Based on the IM3/HyperFACETS Thermodynamic Global Warming (TGW) Simulations (v1.0.0) [Data set]. MSD-LIVE Data Repository. https://doi.org/10.57931/1960548
> 
Jones, A. D., Rastogi, D., Vahmani, P., Stansfield, A., Reed, K., Thurber, T., Ullrich, P., & Rice, J. S. (2022). IM3/HyperFACETS Thermodynamic Global Warming (TGW) Simulation Datasets (v1.0.0) [Data set]. MSD-LIVE Data Repository. https://doi.org/10.57931/1885756