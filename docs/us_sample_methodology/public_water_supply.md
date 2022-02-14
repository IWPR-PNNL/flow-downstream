---
layout: default
title: Public Water Supply
parent: Methodology
grand_parent: US Sample Data Methodology
nav_order: 3
---

## Navigation
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

## Water in Public Water Supply

### Water Withdrawals/Deliveries
Water withdrawals to public water supply are provided by US Geological Survey (USGS) (Dieter et al. [1]) and are provided in million gallons per day (mgd) for each county. Public supply is defined as "water withdrawn by public and private water suppliers that provide water to at least 25 people or have a minimum of 15 connections." Public supply withdrawals include fresh/saline and surface/ groundwater.

### Water Supply Imports (Interbasin transfers)
Interbasin transfer flows and energy intensities in each county are provided through data from two sources. For western states, county-level water flows were available from Tidwell et al. [2]. For the state of Texas, county-level interbasin transfers between specified counties were collected from the Texas Water Development Board [3]. No data is currently available for interbasin transfers in eastern US counties. For these counties, the value is assumed to be zero.

Interbasin transfers are used for both public water supply as well as for irrigation purposes. To determine how much of the total interbasin transfer flows in each county goes to crop irrigation versus public water supply, the methodology from Greenberg et al. [4] is adapted which uses the ratio of water flows to crop irrigation vs. public water supply to split the values. The ratio is determined by taking the ratio of all water withdrawals to crop irrigation (Fresh surface water and fresh groundwater) over the sum of all water withdrawals to crop irrigation and water withdrawals by the public water supply from Dieter et al. [1]. This determines the percent of total flows to both sectors that goes to crop irrigation. This fraction is multiplied by the total interbasin transfer flow to determine how much of the interbasin transfer flow goes to crop irrigation. Any interbasin transfer flow that does not go to crop irrigation is assumed to go to the public water supply. It should be noted that interbasin transfers are only assumed to go to crop irrigation and are not used for other agricultural applications such as golf irrigation or livestock.

#### Texas interbasin transfer Methodology

To calculate the total interbasin transfer flows in each texas county, the total intake in acre-feet per year was converted to meters per second cubed (1 acre-ft = 25,568 mps^3). The cubic meters per second was then converted to million gallons per day (1 mps^3 = 22.82 mgd). Each value in the Texas interbasin transfer data is associated with two counties (source and target county). Given a lack of more detailed data, it is assumed that half of the water flow and half of the subsequent energy required is split evenly between the two counties.

#### Western States interbasin transfer Methodology

Interbasin transfer flows were available for the states of Idaho, California, Arizona, Utah, Washington, Nevada, Colorado, Oregon, Montana, New Mexico, and Wyoming. Most rows in the dataset provided water flow values on a cubic feet per second basis, which were converted to mgd (1 cfs = 0.646317 mgd). For rows that did not provide cfs, acre-ft per year were provided and converted to mgd using the same methodology as the Texas calculation described above.


### Water Discharges/Consumption
### Water Consumption/Evaporation
Public water supply is not assumed to have any consumption or evaporation values.

### Water Discharges
It is assumed that all water in public water supply is either send to public water demand (and onward to residential, commercial, and industrial end users) or it is sent to exports (i.e., exported to another county). The total amount of water that is sent to public water demand is assumed to be equal to the sum of public water demand to residential, commercial, and industrial sectors (see the respective Residential, Commercial, and Industrial methodology sections for more information on these flows). Taking the total water in public water supply (including both withdrawals and interbasin transfer deliveries) and substracting the total public water demand allows us to determine the total public water export in each county. In counties where the total public water supply is less than or equal to the total public water demand, the amount of exports is equal to zero. Following this methodology, if the total public water demand is greater than the total public water supply in a county, the difference established the total public water demand that is imported from another county.

## Energy in Public Water Supply

### Energy Demand

Energy use in public water supply is determined by coefficients for energy intensity in surface water withdrawal, groundwater withdrawal intensity, surface water treatment intensity, groundwater treatment intensity, distribution intensity to end-users, and interbasin transfer pumping intensity. It is assumed that all energy used in the public water supply sector is supplied by electricity.

#### Pumping

USDA's Farm and Ranch Irrigation Survey (FRIS) [5] provides state-by-state data on irrigation groundwater depth and average irrigation pressurization levels for irrigation within a state, enabling the calculation of pump electricity consumption for both groundwater and surface water pumping. The 2013 survey is the closest year available to 2015 values. It is assumed that values do not vary significantly between the two years.

The methodology for calculating groundwater and surface water pumping energy is described in Tidwell et al [2]. However, where that publication uses well depth to water to calculate total differential height, the total well depth is used here as a way to offset some of the losses due to friction that would occur in the piping, as described in Lawrence Berkeley National Laboratory (LBNL) Home Energy Saver & Score: Engineering Documentation [6]. Pump efficiency is assumed to be the average (46.5%) of the range (34-59%) listed in [2]. State-level intensity rates are calculated here and applied to the county level water in public water supply values.


The groundwater pumping intensity is calculated through the following:

'ACC_GRAVITY = 9.81  # Acceleration of gravity  (m/s^2)
WATER_DENSITY = 997  # Water density (kg/m^3)
PUMP_EFF = .465  # assumed pump efficiency rate
PSI_PSF_CONVERSION = 2.31  # conversion of pounds per square inch (psi) to pounds per square foot (psf)
CUBIC_METERS_MG_CONVERSION = 3785.41178  # conversion factor for m^3 to million gallons
JOULES_KWH_CONVERSION = 1 / 3600000  # conversion factor from joules to kWh
KWH_BBTU_CONVERSION = 3412.1416416 / 1000000000  # 1 kWh is equal to 3412.1416416 btu
METERS_FT_CONVERSION = 0.3048  # meters in a foot'

'head_ft = PSI_PSF_CONVERSION * average_operating_pressure_psi  # conversion of psi to head (pounds per sqft)
diff_height_gw = METERS_FT_CONVERSION * (average_well_depth_ft + head_ft)  # calc. differential height (m)
pump_power_gw = (water_density * diff_height_gw * ACC_GRAVITY * CUBIC_METERS_MG_CONVERSION) / PUMP_EFF  # joules/MG
groundwater_pumping_bbtu_per_mg = pump_power_gw * JOULES_KWH_CONVERSION * KWH_BBTU_CONVERSION  # power intensity (bbtu/mg)'


For surface water pumping, the average well depth is set to zero.

#### Treatment

The energy intensity for public water supply treatment for fresh water is provided in Greenberg et al. [4]. Estimates for desalination (saline water treatment) are provided by Tidwell et al. [2].

Fresh surface water treatment = 405 kWh/mg
Fresh groundwater treatment = 205 kWh/mg
saline surface water treatment = 12,000 kWh/mg
saline groundwater treatment = 12,000 kWh/mg

All values are converted to bbtu/mgd.

#### Distribution

The energy intensity for public water supply distribution is provided in Greenberg et al. [4] as 1040 kWh/mg. This value is converted to bbtu/mgd.

#### Interbasin-transfers

The energy intensity required for interbasin transfers was calculated on a per-county basis from values provided in Tidwell et al. [2] and the Texas Water Development Board [3].

##### Texas interbasin transfer energy intensity

Information provided in Tidwell et al. [2] includes the elevation difference (ft) between the two counties that are passing water. With this information, along with the estimated pumping efficiency per county, the energy required to transfer each mgd can be calculated.

The total mwh per mgd is calculated as:

 energy_mwh = ((elevation_meters * mps_cubed * acc_gravity * water_density) / pump_eff) / (10 ** 6)

where,
elevation_meters = elevation difference between the two counties in meters
mps_cubed = the water flow value in meters per second cubed
acc_gravity = the acceleration due to gravity (9.81 m/sec^2)
water_density = the density of water (997 kg/m^3)
pump_eff = assumed pumping efficiency

This value is converted to bbtu and divided in half to split between the source and target counties (to follow the same methodology as the interbasin water transfer value described previously on this page). The total energy in interbasin transfer is divided by the total interbasin water flow in each county to get the energy intensity per county.

### Energy Services

The public water supply sector is assumed to have an efficiency level of 65%, following the assumption made in Greenberg et al. [4]. Therefore, 65% of all energy demand by the public water suppy sector is assumed to go to energy services.

### Rejected Energy

Given the assumed efficiency level of 65%, 35% of all energy in the public water supply sector is assumed to go to rejected energy.
