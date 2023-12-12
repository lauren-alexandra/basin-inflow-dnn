Basin Inflow LSTM: Forecasting Regional Water Inflow
=====

Overview
----
Basin Inflow LSTM is an implementation of a long short-term memory model for forecasting reservoir inflow in the American River Basin located in the Sacramento, California region. The proposal model is composed of stacked LSTM layers, with regularization applied to both (L2, dropout, and recurrent dropout), followed by a densely connected layer. Model application and evaluation uses river basin data with temporal coverage from 2008-2022. Across the watershed and along forks of the river, daily precipitation, temperature, snow water content and depth, and river discharge and stage are employed to predict local reservoir inflow. Data was pre-processed with a 30-day exponential moving average to give recent weather events more weight in the forecast, normalized, and made stationary for training. 14 years of data were separated into three sets: training set (2008-2017), validation set (2018–2020), and test set (2020-2022). The model achieves a lower MAE score (0.036) in inflow prediction than the baseline model. 


Background
----
The Department of Interior’s Bureau of Reclamation (BOR) employs river basin observations including streamflow, snowpack, temperature, and precipitation in addition to projected water demand to operate reservoirs in California’s Central Valley Project. Water managers must optimize storage during dry periods while allocating space for flood control. In 2019, BOR approved a water control manual for the Folsom Reservoir north of Sacramento that relies on weather forecasts to make more accurate release decisions and engage the auxiliary spillway for flood management (BOR, 2021). 

Sacramento and surrounding municipalities exist on a floodplain. The area receives most of its water from precipitation in the Sierra Nevada during a short wet period consisting of five to six Pacific storms on average, with high year-to-year variability (Ingram & Malamud-Roam, 2015). A difference of one to two major storms can ensure a normal versus a dry water year. Water management in the state has proven challenging since its founding. This challenge was evident in the early years of the state, when in late 1861 and the beginning of 1862 unprecedented snowfall followed by a series of warm storms drenched the western Sierra Nevada with four times its annual average rainfall, swelling the American River Basin, eliminating mining settlements, displacing communities, and submerging Sacramento under ten feet of water (Ingram & Malamud-Roam, 2015). The extensive destruction of the 1861-1862 floods in Sacramento and across the state, led the city to pursue a project of raising the district by ten to fifteen feet shortly after the flooding. Notably, on January 11, 1862 the *Nevada City Democrat* reported that indigenous people left the area a week before the floods, recognizing the weather pattern of atmospheric river storms. 

Folsom Reservoir (1956) was constructed by the U.S. Army Corps of Engineers for the purpose of flood damage reduction. Another area within California State Parks’ American River District, the Auburn State Recreation Area, was also evaluated as a potential location for a dam that would have regulated downstream flow into the Folsom Reservoir. However, construction of the dam was frequently impeded for decades by concerns around the dam’s design, cost, and purpose. The fight over the proposed dam was acutely chronicled in Auburn State Recreation Area park ranger Jordan Fisher Smith’s (2006) memoir. In 1991, the district’s superintendent advocated for the concept of a “dry dam” which would have flooded the American River canyons after a storm. The following year the U.S. Army Corps of Engineers as well as a flood control agency formed by local governments supported a flood-control Auburn dam. Yet the quickly growing populations of nearby towns in the Fourth Congressional District exerted an opposing pressure on the district’s representative John Doolittle, and by 1995 he committed to sinking any proposal which did not generate power and store water for his district’s population. Finally, in 2008 the fights concluded when the State Water Resources Control Board revoked BOR’s federal water rights, ending the stalled project. Today decisions balancing flood events in the American River Basin and both local and state water demand must be handled by the Folsom Reservoir and Dam. 

BOR operation in the American River Basin must adapt not only to the region’s typical variability, but also to shifts in timing and quantity of precipitation in a warming climate. The state’s water year now experiences earlier snowmelt with lower streamflows in the summer when demand is high (East & Grant, 2023). Positioning the reservoir to hold capacity for floods in the wet season while storing requisite supply for summer months will necessitate close observation of upstream flow variation (Naz et al., 2018) and strategic changes in operation policies downstream. Moreover, during the past 80 years there has been a greater magnitude of wet extremes during the winter season (Zamora-Reyes et al., 2021). Atmospheric river storms are projected to be more extreme under climate change with a significant decrease in snow at higher elevations in the Sierra Nevada (Huang et al., 2020), generating sizable runoff and obstacles for flood management. Climate science must be incorporated into daily operation to handle the growing variability of the state’s hydroclimate.

References

Bureau of Reclamation. (n.d.). *Folsom Dam joint federal project*. https://www.usbr.gov/mp/mpr-news/docs/factsheets/folsom-dam.pdf 

Bureau of Reclamation. (2021). *Water reliability in the west - 2021 SECURE Water Act report*. https://www.usbr.gov/climate/secure/docs/2021secure/2021SECUREReport.pdf

East, A. E., & Grant, G. E. (2023). A watershed moment for western U.S. dams. *Water Resources Research, 59*(10). https://doi.org/10.1029/2023WR035646 

Huang, X., Stevenson, S., & Hall, A. D. (2020). Future warming and intensification of precipitation extremes: A “double whammy” leading to increasing flood risk in California. *Geophysical Research Letters, 47*(16), 1-9. https://doi.org/10.1029/2020GL088679 

Ingram, B. L., & Malamud-Roam, F. (2015). *The west without water: What past floods, droughts, and other climatic clues tell us about tomorrow*. University of California Press. 

Naz, B. S., Kao, S., Ashfaq, M., Gao, H., Rastogi, D., & Gangrade, S. (2018). Effects of climate change on streamflow extremes and implications for reservoir inflow in the United States. *Journal of Hydrology, 566*, 359-370. https://doi.org/10.1016/j.jhydrol.2017.11.027 

Smith, J. F. (2006). *Nature noir: A park ranger’s patrol in the Sierra*. Mariner Books. 

Zamora-Reyes, D., Black, B., & Trouet, V. (2021). Enhanced winter, spring, and summer hydroclimate variability across California from 1940 to 2019. *International Journal of Climatology, 42*(9). https://doi.org/10.1002/joc.7513 


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
