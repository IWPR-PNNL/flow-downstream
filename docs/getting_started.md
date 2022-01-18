---
layout: default
title: Getting Started
nav_order: 2
---

# Getting started


## About


The flow model (flow) gives us the capability to estimate water flows (in million gallons per day) and energy flows (in billion btu per year) across and within various sectors across and within geographical regions to analyze the interdependencies and linkages between water and power. We can use **flow** to gain an understanding of topics such as
(1) which regions have the greatest water intensity in their energy sectors,
(2) which regions have the greatest energy intensity in their water sectors,
(3) which sectors within a region have high water and/or energy intensities
(4) how do energy and water intensities and interdependencies compare across regions,
(5) which regions  offer the greatest opportunity for energy and water resilience and efficiency enhancement,
(6) which regions show indicators of being at high risk for water and energy related threats

Though **flow** provides sample data to run each county of US for the year 2015, it can be extended to function for any set of regions (e.g., province, country, zip code, neighborhood) so long as the correct prerequisite data has been provided. The prerequisite data must be in the form of two-dimensional tabular data including (1) An initial data column containing rows of unique region identifiers (e.g., county FIPS code), (2) additional columns with "baseline" data for water flows (in million gallons per day) including water withdrawals to public water supply and any end-use sectors of interest (e.g., residential sector, agriculture sector) by provided region identifier and (3) energy flows [in billion british thermal units (bbtu) per year] to both electricity generation and end-use sectors of interest (e.g., residential, industrial, commercial). The baseline data must be complete for each region (e.g., for each county) specified in the region column and follow the naming conventions outlined for the model.

From the baseline dataset, downstream energy and water flows are calculated based on various customizable water, energy, and sector assumptions. Examples include: water consumption rates by sector, energy efficiency rates by fuel type, fuel types used in energy applications within a sector, and more. Note that these assumptions are applied to the baseline data provided by the user as necessary. That is, if more detailed sector-level and/or region-level data is available and provided by the user, the model will implement that data in the calculations in place of the generalized assumptions. For example, if water flows processed by the wastewater treatment sector are available for each region and supplied by the user, the model will determine energy use in wastewater based on these flows. However, if region-level water flows processed by wastewater treatment facilities is unavailable, the model will estimate water flows to wastewater treatment facilities for each region based on the estimated water discharge from end-use sectors (e.g., residential). In addition, if treatment type data is not provided by the user, the model will also apply assumptions to split out the estimated end-use water flows to wastewater treatment into different types of wastewater treatment flows (e.g., advanced, primary). The assumptions applied to fill the gaps where user data is not provided are customizable for each calculation, allowing for a highly customizable tool.

On top of calculating energy and water flows across sectors up to the maximum level of granularity given the supplied data, **flow** also determines various energy-water resilience metrics used to evaluate model outputs across and within regions.

Lastly, flow can use run output data to provide various visualizations including: barcharts, scattercharts, geospatial maps, sankey diagrams, and more. Note that the geospatial maps require additional prerequisite data.




## Python version support

Python 3.7, 3.8, and 3.9


## Installation

**flow** can be installed via pip by running the following from a terminal window::

    pip install flow

Conda/Miniconda users can utilize the ``environment.yml`` stored in the root of this repository by executing the following from a terminal window::

    conda env create --file environment.yml


## Dependencies

=============   ================
Dependency      Minimum Version
=============   ================
numpy           1.19.4
pandas          1.1.4
matplotlib      3.3.3
seaborn         0.11.1

=============   ================
