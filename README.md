Basin Inflow LSTM: Forecasting Regional Water Quantity for Reservoir Operation
=====

Overview
----
Basin Inflow LSTM is an implementation of a long short-term memory model for forecasting reservoir inflow in the American River Basin located in the Sacramento, California region. The proposal model is composed of stacked LSTM layers, with regularization applied to both (L2, dropout, and recurrent dropout), followed by a densely connected layer. Model application and evaluation uses river basin data with temporal coverage from 2008-2022. Across the watershed and along forks of the river, daily precipitation, temperature, snow water content and depth, and river discharge and stage are employed to predict local reservoir inflow. Data was pre-processed with a 30-day exponential moving average to give recent weather events more weight in the forecast, normalized, and made stationary for training. 14 years of data were separated into three sets: training set (2008-2017), validation set (2018–2020), and test set (2020-2022). The model achieves a lower MAE score (0.036) in inflow prediction than the baseline model. 


Data
----

California Data Exchange Center: California Department of Water Resources

- Window: Daily and hourly records from 01-01-2008 to 12-31-2022 
- Source: California Data Exchange Center. (n.d.). *CDEC Webservice JSON and CSV*. https://cdec.water.ca.gov/dynamicapp/wsSensorData

#### American River Watershed Stations
<img width="747" alt="River Basin Stations" src="https://github.com/lauren-alexandra/weather-informed-reservoir-operation/assets/56773938/5bd98c71-6fe8-415e-a904-f72d4373ba35">

Google. (n.d.). [River Basin Stations]. Retrieved November 26, 2023, from https://maps.app.goo.gl/5ACnKE3bT1TMQ15J8


Run locally
----

### Download/Clone Git Repository

    $cd <replace with desired location of project folder>
    $git clone https://github.com/lauren-alexandra/basin-inflow-lstm.git
    $cd basin-inflow-lstm

### Create Environment

    $conda create -n myenv
    $conda activate myenv

### Install required packages

    $conda install pip
    $pip install -r requirements.txt

### Set up Jupyter Notebook Kernel

    $pip install --user ipykernel
    $python -m ipykernel install --user --name=myenv

### Launch Jupyter Notebook

    (in git bash or other conda environment)
    $jupyter notebook
