---
layout: default
title: Model Outputs
parent: User Guide
nav_order: 3
---

# Key Outputs

**flow** returns a Pandas DataFrame when calling run(). The DataFrame
contains the following for each flow value for each region included in the input data:

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
