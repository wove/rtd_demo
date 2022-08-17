# Individual ecosystem services tools

All of the individual ecosystem services tools requires the output from the **Generate Baseline** tool. Each tool generates files and several are loaded to the screen with the correct symbology and the legend. The key outputs are written to a PDF file that can be found within the output folder. If desired, the key maps and tables can be generated in PNG format by ticking the *Generate PNG maps and graphs parameter*. These maps and tables can be found under the Images folder of the output folder.

If a tool fails, the user can re-run the tool through the Results window and tick the Rerun tool (will continue pre- vious run from the point where any errors occurred option. This only works if the relevant files such as intermediate and temporary files are still within the scratch folder and have not been erased

## Agricultural Productivity

### Summary

This tool evaluates potential agricultural productivity of the land according to simple criteria (slope, fertility, aspect and drainage). The model calculates predicted optimal agricultural utilisation based on soil type, using assigned values of fertility and waterlogging (yes, no or seasonal) and topographic data, using calculated values for aspect slope and elevation. If desired you can weight this calculation to increase soil fertility values to account for farmer effort and management which may be applied due to low production potential in the region containing your study area. Current agricultural utilisation will be mapped according to the land cover data, ranking land use from highest productivity to lowest: Arable; Improved grassland; Unimproved grassland; Woodland and heath; Bog sand and rock. An output for relative utilisation is calculated from comparison of current and potential utilisation.

As input, this tool requires the outputs from the **Generate Baseline** tool. Output from this tool can be used to assess where land may be under or over utilised. The tool can also be used to identify areas of more productive land, where farmers may be less willing to make changes, and areas of less productive land,which could be targeted for re-wilding or afforestation

### Input

- **Output folder:** Specify the path and folder where output from this tool should be stored.

- **Input:** Study area baseline folder: Specify the path and folder where files are stored from running the **Generate Baseline** tool.

- **Slope threshold (degrees) for very productive land:** Maximum slope (in degrees) of very highly pro- ductive agricultural land. This can be changed to respect regional agricultural practice. If an adjusted value is applied, this should be considered when interpreting model output, in terms of additional management efforts required to enable agricultural production of steeper slopes. When setting this threshold DEM resolution should be considered. For example, use of an overly coarse DEM may mean that smaller areas of steep slope are not detected. *(Default value is 5.)*

- **Slope threshold (degrees) for somewhat productive land:** Maximum slope (in degrees) of somewhat productive agricultural land. This can be changed to respect regional agricultural practice. If an adjusted value is applied, this should be considered when interpreting model output, in terms of additional management efforts required to enable agricultural production of steeper slopes. When setting this threshold DEM resolution should be considered. For example, use of an overly coarse DEM may mean that smaller areas of steep slope are not detected. *(Default value is 15.)*

- **Elevation threshold (metres) for improved agriculture:** Maximum threshold in metres above sealevel (m asl) of productive agricultural land. This can be changed to respect regional agricultural practice. If an adjusted value is applied, this should be considered when interpreting model output, in terms of additional management efforts required to enable agricultural production at higher elevations. *(Default value is 350m asl.)*

- **Elevation threshold (metres) for all agriculture:** Maximum threshold in metres above sealevel (m asl) of all agricultural land. This can be changed to respect regional agricultural practice. If an adjusted value is applied, this should be considered when interpreting model output, in terms of additional management efforts required to enable agricultural production at higher elevations. *(Default value is 3000m asl.)*

- **Fertility relative to national standard:** This parameter allows fertility to be adjusted for regional variation to account for the study area being in a low or very low fertility region.

    - *1: standard*

    - *2: low fertility*

    - *3: very low fertility*

- **Save intermediate calculations?:** If this is selected, the intermediate categorisations for agricultural pro- ductivity, based on single indicators only (i.e. slope, waterlogging etc.), are saved for user inspection. This will enable consideration of how the component factors affect productivity potential. Saving this data is recommended if slope and elevtaion thresholds are adjusted or soil fertility reweighted because exploration of intermediary data will enable the influence of these user choices to be better understood when interpreting model output.

- **Consider slope in overall valuation?:** Select to consider slope in evaluation of agricultural productivity. This should be applied in areas where slope is a factor in agricultural productivity. If not selected in areas with slopes over relevant thresholds, this may reduce accuracy of output on predicted agricultural productivity.

- **Consider elevation in overall valuation?:** Select to consider elevation in evaluation of agricultural productivity. This should be applied in areas where elevation is a factor in agricultural productivity. If not selected in areas with elevations over relevant thresholds, this may reduce accuracy of output on predicted agricultural productivity.

- **Consider waterlogging in overall valuation?:** Select to consider waterlogging in evaluation of agricultural productivity. This should be applied in areas where waterlogging is a factor in agricultural productivity. If not selected in areas with waterlogging, this will reduce accuracy of output on predicted agricultural potential. Conversely, in areas where all soils are prone to waterlogging and have been artificially drained, it may be more accurate not to apply this variable, and this option should be de-selected.

- **Consider soil fertility in overall valuation?:** Select to consider soil fertility in evaluation of agricultural productivity. If not selected in areas where soil fertility is important this will reduce accuracy of output on predicted agricultural potential. Where management activities aim to overcome issues with soil fertility, it may still be appropriate to select this option, in combination with a soil fertility adjustment of 2 or 3 in "Fertility relative to national standard" above.

- **Consider aspect in overall valuation?:** Consideration of aspect can be adjusted. Choose adjustment desired from dropdown options:

    - *0: no*

    - *1: yes, direct face only*

    - *2: yes, direct face + face-E and face-W*

### Output

- Current agricultural utilisation (util_curr): This map predicts the current agricultural utilisation from the input land cover product (or land cover scenario), and is therefore reliant on its accuracy. Arable and improved grassland are considered to be highly productive, for example, while bare ground and wetlands are considered to provide no agricultural utilisation. The output is discrete; five categories of production are considered, from very high production (or production capacity) to no production (or production capacity).

- **Predicted optimal agricultural utilisation (util_pred):** This map ignores the input land cover, and instead predicts a near-optimal utilisation based on soil water holding characteristics, fertility, slope and aspect. Flat, well-draining and fertile areas are predicted to have high potential for agricultural production for example, more waterlogged areas or steeper areas have less potential. This model output is dependent on accuracy of user set thresholds and weightings, as well as the soil data layer supplied as input to the scenario pre-processing tool. Uncertainty may also be introduced through model processing, since values for soil fertility and waterlogging are based on estimates or national averages for the soil type, and may not reflect site conditions accurately.

- **Relative agricultural utilisation (util_rel):** This map compares the previous two outputs, and flags where land appears to be over or under-utilised. If both current and predicted utilisation are within one category of each other, land is considered to be appropriately utilised. If they differ by more than one category, LUCI flags where current production appears to be over utilising the land (so may be ineffcient farming, or not sustainable), and also where opportunities to increase agricultural production may be present. Any errors in model output for current and predicted agricultural utilisation will propagate through to this data layer.

- **Agricultural utilisation status (util_stat):** This map combines the current and "predicted optimal" output in a different way to the relative utilisation described previously. Rather than being concerned with direction of change (under or over utilisation), it considers whether the current agricultural utilisation may be worthy of preservation or change. Land in appropriate utilisation is considered worthy of protection, areas where land is over or under-utilised are flagged for consideration of change to management. This output is a fundamental input to the trade-off and synergy mapping algorithms within LUCI. Again, errors in model output for current and predicted agricultural utilisation will propagate through to this data layer

## Carbon Stocks and Fluxes

### Summary

**For England and Wales:** The model first calculates carbon levels at steady state i.e. assuming that land cover is fully established and soil and biomass carbon are no longer in flux. Values are assigned based on the soil and land cover combination, according to assumptions that a) the England and Wales mean for a given soil and landcover combination is broadly representative of the steady state soil carbon where that combination occurs and b) the England and Wales mean biomass carbon for a landcover is broadly representative of the steady state mean value. Values calculated for use in the model are based on the IPCC tier 1 protocols on Climate Change (IPCC); separating carbon into above ground biomass, below ground biomass, deadwood, litter, and soil carbon. The total values for biomass carbon and soil carbon are then fed into the model, to avoid modelling time spent on unnecessary processing.

The model then calculates potential to increase carbon storage over the landscape, by comparing a value of potential carbon stock at equilibrium under a different landcover with the current carbon stock. The model applies a "space for time" substitution to calculate potential for emissions or sequestration, in assuming that any change in carbon storage in soils following landuse change can be estimated based on comparison with data from other sites with the same soils where the new land use is already established. In the case of a supplied landcover change scenario, the second valuation layer is indicative of emissions, whilst in the case of a baseline run, the second valuation layer is indicative of potential for sequestration of carbon, as detailed below.

The values for carbon and land use combinations were based on Bradley et al. (2005), Milne and Brown (1997), and Morison et al. (2012).Values for some soil/land use combinations may be based on expert opinion where data were absent. These calcluations will also be affected by spatial uncertainty in land use and soil layers combined in stage 1.

**For New Zealand:** The model first calculates carbon levels at steady state i.e. assuming that land cover is fully established and soil and biomass carbon are no longer in flux. Values are assigned based on the land cover, according to assumptions that a) the average value for that landcoveris broadly representative of the steady state soil carbon where that coveroccurs and b) the average carbon for a landcover is broadly representative of the steady state mean value. Values calculated for use in the model are based on the IPCC tier 1 protocols on Climate Change (IPCC); separating carbon into above ground biomass, below ground biomass, deadwood, litter, and soil carbon.

The model then calculates potential to increase carbon storage over the landscape, by comparing a value of potential carbon stock at equilibrium for that soil type with the current carbon stock associated with the landcover. The model applies a "space for time" substitution to calculate emissions or sequestration, in assuming that any change in carbon storage in soils following landuse change can be estimated based on comparison with data from other sites with the relevant soil or landcover.

### Input

- **Output folder:** Specify the path and folder where output from this tool should be stored.

- **Input: Study area baseline folder:** Specify the path and folder where files are stored from running the **Generate Baseline** tool.

- **Very high stock threshold:** Threshold for stocks to be classified as very high that feeds into classification for mapping and tradeoffs. *Default value is 90.*

- **High stock threshold:** Threshold for stocks to be classified as high that feeds into classification for mapping and tradeoffs. *Default value is 50.*

- **Moderate stock threshold:** Threshold for stocks to be classified as moderate that feeds into classification for mapping and tradeoffs. *Default value is 27.*

- **Low stock threshold:** Threshold for stocks to be classified as low that feeds into classification for mapping and tradeoffs. *Default value is 21.*

## Output

- **Carbon stock (cstock) and Carbon stock to 30 (CSto30):** This map shows the estimated total carbon storage in the biomass and either top 1m or top 30cm of soil in tonnes/ha. Values are calculated based on soil carbon data for soil type and land-use combinations, and average biomass carbon for each land-cover type. The dataset used depends on the level of aggregation selected in the pre-processing tool; fully disaggregated *(Soil disaggregation value is 15)* uses published soil series level national data from Bradley et al. (2005); Milne and Brown (1997), whereas LULUCF inventory level *(Soil disaggregation value is 14)* uses values taken from the more aggregated inventory approach described in Dyson et al. (2009); Morison et al. (2012).

    Potential sources of error and uncertainty include inaccuracies in user input spatial land use and soil data; in particular, peats are not well accounted for spatially in soil or land use datasets. Accounting will have significant uncertainty, due to use of inventory values of average C for the relevant land use on the relevant soil type; these are often estimated, or based on limited sampling. Actual carbon storage will be strongly affected by site variation from national average conditions.

    Although average and estimated values are not expected to provide an accurate measure of change for in- dividual sites, there is an assumption that errors will balance out at scales relevant for most assessments, particularly for national level inventories. Likely site variation around the mean value applied is strongly affected by the option selected for soil disaggregation; there is much greater variance within the lumped soil types applied in the LULUCF compatible approach. Values for some soil/land use combinations in the fully disaggregated approach may be based on expert opinion where data were absent, increasing uncertainty.

- **Classified carbon stock (cstockclass):** This map is a classified version of carbon stock created both for display purposes and for calculation of inputs to trade-off mapping. Only provided for 1m of soil depth plus biomass, and subject to same sources of error as the non-classified version, in addition to influence from the user-set thresholds. The user provided values for low, moderate, high and very high storage should therefore reflect levels requiring improvements for agricultural purposes or worth protecting to avoid CO<sub>2</sub> emissions.

- **Carbon emission estimation (cemit):** This map predicts the rate of emissions or sequestration of C in tonnes/ha/year. Output will be subject to the same sources of error as the carbon stock maps, in addition to error associated with the space for time substitution approach, since soils may never reach the expected carbon value. There is an assumption that soils will take 150 years to reach the expected value, and output is provided as annual average sequestration or emissions, however soil carbon change tends to follow an exponential curve, and much of the change would occur during the first few years. This approach also fails to account for any initial losses due to soil disturbance etc., which will be strongly affected by land management approaches and timing of activities. Using the fully disaggregated approach, new soil carbon is calculated for the "effective depth" occupied by the same quantity of soil, to give a value for change in carbon that accounts for change in soil density.

    **For scenario:** In the case of a supplied landcover change scenario, the second valuation layer is indicative of emissions in kg m<sup>-2 yr-1</sup>, calculated as:
    
    ```{math}
    Scenario\ total\ C\ storage − Current\ total\ C\ storage \over 150
    ```
    
    **For current land cover:** In the case of a baseline run, the second valuation layer is indicative of potential for sequestration of carbon in soils. The scenario with most soil carbon is identified from the average under each land use on the relevant soil type, and sequestration potential thus calculated as:
    
    ```{math}
    Maximum\ potential\ soil\ C\ storage + Associated\ biomass\ carbon − Current\ total\ C\ storage \over 150
    ```

