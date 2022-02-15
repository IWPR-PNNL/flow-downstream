---
layout: default
title: US Sample Data Methodology
nav_order: 5
has_children: true
---



# US Case Study

## Background
Information on the case study and project


## General Methodology
The following list of assumptions are applicable to the 2015 US Case Study:
- Calculations are for the year 2015, the most recent year available for water use data in the US. When data was unavailable for 2015, the closest year available was applied.
- Many calculation methodologies are informed by the literature. References for these methodologies are noted in the methodology descriptions as applicable.
- Water values are provided in million gallons per day (MGD) and energy values are provided in billion British thermal units (BBTU) per year
- Data was available at various levels of granularity across the US including county-level, state-level, and plant-level. Data was aggregated or split out appropriately so that the resulting dataset has values on the county-level, given by county FIPS code. When data collected was provided at the state-level, state-level totals are divided among state counties through an appropriate method (e.g. population weighting). When information was available at the plant level (e.g. power plant generation), information on plant county were used to sum plant values to achieve a county total.
- Where data was unavailable on a county level, assumptions were applied to obtain county-level data. These assumptions are additionally implemented in the flow package for those that wish to use them.


## Data

All data used in the 2015 US Case Study, which serves as the sample dataset for flow, was provided by the sources listed in the table below.

.. csv-table:: a title
  :header: "Data File Name ", "Description", "Reference", "Year of Data"
  :widths: 20, 20, 10

  "usco_2015.csv", "Estimated use of water in the United States in 2015", "Dieter et al. (2015)", 2015
  "usco_1995.csv", "Estimated use of water in the United States in 1995", "Dieter et al. (2015)", 2015



Sector Calculations & Methodologies
===============
Nearly all sectors included have energy in-flows (demand), energy out-flows (discharge), water in-flows (withdrawals), and water out-flows (discharge). The methodology for determining each of these is described within each sector section.

To see the code behind each of these calculations, see ___________
