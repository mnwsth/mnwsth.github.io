---
layout: page
title: Research
use-site-title: true
---

### Research Interests
I am primarily interested in issues related to memory and storage design. 
In the recent past, my work has revolved around multiple aspects of system 
design - from workload characterization, all the way up to proposing and 
evaluating system-level architectures, with focus on memory and storage 
sub-system design. Currently, I am interested in the following broad 
research themes.

* Heterogeneous main memory architectures for smartphones and servers
* Storage system design and optimization, including the system software stack
* Workload characterization of emerging applications, across the entire spectrum of computing devices

In the past, I have looked at memory hierarchy design for Chip Multi Processors (CMPs), at all levels of the hierarchy. More specifically, the techniques to efficiently manage data and capacity in large, last-level caches and multi-socket, single-board NUMA main memories. I have also proposed techniques to manage resistance drift in phase-change memory (PCM) multi-level cells (MLCs), reduce timing and thermal issues in 3D stacked clustered architectures and designed commit algorithms for hardware transactional memory architectures.

### Research Projects
#### **1. Non Volatile Memory Architectures**
The increase in the amount of data to be processed with increasingly strict 
latency requirements has made the architecture of main memory a renewed focus 
area. The main memory, especially on enterprise or datacenter servers is expected 
to have high bandwidth, large capacity, low
latency and low energy consumption. Many of these are contradictory design 
objectives, and cannot be met only by DRAM, or it's descendants. However, the 
advent of new memory technologies has made it possible to design architectures
that can provide *most* of the above requirements. These include emergence of 
non-volatile memory technologies (NVM) like Phase Change Memory (PCM) and Spin 
Torque Transfer Memory (STT-RAM), which are being touted as potential
replacements for DRAM as main memory. 3D stacking of DRAM, which has also 
been made economically feasible recently has also led to solutions like 
High Bandwidth Memory (HBM), and has the potential to be applied to NVMs as well.
Despite the availability of architectural possibilities, there is little 
consensus on which combination of technologies 
will result in architectures that are best suited for a set of workloads.
In this project, we are exploring multiple ways to design better
memory hierarchies using a combination of NVMs, traditional architectural 
optimizations, as well as using novel high performance, energy efficient 
memory cells for use in caches and main memory.

##### 1.1 Prefetcher Designs for Hybrid Memory Architectures
Hybrid main memory hierarchies are being designed by using a combination of DRAM 
and an NVM. Typical designs are either splitting the 
memory address across two or more memory technologies, or using a faster 
technology with higher lifetimes, typically the DRAM, as a cache for the higher 
capacity, albeit slower main memory made up of a NVM.

Design of such hybrid architectures remains an active area of research from the perspective of DRAM-as-a-cache design, since DRAM could quickly become the bottleneck, as cache lookups require multiple accesses for reading tag and data. In this work, we are exploring if augmenting the DRAM-as-a-cache model with a novel DRAM cache prefetcher which builds on state of the art Alloy Cache could yield performance benefits. The new DRAM cache architecture allows for prefetching data at both cacheline and page granularities from the NVM, and as a result, provides upto a maximum of 2× performance improvement over a state of the art baseline. (<a href="/pubs/hotstorage2020.pdf">HotStorage '20</a>)

##### 1.2 Hybrid On-Chip Memory Hierachies
In this project, we are exploring a “full-stack” solution to designing high
capacity and low latency on-chip cache hierarchies by starting at
the circuit level of the hardware design stack. We have designed a
novel Gain Cell (GC) using FDSOI. The GC has several
desirable characteristics, including ~50% higher storage density
and ~50% lower dynamic energy as compared to the traditional
6T SRAM, even after accounting for peripheral circuit overheads.

We believe that compared to 6T SRAM, for a
given area budget, GC based caches will provide large gains in IPC 
as well as energy consumption for single- and multi-programmed workloads,
respectively, which is being substantiated by our initial results as well.

#### **2. Workload Characterization and Tool Development**
To design efficient architectures for the future, we must first understand 
the behavior of *emerging* applications on *contemporary* architectures. 
Both parts of the equation are equally important to address. If we 
do not study contemporary (let alone emerging) applications, the chances
are that architectures designed using these applications as benchmarks
will not be optimized for future workloads in the best case, or will be 
optimized for workloads that are quickly becoming extinct in the worst. 
Similarly, studying emerging workloads on near obsolescence architectures 
fails to reveal system bottlenecks for these workloads. 


Workload characterization is a great way to understand the 
behavior of contemporary applications, and narrow down the sources of 
inefficiencies and performance bottlenecks in contemporary architectures. 
This provides us with a set of problems that are worth solving in system
design in the near term, as well as provides insights into issues that 
*might* become bottlenecks for emerging applications. In this project, 
carry out workload characterization of emerging applications with a 
focus on revealing performance bottlenecks in memory and storage systems. 


As a part of this project, we have carried out extensive characterization of the 
SPEC 2017 CPU suite to understand its memory behavior.
We have also explored if statistical sampling techniques like SimPoint 
remain effective for contemporary workloads. In this project, we observed that for cases like memory hierarchy explorations, SimPoints should 
be used judiciously and with extreme caution in order to derive correct conclusions – inappropriately chosen SimPoint configurations can show large deviations in memory hierarchy behavior as compared to full runs, as reported by prior studies. We have also studied performance bottlenecks in Android, and 
are currently researching bottlenecks in ML applications using MLPerf. (<a href="/pubs/bench2021.pdf">Bench '21</a>, <a href="/pubs/icpe2019b.pdf">ICPE '19</a>, <a href="/pubs/iiswc2019.pdf">IISWC '19</a>)

#### **3. In Memory Compute Architectures**
Applications which process extremely large data sets, require large scale movement 
of data across multiple levels of the memory hierarchy. First, from storage to
 main memory, and from there to on-chip caches. Finally, the cached data is moved
 to the CPU registers, where it can be processed. By most estimates, this 
 data movement incurs large latency and consumes a significant amount of 
 energy. Not only that, it causes applications to be bottlenecked by the 
 memory and storage hierarchy. As a result, the need of the hour is for 
 innovations in system design along two major axes. First, the memory and storage
  hierarchies of existing architectures have to be strengthened to reduce 
  the energy and latency cost of data movement. In parallel, we have to 
  devise architectures that consider data, and not instructions as first 
  class components of computer system design. This would require a diversion 
  from the traditional von-Neumann computing model and move instructions 
  (compute) to where the data is located, than the other way around. We are 
  trying to address both of these important problems in this project via a number of innovative architectural designs for memory hierarchies, as well as exploring non-traditional architectures like in-memory computing.

#### **4. META**
The overall goal of the project is to design tools to efficiently 
explore hybrid memory hierarchies for smartphones and other handheld
devices. To that end, we are developing a trace-based simulator based 
on the <a href="https://source.android.com">Android Open Source Project (AOSP)</a> which can simulate multiple types of memory 
hierarchies, including ones that are architected using emerging 
memory technologies, as well as arbitrarily deep cache hierarchies. 
The tool will also be capable of executing application traces across multiple Android versions. (<a href="/pubs/date2018.pdf">DATE 2018</a>, <a href="/pubs/mobicom2018.pdf">MobiCom 2018</a>)

