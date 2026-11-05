# esp_forecasting_loads

## Workflow
Use the following notebooks to rerun the analysis and reproduce the load data. The specific BAs the analysis uses are 
controlled in the `balancing_authority_modeled.yml` file in the `/data` directory. The underlying machine learning 
models rely on functions within the Total ELectricity Loads (TELL) python package. Before running any of the scripts 
below you should install TELL using `pip install tell`.

| Notebook Order |              Script Name               |                                                       Description                                                        | 
|:--------------:|:--------------------------------------:|:------------------------------------------------------------------------------------------------------------------------:|
|       1        |    plot_ba_service_territory.ipynb     |                              Plots the service territory of the BAs used in this analysis.                               |
|       2        | plot_ba_load_weather_time_series.ipynb |                     Plots the raw time series of the load, weather, and population data for each BA.                     |
|       3        |     train_and_run_mlp_models.ipynb     | Iteratively trains the TELL MLP models using evolving time windows and uses the models to project loads forward in time. |