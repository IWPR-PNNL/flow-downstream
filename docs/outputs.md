---
layout: default
title: Model Outputs
parent: User Guide
nav_order: 4
---

# Key Outputs

## Data Output

**flow** returns a Pandas DataFrame when calling calculate(). The DataFrame
contains the following for each flow value for each region included in the input data when the level parameter is set to 5:

| Column Name | Description                               | Type  |
|:------------|:------------------------------------------|:------|
| region      | Name of region                            | str   |
| S1          | Level 1 source node name                  | str   |
| S2          | Level 2 source node name                  | str   |
| S3          | Level 3 source node name                  | str   |
| S4          | Level 4 source node name                  | str   |
| S5          | Level 5 source node name                  | str   |
| T1          | Level 1 target node name                  | str   |
| T2          | Level 2 target node name                  | str   |
| T3          | Level 3 target node name                  | str   |
| T4          | Level 4 target node name                  | str   |
| T5          | Level 5 target node name                  | str   |
| units       | unit type for value                       | str   |
| value       | value of flow connecting source to target | flt   |

Note that setting the level parameter equal to a value less than 5 will reduce the output accordingly to only show the appropriate levels, aggregated to the level specified. For example, specifying level 1 will return the following DataFrame instead.

| Column Name | Description                               | Type  |
|:------------|:------------------------------------------|:------|
| region      | Name of region                            | str   |
| S1          | Level 1 source node name                  | str   |
| T1          | Level 1 target node name                  | str   |
| units       | unit type for value                       | str   |
| value       | value of flow connecting source to target | flt   |

## Visualizations

In addition to the Pandas DataFrame output, a variety of vizualization and analysis functions are pre-built into the flow package and can be used to interpret results. These include the following:

### Single-unit sankey diagrams

Sankey diagrams are used to visualize flows from source nodes to target nodes where links between nodes have variable width depending on the value of the flow. The 'flow.plot_sankey()' function plots up to two sankey diagrams (one for each unit specified) based on the run output that is provided to the function. Users can specify a level of granularity to show flows from level 1 (major sector aggregates only) to level 5 (the highest level of granularity available). For more information on the specific function paramaters, defaults, and other components, see the function_guide section.

![sankey_example](https://user-images.githubusercontent.com/74064300/157076964-e8a902e2-30c4-45a1-b860-f0660c68795e.png)


### Single region stacked barcharts of sectors

![image](https://user-images.githubusercontent.com/74064300/157077416-13e7191e-bd2c-4744-8407-32cc8f91889b.png)

![image](https://user-images.githubusercontent.com/74064300/157079185-d433d9f6-c6c1-4fd2-8bf9-98e95b995e44.png)


### Cloropleth map displaying single flow values across regions

![image](https://user-images.githubusercontent.com/74064300/157077774-28f4ea72-6c4e-49fc-869d-bf878d91b092.png)
