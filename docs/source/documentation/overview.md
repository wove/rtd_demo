# Overview

The LUCI (Land Utilisation and Capability Indicator) model, is a second-generation extension and software implementation of the Polyscape framework, as described in (Jackson et al., 2013). LUCI explores the capability of a landscape to provide a variety of ecosystem services, such as agricultural production, erosion control, carbon sequestration, food mitigation, habitat provision etc. It compares the services provided by the current utilisation of the landscape to estimates of its potential capability, and uses this information to identify areas where change might be benefcial, and where maintenance of the status quo might be desirable.

## The ecosystem services that LUCI models include

- Agricultural production
- Erosion risk and sediment delivery
- Carbon sequestration
- Flood mitigation
- Habitat provision
- Water quality – Nitrogen and Phosphorus

## Background

Ecosystem service condition is assigned based on nationally-available datasets (enhanced with local data where available), on topography (raster DEM), stream network (vector polyline format), precipitation and evapotranspiration (raster format), land cover and soil type (vector polygon format). These are linked to lookup tables and processed within the model, with simulation of connectivity through cost distance approaches for habitat and topographic routing for hydrological and associated services. The topographic routing approach enables explicit simulation of movement of water and difuse pollution over the landscape, as well as identifcation of features which help to mitigate risk of flash flood and in-stream pollution. The model runs at catchment scale with a fine resolution, enabling assessment of the impact of farm scale interventions at catchment scale. The model also identities opportunities to improve ecosystem service condition, and these output maps can be used for decision support. Tradeoffs and synergies between individual service provisions are modelled explicitly to support such decision making. The LUCI framework is designed to follow the following principles:

(Table 1: Principles of the LUCI framework)
| Practical | Conceptual |
|--------------|-----------|
| Can be run using nationally available data; i.e. available everywhere so *relevant to national spatial planning* | Operates at a spatial scale *relevant for field and sub-field level management decisions* |
| Modular – can embed other models and aspects can be embedded in other models (LUCI is a *framework*) | "Values" features and potential interventions by area affected, not just area directly modified |
| Fast running to enable "real time" scenario exploration | Addresses trade-offs and searches for "win-win" solutions |

## Availability and requirements for application

LUCI is an evolving tool; the current release version includes the original Polyscape functionality along with additional water quality, data analysis and reporting functions. It requires ESRI's ArcGIS 10.1 or above to run. Documentation and help are included within this document, and additionally embedded within the LUCI software.

LUCI requires three datasets to run and can be enhanced with local data if available:

1. **Digital elevation model (DEM):** To represent landscape topography and ideally has a grid size of 5x5m
to 10x10m, although any resolution data can be used as input. The finer the resolution the more detailed the
output
2. **Land cover information:** To represent impacts of different types of vegetation and management on ecosys-
tem services. The land cover information must first be correlated to the existing database of land cover types
already supported by LUCI
3. **Soil information:** To represent the effect of soil types on ecosystem services. The soil information must first
be correlated to one of the existing soil classiffcation schemes already supported by LUCI

Other optional information that can be used as input include a stream network, rainfall, and evapotranspiration. These are not necessary to LUCI, but their addition improves the accuracy and reliability of LUCI output.

The DEM and stream network (if available) generates a hydrologically and topographically consistent DEM to correct for potential artefacts, allowing LUCI to more accurately simulate the flow of water through the landscape. Together with the land cover and soil information, LUCI generates a baseline scenario that feeds into determining the spatial distribution, supply, and opportunities of the individual ecosystem services. The land cover information can be amended to explore potential scenarios where the land use or management have changed. 

Because of its effcient numerical implementation, LUCI is fast-running and runs at multiple spatial scales, from sub-field to catchment to national planning. LUCI generates a series of ecosystem services maps that show areas of good provision and areas that would benefit from changes in management intervention. Multiple ecosystem services can be compared to identify where trade-offs or synergies in ecosystem services exist.

A number of national datasets are supported for United Kingdom and New Zealand applications; for other countries it is currently necessary to match land cover and soil information into the supported classiffcation systems. Support for a broader range of datasets will be added in the future. Suggested/default parameters are provided with LUCI; see the individual tool documentation for more detail.