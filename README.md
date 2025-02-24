[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/IAASVEAZ)
# CSIT5970 Assignment-1: EC2 Measurement (2 questions, 4 marks)

### Deadline: 11:59PM, Feb, 28, Friday

---

### Name: Tong Shuyao
### Student Id: 21136668
### Email: stongaa@connect.ust.hk

---

## Question 1: Measure the EC2 CPU and Memory performance

1. (1 mark) Report the name of measurement tool used in your measurements (you are free to choose *any* open source measurement software as long as it can measure CPU and memory performance). Please describe your configuration of the measurement tool, and explain why you set such a value for each parameter. Explain what the values obtained from measurement results represent (e.g., the value of your measurement result can be the execution time for a scientific computing task, a score given by the measurement tools or something else).

    > The measurement tool I chose is the Phoronix Test Suite.
    > 
    > To measure CPU performance, I configured PTS with the 7-Zip Compression Benchmark, and the default settings were used, which include multi-threaded compression and decompression workloads to stress the CPU. To measure memory performance, I configured PTS with the RAMspeed Benchmark, and used the "copy" test measures memory bandwidth for copying data, and the "integer" test measures memory bandwidth for integer operations.
    > 
    > The CPU performance measurement results will include a compression rating and a decompression rating, both reported in MIPS, which represents the CPU's processing speed. The memory performance measurement results will include memory bandwidth for the "copy" and "integer" tests, reported in MB/s.

2. (1 mark) Run your measurement tool on general purpose `t2.micro`, `t2.medium`, and `c5d.large` Linux instances, respectively, and find the performance differences among these instances. Launch all the instances in the **US East (N. Virginia)** region. Does the performance of EC2 instances increase commensurate with the increase of the number of vCPUs and memory resource?

    In order to answer this question, you need to complete the following table by filling out blanks with the measurement results corresponding to each instance type.

    | Size        | CPU performance | Memory performance |
    | ----------- | --------------- | ------------------ |
    | `t2.micro` ||                    |
    | `t2.medium`  ||Average: 19383.35 MB/s|
    | `c5d.large` |                 |                    |

    > Region: US East (N. Virginia). Use `Ubuntu Server 22.04 LTS (HVM)` as AMI.

## Question 2: Measure the EC2 Network performance

1. (1 mark) The metrics of network performance include **TCP bandwidth** and **round-trip time (RTT)**. Within the same region, what network performance is experienced between instances of the same type and different types? In order to answer this question, you need to complete the following table.

    | Type                      | TCP b/w (Mbps) | RTT (ms) |
    | ------------------------- | -------------- | -------- |
    | `t3.medium` - `t3.medium` |3.95 Gbits/sec  |0.281     |
    | `m5.large` - `m5.large`   |     4.95 Gbits/sec           |     0.244      |
    | `c5n.large` - `c5n.large` |     4.95 Gbits/sec           |    0.236 ms
      |
    | `t3.medium` - `c5n.large` | 2.12 Gbits/sec               |   0.823       |
    | `m5.large` - `c5n.large`  | 2.76 Gbits/sec               |     0.680     |
    | `m5.large` - `t3.medium`  |4.57 Gbits/sec                |    0.243      |

    > Region: US East (N. Virginia). Use `Ubuntu Server 22.04 LTS (HVM)` as AMI. Note: Use private IP address when using iPerf within the same region. You'll need iPerf for measuring TCP bandwidth and Ping for measuring Round-Trip time.

2. (1 mark) What about the network performance for instances deployed in different regions? In order to answer this question, you need to complete the following table.

    | Connection                | TCP b/w (Mbps) | RTT (ms) |
    | ------------------------- | -------------- | -------- |
    | N. Virginia - Oregon      |                |          |
    | N. Virginia - N. Virginia |                |          |
    | Oregon - Oregon           |                |          |
 
    > Region: US East (N. Virginia), US West (Oregon). Use `Ubuntu Server 22.04 LTS (HVM)` as AMI. All instances are `c5.large`. Note: Use public IP address when using iPerf within the same region.
