# Introduction
With cloud computing, users are able to tune cloud configurations to meet their performance or cost objectives.  In our research project, we aim to find out the best cloud configuration for a given workload and a give objective.  During our research, we found performance data is very hard to find—at least, we could not find performance that suits our needs.  We instead collected the required data.  This data repository is the effort.  We make this data available to encourage research advance in cloud performance optimization.


This data repository includes large-scale performance data of Hadoop and Spark applications on AWS EC2.  Since performance varies with different inputs, our data includes multiple combinations of applications and inputs.  We use workload to describe an application and its input.  The workloads are extracted from [HiBench](https://github.com/intel-hadoop/HiBench) and [spark-perf](https://github.com/databricks/spark-perf).

We ran these workloads on numerous cloud configuration on Amazon EC2.  Each configuration is composed of a virtual machine (VM) type and a number of the same VMs.  This data repository includes both the single-node setting and the multi-node setting.  The single-node setting includes 18 VM types and the multi-node setting includes 69 configurations (9 VM types and various numbers of VMs).

For each measurement, we collect its execution time and also its low-level performance information using [sar](https://linux.die.net/man/1/sar). For more detail, read the description of each dataset.


# Dataset Overview

| ID                 | Platforms | Systems                          | Workloads | Description                                                     |
|--------------------|----------|----------------------------------|-----------|-----------------------------------------------------------------|
| [osr_single_node](dataset/osr_single_node.md)    | AWS EC2  | <ul><li>Hadoop 2.7</li><li>Spark 2.1</li><li>Spark 1.5</li></ul> | <ul><li>sort</li><li>terasort</li><li>pagerank</li><li>workcount</li><li>aggregation</li><li>join</li><li>scan</li><li>chi-feature</li><li>chi-gof</li><li>chi-mat</li><li>spearman</li><li>statistics-summary</li><li>pearson</li><li>svd</li><li>pca</li><li>word2vec</li><li>classification</li><li>regression</li><li>als</li><li>naive-bayes</li><li>lr</li><li>mm</li><li>decision tree</li><li>gradient boosted tree</li><li>random forest</li><li>fp-growth</li><li>gmm</li><li>kmeans</li><li>lda</li><li>pic</li></ul>          | Multiple workloads running on a single-node setting on AWS      |
| [osr_multiple_nodes](dataset/osr_multiple_nodes.md) | AWS EC2  | <ul><li>Hadoop 2.7</li><li>Spark 2.1</li><li>Spark 1.5</li></ul> | <ul><li>terasort</li><li>pagerank</li><li>wordcount</li><li>join</li><li>lr</li><li>kmeans</li><li>naive-bayes</li><li>regression</li></ul>          | Multiple workloads running on the multiple-nodes setting on AWS |

# How to Contribute
* We encourage researchers share their performance data.  Please submit a pull request.
* You can obtain the scripts and required AMI at the [scout-scripts repo](https://github.com/oxhead/scout-scripts).



# How to Cite

```
@inproceedings{hsu2018arrow,
  title={Arrow: Low-Level Augmented Bayesian Optimization for Finding the Best Cloud VM},
  author={Hsu, Chin-Jung and Nair, Vivek and Freeh, Vincent W and Menzies, Tim},
  booktitle={the 2018 IEEE 38th International Conference on Distributed Computing Systems (ICDCS 2018)},
  year={2018}
}
@inproceedings{hsu2018micky,
  title={Micky: A Cheaper Alternative for Selecting Cloud Instances},
  author={Hsu, Chin-Jung and Nair, Vivek and Menzies, Tim and Freeh, Vincent},
  booktitle={the IEEE International Conference on Cloud Computing (IEEE CLOUD 2018)}
  year={2018}
}
@article{hsu2018scout,
  title={Scout: An Experienced Guide to Find the Best Cloud Configuration},
  author={Hsu, Chin-Jung and Nair, Vivek and Menzies, Tim and Freeh, Vincent},
  journal={arXiv preprint arXiv:1803.01296},
  year={2018}
}
```
