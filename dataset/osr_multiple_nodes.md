# Description

This dataset includes 18 workloads runnings 69 configurations.  Each workload has only one measurement.

## AWS EC2 VM Types
* {4, 6, 8, 10, 12, 16, 20, 24, 32, 40, 48} x {c4.large, m4.large, r4.large}
* {4, 6, 8, 10, 12, 16, 20, 24} x {c4.xlarge, m4.xlarge, r4.xlarge}
* {4, 6, 8, 10, 12} x {c4.2xlarge, m4.2xlarge, r4.2xlarge}


## Workloads
For each application, we use two different inputs—either data inputs or input parameters.  This dataset includes a full measurements—both execution time and low-level performance metrics.  Since some configurations may run too long, we use a 2-hour timeout.

## Dataset Formation
Each record id is encoded by its configuration and workload.  Taken 
```
4_m4.2xlarge_naive-bayes_spark1.5_bigdata_1
```
for example, it represents

* 4 x m4.2xlarge
* naive-bayes on Spark 1.5
* input is bigdata
* the first run (only 1 run in this dataset)

Others follows the same rule.

## Data Record
The record structure is similar to [osr_single_node](osr_single_node.md). However, since this dataset is for the multi-node setting, it contains low-level performance metrics from multiple nodes.  We use

```
sar_node[x].csv
```
to represent the low-level data collected from distributed nodes.
