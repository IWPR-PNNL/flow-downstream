---
layout: default
title: Getting Started
nav_order: 2
---


# Getting started
## About
The flow model (flow) gives us the capability to organize and evaluate the interdependencies and linkages between sectors at various levels of granularity and across regions. We can use **flow** to gain an understanding of topics such as:
1. which regions have the greatest water intensity in their energy sectors,
2. which regions have the greatest energy intensity in their water sectors,
3. which sectors within a region have high water and/or energy intensities
4. how do energy and water intensities and interdependencies compare across regions,
5. which regions offer the greatest opportunity for energy and water resilience and efficiency enhancement,

Though **flow** provides sample data to run water and energy data for each county of the US, it can be extended to function for any set of regions (e.g., province, country, zip code, neighborhood) so long as the correct prerequisite data has been provided. Additionally, while **flow** was constructed to build water and energy interdependencies, units and sectors are customizable by the user, meaning that flow can be used to evaluate interdependencies between any sectors (e.g., water-food, energy-land) so long as the correct prerequisite data is provided. The prerequisite data must be in the form of two-dimensional tabular data including (1) An initial column containing rows of region identifiers (e.g., county FIPS code), (2) additional columns documenting initial flow values (e.g., water withdrawals to the public water supply), intensity factor assumptions (e.g., unit of energy required per unit of water withdrawn in the public water supply), and source/discharge fraction assumptions (e.g., 35% of electricity used in the public water supply sector is discharged to rejected energy). This prerequisite data is used by the model to iteratively build the specified connections between sectors for each region specified. In addition to building connections between sectors (e.g., electricity demand to public water supply sector), input data can be specified up to five levels of sub-sector granularity. For example, flows between total electricity demand and public water supply can be split into individual applications within the public water supply sector such as fresh surface water pumping, fresh groundwater treatment, and others.

In addition to calculating and organizing flows across sectors, **flow** also provides visualization and analysis functions to digest the aggregated data output. These include: sankey diagrams of each unit (water and energy) showing flows between sectors in a given region, bar charts of specified sectors showing the breakdown of subsector components (e.g., electricity use by application in public water supply), and an interactive map to compare output values across included regions. Note that the geospatial maps require additional prerequisite data.


## Python version support

Python 3.7, 3.8, and 3.9


## Installation

**flow** can be installed via pip by running the following from a terminal window::

`pip install flow`

## Dependencies

| Dependency | Minimum Version  |
|:-----------|:-----------------|
|numpy       | 1.19.4           |
|pandas      | 1.3.4            |
|plotly      | 5.5.0            |
