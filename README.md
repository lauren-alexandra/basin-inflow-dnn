Basin Inflow LSTM: Forecasting Regional Water Quantity for Reservoir Operation
=====

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
