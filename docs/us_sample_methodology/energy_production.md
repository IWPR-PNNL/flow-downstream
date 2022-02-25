---
layout: default
title: Energy Production
parent: Methodology
grand_parent: US Sample Data Methodology
nav_order: 4
---

## Energy in Energy Production

The following energy production (fuel) types are included in the analysis:
- Natural gas
- Petroleum
- Coal
- Biomass

For all of the fuel production types above except coal production data by type is taken from US EIA SEDS state-level data for 2015 [8]. Data is provided in BBTU/yr. Information is provided at the state level and broken up based on various methodologies described in greater detail below.

MSN codes used from the EIA SEDS [8] dataset include:
- "PAPRB": Crude oil production (including lease condensate) (BBTU)
- "EMFDB": Biomass inputs (feedstock) to the production of fuel ethanol (BBTU)
- "NGMPB": Natural gas marketed production (BBTU)

Coal production data is provided in an alternative mine-level dataset [17] that allows us to aggregate production to the county level. This is discussed in greater detail later on this page.

Note that for energy sources that are not direct fuels (e.g., solar, nuclear), any production is directly consumed and values are captured in electricity production or fuel demand by end use sectors.

Various methods are used to break up state-level energy production values into county level values. These are described for each of the four fuel types below.

### County-level Coal Production

Coal production at the county level is provided from two separate datasets. The first dataset, US EIA E-7 [17], includes coal production data (tons), coal mine type (surface or underground), as well as the mine ID number for 2015. The Mine ID number provided in the US EIA dataset is used to map coal mine data to coal mine data provided by the US Department of Labor - Mine Safety and Health Administration [18]. The latter of these datasets includes the county FIPS codes for each Mine ID that is used to aggregate production to the county level. While information is provided for Refuse coal mines in addition to surface and underground mines, these mines are not included in this analysis.

Coal production for each mine type is provided in short tons per year. This is converted to bbtu where one short ton is equal to 0.02009 bbtu. Production values by mine type are aggregated to the county level.

### County-level Biomass Production

### County-level Natural Gas Production

### County-level Petroleum Production




## Water Withdrawals in Energy Production

Water in energy production is calculated for the following energy types:
- Coal (specifically, dust control in mining)
- Biomass (specifically, water used in corn growth for ethanol production and water use in the production of ethanol from corn grain)
- Natural gas (water used in drilling unconventional natural gas wells)
- Petroleum (water used in drilling both conventional and unconventional oil wells)

Each of these are described in more detail below

### Coal
#### Water withdrawal
To determine the amount of water used in the production of coal from each type of coal mine (surface vs. underground), the assumptions from Greenberg et al. [4] are used. Greenberg et al. [4] estimates that surface mines withdraw 7 gallons of water per ton of coal and underground mines withdraw 29 gallons per ton. To determine water source/type for mining dust control, it is assumed that the source of the water withdrawal for coal mining follows the same distribution of water use for other types of mining in the same county. For example, if 50% of water withdrawals for all mining in a county are estimated to come from fresh surface water, the same percentage is applied to coal mining. Water withdrawals for all mining types is provided in the USGS 2015 water use dataset [1].

Given that water withdrawals for coal mining are implicitly included in the water withdrawals for all mining in the USGS 2015 [1] dataset, the water withdrawals for coal mining are subtracted from the water withdrawals to all mining to avoid double counting. 


[CONTINUE HERE]




#### Water Consumption/Evaporation
Estimates for consumed water from coal mining follow the same consumption fractions as for all mining water consumed. These values are not available in the 2015 dataset and are instead calculated from the 1995 USGS dataset on a county basis.

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
