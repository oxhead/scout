# Description

This dataset includes more than 100 workloads runnings 18 VM types.  Each workload is run three times.

## AWS EC2 VM Types
* c4.large, c4.xlarge, c4.2xlarge
* c3.large, c3.xlarge, c3.2xlarge
* m4.large, m4.xlarge, m4.2xlarge
* m3.large, m3.xlarge, m3.2xlarge
* r4.large, r4.xlarge, r4.2xlarge
* r3.large, r3.xlarge, r3.2xlarge

## Workloads
For each application, we use three different inputs—either data inputs or input parameters.  Since some workloads cannot complete on some of the VM types, we totally have 107 workloads with full performance data on 18 VM types.  The other workloads are also included in this dataset.

## Dataset Formation
Each record id is encoded by its configuration and workload.  Taken 
```
r4.xlarge_i-0f4e4b248a6aa957a_terasort_spark_small_1
```
for example, it represents

* r4.xlarge
* terasort on Spark 2.1
* input is small
* the first run (3 runs in this dataset)

Others follows the same rule.

## Data Record
Each data record contains a execution result (report.json) and a history of low-level performance information (sar.csv).  An example execution result is
```
{
    "completed": true,
    "datasize": "small",
    "elapsed_time": "119.742",
    "framework": "spark",
    "input_size": "3200000000",
    "program": "ScalaSparkTerasort",
    "throughput_cluster": "26724123",
    "throughput_node": "26724123",
    "timestamp": "2017-09-24 14:05:47",
    "workload": "terasort"
}
```
The main fields are the *elapsed_time* and *completed*.  The output of low-level metrics has a timestamp and 72 metrics.
* timestamp
* cpu.[%usr, %nice, %sys, %iowait, %steal, %irq, %soft, %guest, %gnice, %idle]
* task.[proc/s, cswch/s]
* intr.intr/s
* swap.[pswpin/s, pswpout/s]
* paging.[pgpgin/s, pgpgout/s, fault/s, majflt/s, pgfree/s, pgscank/s, pgscand/s, pgsteal/s, %vmeff]
* io.[tps, rtps, wtps, bread/s, bwrtn/s]
* memory.[kbmemfree, kbavail, kbmemused, %memused, kbbuffers, kbcached, kbcommit, %commit, kbactive, kbinact, kbdirty, kbanonpg, kbslab, kbkstack, kbpgtbl, kbvmused]
* swap.[kbswpfree, kbswpused, %swpused, kbswpcad, %swpcad]
* load.[runq-sz, plist-sz,ldavg-1, ldavg-5, ldavg-15, blocked]
* disk.[tps, rd_sec/s wr_sec/s, avgrq-sz, avgqu-sz, await, svctm, .%util]
* network.[rxpck/s, txpck/s, rxkB/s, txkB/s, rxcmp/s, txcmp/s, rxmcst/s, %ifutil]

```
timestamp,cpu.%usr,cpu.%nice,cpu.%sys,cpu.%iowait,cpu.%steal,cpu.%irq,cpu.%soft,cpu.%guest,cpu.%gnice,cpu.%idle,task.proc/s,task.cswch/s,intr.intr/s,swap.pswpin/s,swap.pswpout/s,paging.pgpgin/s,paging.pgpgout/s,paging.fault/s,paging.majflt/s,paging.pgfree/s,paging.pgscank/s,paging.pgscand/s,paging.pgsteal/s,paging.%vmeff,io.tps,io.rtps,io.wtps,io.bread/s,io.bwrtn/s,memory.kbmemfree,memory.kbavail,memory.kbmemused,memory.%memused,memory.kbbuffers,memory.kbcached,memory.kbcommit,memory.%commit,memory.kbactive,memory.kbinact,memory.kbdirty,memory.kbanonpg,memory.kbslab,memory.kbkstack,memory.kbpgtbl,memory.kbvmused,swap.kbswpfree,swap.kbswpused,swap.%swpused,swap.kbswpcad,swap.%swpcad,load.runq-sz,load.plist-sz,load.ldavg-1,load.ldavg-5,load.ldavg-15,load.blocked,disk.tps,disk.rd_sec/s,disk.wr_sec/s,disk.avgrq-sz,disk.avgqu-sz,disk.await,disk.svctm,disk.%util,network.rxpck/s,network.txpck/s,network.rxkB/s,network.txkB/s,network.rxcmp/s,network.txcmp/s,network.rxmcst/s,network.%ifutil
```


## How data is collected?
We run the sar tool in the background with a sampling interval of 5 seconds.

```
sar -p -A -o /tmp/sar.dat 5
```

After a workload completes, we run sadf to export the necessary output to derive the sar.csv.