---
layout: default
title: Energy Production
parent: US Case Study
nav_order: 2
---

## Navigation
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

## Energy in Energy Production

The following energy production technologies are included in the analysis:
- Natural gas
- petroleum
- coal
- biomass
- nuclear
- hydropower
- geothermal
- solar
- wind

Energy production data by type is taken from SEDS state-level data for 2015 [EIA2015]_. Data is provided in BBTU/yr. Information is provided at the state level and broken up into county level based on population percentage of total state population. Population data is provided for each US county FIPS code for 2015 in Dieter et al. (2015).

MSN codes used from the EIA SEDS dataset include:
- "PAPRB": Crude oil production (including lease condensate) (BBTU)
- "EMFDB": Biomass inputs (feedstock) to the production of fuel ethanol (BBTU)
- "NGMPB": Natural gas marketed production (BBTU)
- "CLPRB": Coal production (BBTU)
- "NUETB": Nuclear energy consumed for electricity generation, total (BBTU)
- "GETCB": Geothermal energy total consumption (BBTU)
- "HYTCB": Hydropower total consumption (BBTU)
- "WYTCB": Wind energy total consumption (BBTU)
- "SOTCB": Solar energy total consumption (BBTU)

Note that for energy sources that are not direct fuels (e.g., solar, nuclear), production will be equal to total consumption.

## Water in Energy Production

Water in energy production is calculated for the following energy types:
- Coal (specifically, dust control in mining)
- Biomass (specifically, water used in corn growth for ethanol production)
- Natural gas (water used in drilling unconventional natural gas wells)
- Petroleum (water used in drilling both conventional and unconventional oil wells)

### Coal

#### Water withdrawal
Average water intensity values are provided for both surface and coal mines from [SOURCE], shown below:
(7 gallons of water per shortton and 29 million gallons per shortton)
1 shortton of coal = 0.02009 bbtu

Average surface coal mine water intensity = 0.00034 million gallons per bbtu
Average underground coal mine water intensity = 0.00144 million gallons per bbtu

Water type and source - Coal production is assumed to use water from each type and source at the same fraction as all mining in general. Fresh and saline, groundwater and surface water flows to mining is provided by Dieter et al. [SOURCE] and are therefore available on a county level. For the default assumptions in the flow package when determining the fraction of water to coal production from
each water type and water source, the average US values are used. These values are:

Water types and water source for coal mining
 - Fresh surface water: 43%
 - Fresh groundwater: 38%
 - Saline groundwater: 18%
 - Saline surface water: 1%
 - Wastewater: 0%

For counties that did not record water flows to mining in the USGS (dieter et al.) dataset, the US averages for water type and source percentages are applied.

#### Water Consumption/Evaporation
Estimates for consumed water from coal mining follow the same consumption fractions as for all mining water consumed. These values are not available in the 2015 dataset and are instead calculated from the 1995 USGS dataset on a county basis. For counties that did not provide these values, the national averages are applied.

The average consumption values for mining in the US are:
 - Fresh groundwater: 38%
 - Fresh surface water: 38%
 - Saline groundwater: 16%
 - Saline surface water: 16%

#### Water Discharge
Very few coal mines exist in coastal areas of the united states. Therefore, following in line with assumptions made in [Llnl SOURCE], 100% of water not consumed in the production of coal is
assumed to be discharged to the surface.

Discharge estimates for coal:
- Surface: 100%
- Ocean: 0%
- Ground: 0%

### Biomass

#### Water Withdrawal
biomass (estimated as described above) for all US counties, divided by the total production of biomass per day across all counties. This methodology provides a better ratio compared to the average intensity of each county individually given that some counties produce corn for ethanol but have no ethanol production while others have ethanol production but do not grow the corn locally.

Average intensity =  0.1465 million gallons per bbtu

Water type and source - Corn growth for ethanol is assumed to withdraw water from each type (fresh and saline) and source (groundwater and surface water) at the same ratio as all crop irrigation. This information is provided directly in Dieter et al. [SOURCE]. For counties where no data on crop irrigation is provided, water source and type to all irrigation is used instead.

The default values in the flow package for when water type and source are not provided on a regional level are equal to the US average values. These are:

Water types and water source:
 - Fresh groundwater: 54%
 - Fresh surface water: 44%
 - Saline groundwater: 0%
 - Saline surface water: 0%
 - Wastewater: 1%

#### Water Consumption/Evaporation
Water consumption estimates for corn growth for ethanol used in biomass are expected to follow the same consumption estimates for all crop irrigation. This information is provided directly in in Dieter et al. [SOURCE].

The average consumption values for ethanol growth for biomass in the US are:
 - Fresh groundwater: 77%
 - Fresh surface water: 77%

#### Water Discharge
Water discharge estimates for corn growth for ethanol used in biomass are expected to follow the same discharge estimates for all crop irrigation. All water discharged from crop irrigation is expected to be to the surface.

Discharge estimates for biomass (ethanol):
- Surface: 100%
- Ocean: 0%
- Ground: 0%


### Natural Gas

#### Water withdrawal
The average intensity of water use in unconventional natural gas drilling was determined by taking the total water to unconventional natural gas production in each county and dividing it by the total natural gas production per day in the same county. The average intensity value (million gallons per bbtu) was applied to counties that recorded unconventional natural gas production in 2015 but no water estimates were available for the same county. Note that this is a different average intensity calculation than what was determined for biomass given that water use in natural gas production is sourced onsite, whereas corn use in ethanol production can be sourced in an external location.

Average intensity = 0.0008 million gallons per bbtu

Water withdrawal type and source - It is assumed that 80% of water withdrawals by natural gas production are from fresh surface water sources and the remainder is from fresh groundwater sources following [SOURCE]. No saline water is assumed to be used in the production of natural gas. 0% of water flows to natural gas are assumed to come from wastewater reuse.

#### Produced Water
When water is injected into the ground for natural gas production, some water is produced. Water production fractions are provided in [SOURCE] for various states in gallons of water per mmcf of natural gas produced. This is converted to million gallons of water per bbtu and applied to unconventional natural gas production by county. It is assumed that the state value provided in [SOURCE] applies to each county in the state. For states without a value, the US average is supplied.

Natural gas average produced water intensity: 0.005342 mg/BBTU

#### Water Consumption/Evaporation
The same resource that provided produced water intensities for natural gas also supplied discharge percentages to surface, injection (ground), and consumption for each state. These estimates do not differentiate between natural gas and petroleum drilling. The assumption is made that these values are equivalent and are applied appropriately. For states without estimates, the national average is applied. This is also the default value for discharge and consumption in the flow package. Values provided by [SOURCE] split discharge and consumption evenly. For use within the flow package, these values must be applied separately. That is, consumption is an individual fraction and other discharges are fractions of the remaining water after consumption. The values provided in
[SOURCE] have been adjusted appropriately.

Average natural gas consumption fraction: 5%

#### Water Discharge:
Average natural gas discharge fractions (applied after consumption):
Injection (ground) Discharge = 95%
Surface Discharge = 5%

### Petroleum

#### Water Withdrawal
The average intensity of water use in unconventional petroleum drilling was determined through the same procedure as for natural gas. The only differentiating factor is that unconventional Petroleum production was used instead of total petroleum production given that data is available for conventional petroleum production water intensity.

Average unconventional petroleum water intensity = 0.0019 million gallons per bbtu

For conventional water intensity, gallon of water per gallon of oil estimates were provided by [SOURCE]. These values were used to determine the total US average water intensity for conventional oil production. The average value was applied to states that did not have water intensity values. The average value was taken by converting gallons of water per gallon of oil to mgal/bbtu
1 gal water = .0000001 mgal Water
1 gal oil = 0.0001355 bbtu

Average conventional Petroleum water intensity = 0.014984 million gallons per bbtu

Water withdrawal type and source - It is assumed that 80% of water withdrawals for petroleum production are from fresh surface water sources and the remainder is from fresh groundwater sources following [SOURCE]. No saline water is assumed to be used in the production of petroleum. 0% of water flows to natural gas are assumed to come from wastewater reuse.

#### Produced Water
Produced Water - Water produced during unconventional petroleum drilling is estimated in [SOURCE] for various states. These estimates are converted to mg per bbtu as with produced water from natural gas. For states with no produced water intensity estimate, the US average is applied. This also represents the default value in the flow package.

Petroleum average produced water intensity: 0.075540 mg/BBTU

#### Water Consumption
Consumption - Consumption estimates for petroleum follow the same as those as natural gas and are applied to all water (withdrawals + produced) in petroleum (conventional and unconventional)

Average petroleum consumption fraction: 5%

#### Water Discharge
Discharge - Discharge estimates for petroleum follow the same as those as natural gas and are applied to all water (withdrawals + produced) in petroleum (conventional and unconventional)

Average petroleum discharge fractions (applied after consumption):
Injection (ground) Discharge = 95%
Surface Discharge = 5%
