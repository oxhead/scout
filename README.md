# scout
Large-scale performance data of Hadoop and Spark on AWS


# Dataset Overview

| ID                 | Platforms | Systems                          | Workloads | Description                                                     |
|--------------------|----------|----------------------------------|-----------|-----------------------------------------------------------------|
| osr_single_node    | AWS EC2  | <ul><li>Hadoop 2.7</li><li>Spark 2.1</li><li>Spark 1.5</li></ul> | <ul><li>sort</li><li>terasort</li><li>pagerank</li><li>workcount</li><li>aggregation</li><li>join</li><li>scan</li><li>chi-feature</li><li>chi-gof</li><li>chi-mat</li><li>spearman</li><li>statistics-summary</li><li>pearson</li><li>svd</li><li>pca</li><li>word2vec</li><li>classification</li><li>regression</li><li>als</li><li>naive-bayes</li><li>lr</li><li>mm</li><li>decision tree</li><li>gradient boosted tree</li><li>random forest</li><li>fp-growth</li><li>gmm</li><li>kmeans</li><li>lda</li><li>pic</li></ul>          | Multiple workloads running on a single-node setting on AWS      |
| osr_multiple_nodes | AWS EC2  | <ul><li>Hadoop 2.7</li><li>Spark 2.1</li><li>Spark 1.5</li></ul> | <ul><li>terasort</li><li>pagerank</li><li>wordcount</li><li>join</li><li>lr</li><li>kmeans</li><li>naive-bayes</li><li>regression</li></ul>          | Multiple workloads running on the multiple-nodes setting on AWS |
