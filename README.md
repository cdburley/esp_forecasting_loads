# esp_forecasting_loads

## Workflow
Use the following notebooks to rerun the analysis and reproduce the load data. The specific BAs the analysis uses are 
controlled in the `wecc_load_areas.csv` file in the `/data` directory. The underlying machine learning 
models rely on functions within the Total ELectricity Loads (TELL) python package. Before running any of the scripts 
below you should install TELL using `pip install tell`.

| Notebook Order |           Script Name            |                                Description                                | 
|:--------------:|:--------------------------------:|:-------------------------------------------------------------------------:|
|       1        | plot_ba_service_territory.ipynb  |   Plots the service territory of the load areas used in this analysis.    |
|       2        | plot_wecc_load_variability.ipynb | Plots the variability in loads summed across the western interconnection. |
