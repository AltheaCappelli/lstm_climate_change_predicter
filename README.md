# __Rising temperatures in Europe: Visualizations and LSTM predictions__ 


<img src="https://raw.githubusercontent.com/altheacappelli/altheacappelli.github.io/main/images/lstm_temp_comparison.svg" width="900">
<p><strong>Figure 1:</strong> <i>LSTM predictions (orange) and MC dropout mean predictions with uncertainty regions (purple) for mean European temperature anomalies from 1940 to 2024, showing a good match between the trained neural network with the observed trend.</i></p>
<img src="https://raw.githubusercontent.com/altheacappelli/altheacappelli.github.io/main/images/bubbles_eu.svg" width="900">
<p><strong>Figure 2:</strong> <i>Scatter plot of mean European monthly temperature anomalies from 1940 to 2024, showing stronger warming in winter months like December, January, and February.</i></p>

  
Both projects aim to work with the __mean European temperature anomalies__ based on time series climate data from the __[ERA5 Reanalysis dataset](https://cds.climate.copernicus.eu/datasets/reanalysis-era5-single-levels?tab=overview)__ provided by the __Copernicus Climate Data Store (CDS)__. $\\$
The first project uses a very simple __LSTM neural network__ built with Tensorflow that learns to compute and predict the temperature anomaly pattern from time series climate data.  
The second project focuses on __visualization__ of the ERA5 data with Matplotlib, using different types of plots to highlight patterns over time and space.  
__[See my other projects](https://altheacappelli.github.io/)__

### __Requirements__

To run these projects, you’ll need following Python packages:

- for data handling:  
`xarray==2025.1.2`
- for visualization:  
`numpy==2.0.2`  
`matplotlib==3.10.0`  
`scipy==1.15.2`  
`cartopy==0.24.1`  
- for ML model:  
`tensorflow==2.18.0`

Install them all together by writing:

```bash
pip install -r Requirements.txt
```

### __Data__

To run this project, you’ll need to download the climate data manually from the CDS.

- Go to this link:  
   [ERA5 Single Levels Dataset](https://cds.climate.copernicus.eu/datasets/reanalysis-era5-single-levels?tab=download)

- Choose the following parameters. These are __exactly__ the parameters used when I downloaded the dataset for this project. If you change them, the code may need slight adjustments to work properly.

- __Product type__: `reanalysis`  
- __Variable__: under “Popular”: `2m temperature`  
- __Year__: select _all_ available years  
- __Month__: select _all_ months  
- __Day__: only select the _15th_ of each month  
    _(one day per month, enough to see patterns without making the file huge)_
- __Time__: `10:00`  
    _(this time is usually not too hot or cold)_  
- __Geographical area__: choose _Sub-region extraction_ and set:  
  - __North__: `75`  
  - __West__: `-30`  
  - __East__: `50`  
  - __South__: `30` 
  _(focus on Europe)_  
- __Data format__: `NetCDF (.nc)`

- Click __Download__  
   _Note: it may take up to 20 minutes to generate the file!_

- Once downloaded, save the file in your project's folder, or create one if needed. Pay attention that the name of the dataset is the same as the one used in the code, adjust if not.

### __Output & results__
Find the full write-up and results on my website [here](https://altheacappelli.github.io/).

After running the script, you will get:
- a simple LSTM model, which reproduces the pattern of temperature anomaly up to 2024 and forecasts future anomalies,
- line plots showing predicted and future vs. actual anomalies,
- MAE metrics to evaluate the performance of the LSTM model,
- line plot of mean anomalies, scatter plots with monthly trends, and geographical maps highlighting anomalies across Europe.
