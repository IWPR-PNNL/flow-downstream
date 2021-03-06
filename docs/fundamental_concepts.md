---
layout: default
title: Fundamental Concepts
parent: User Guide
nav_order: 1
---


# Fundamental Concepts

## Basic Methodology

At its most basic level **flow** collects input values connecting two sectors in specified units (e.g., water delivered to the agriculture sector),
calculates additional sector flows in alternative units based on intensity factors (e.g., energy demand based on water delivered to the agriculture sector),
and builds connections to and from additional sectors to carry those values (e.g., electricity sector connected to agriculture sector to deliver the energy)

**flow** goes through the following steps in completing calculations:

1. Collects a Unit 1 "flow" value connecting Node A to Node B
2. Calculates a Unit 2 value associated with Node B based on a provided Unit 2 per Unit 1 intensity factor for Node B.
3. Builds a Unit 2 flow value from Node C to Node B as a "source" flow based on the provided fraction of the calculated Unit2 value assumed to come from Node C.
4. Builds a flow value from Node B to Node D to "discharge" the estimated value based on the provided fraction of the calculated value assumed to go to Node D.

This process is repeated for all nodal relationships within each region provided in the input data.

A real-world example of the above would be:

1. The total gallons of water withdrawn from the water supply (Node A) and delivered to the public water supply (Node B) is 100 gallons.
2. The energy required to withdraw a gallon of water from the water supply (Node A) by the public water supply sector (Node B) is
5 british thermal units (btu) per gallon. This calculates out to 500 btu in total based on the initial flow value.
3. The fraction of energy used in the public water supply sector that is supplied by the electricity sector (Node C) is estimated to be 100%. Therefore,
the energy flow value connecting the electricity sector (Node C) to the public water supply sector (Node B) is 500 btu.
4. The fraction of energy used in the public water supply sector (Node B) that is lost to rejected energy (efficiency losses) is 35%.
Therefore, the energy flow value connecting the public water supply sector (Node B) and the rejected energy node (Node D) is 0.35*500 = 175 btu.

The diagram below shows each of these steps.

![image](https://user-images.githubusercontent.com/74064300/153686911-fd0ec47d-571d-455c-bde8-e8b05a13bac0.png)

Note that **flow** does not require node inputs and outputs to be balanced. That is to say, inflows to a node do not have to equal outflows as demonstrated above with only 35% of the energy inflow calculated for public water supply being discharged.

Additionally, while the capability is provided to calculate alternate-unit flows (step 2 above) from input values, this is not a requirement. That is to say, a
user could simply provide flow values connecting various nodes in step 1 and the model will simply return those flows unless told to do otherwise.

The example walked through above is a high level example of the flow process that demonstrates what is referred to in this documentation as "level 1" granularity.
**flow** is capable of calculating and handling sectors up to five levels of granularity. To equate that to the previous example, a level 1 sector would be the
public water supply sector. Level 2 and beyond splits up the level 1 sector into subsectors, sub-subsectors, and so on. An example of a level 2 granularity using
the above example would be Water Supply - Fresh (i.e., the portion of the total Water Supply sector that is fresh water as opposed to saline water).

Up to five levels of granularity can be specified for each node. Various examples of level 5 granularity include the following:

| Level 1                | Level 2     | Level 3        | Level 4                      | Level 5                |
|:-----------------------|:------------|:---------------|:-----------------------------|:-----------------------|
| Electricity Generation | Natural Gas | Combined Cycle | Carbon Capture Sequestration | Recirculating Cooling  |
| Electricity Generation | Natural Gas | Combined Cycle | Carbon Capture Sequestration | Once Through Cooling   |
| Water Supply           | Fresh       | Surface Water  | Lake                         | Lake Michigan          |

Note that, while the input data allows up to five levels of granularity for each node, granularity can differ across input sectors. For example, a flow from Water Supply -Fresh - Surface water
(a level 3 node) can be calculated to total public water supply (a level 1 node).

![image](https://user-images.githubusercontent.com/74064300/153687016-10d17859-55f5-443c-aeda-4ed3ab2f199d.png)

More information on generalizability and input data format requirements can be found in the generalizability section.

## Aggregation and Output Granularity

While highly granular data can provide significant insight into the finer details of a sector, big picture relationships can also be informative. As **flow**
loops through the provided sectors as the various levels of granularity and builds connections, it also tracks sums for each level of granularity so that
a level of output granularity can be specified when the model is run. For example, if **flow** calculates energy demand in the public water supply sector for
public water supply treatment and public water supply distribution, it will simultaneously be calculating total energy in the public water supply (i.e., their sum).

This aggregation is done based off of both initial input values and calculated values. For example, if electricity delivery to the residential sector is provided
as input data, but natural gas delivery to the residential sector is later calculated based on intensity factors, the energy delivered to the residential sector (level 1 granularity)
will sum both.
