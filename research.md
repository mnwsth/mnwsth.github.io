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

#### META
The overall goal of the project is to design tools to efficiently 
explore hybrid memory hierarchies for smartphones and other handheld
devices. To that end, we are developing a trace-based simulator based 
on the <a href="https://source.android.com">Android Open Source Project (AOSP)</a> which can simulate multiple types of memory 
hierarchies, including ones that are architected using emerging 
memory technologies, as well as arbitrarily deep cache hierarchies. 
The tool will also be capable of executing application traces across multiple Android versions. (<a href="/pubs/date2018.pdf">DATE 2018</a>, <a href="/pubs/mobicom2018.pdf">MobiCom 2018</a>)

#### Prefetcher Designs
The architecture of main memory has experienced a paradigm shift in recent years, with non volatile memory technologies (NVM) like Phase Change Memory (PCM) being incorporated into the hierarchy at the same level as DRAM. This transformation is being carried out by either splitting the memory address across two or more memory technologies, or using a faster technology with higher lifetimes, typically the DRAM, as a cache for the higher capacity, albeit slower main memory made up of a NVM.
Design of such hybrid architectures remains an active area of research from the perspective of DRAM-as-a-cache design, since DRAM could quickly become the bottleneck, as cache lookups require multiple accesses for reading tag and data. In this work, we are exploring if augmenting the DRAM-as-a-cache model with a novel DRAM cache prefetcher which builds on state of the art Alloy Cache could yield performance benefits. The new DRAM cache architecture allows for prefetching data at both cacheline and page granularities from the NVM, and as a result, provides upto a maximum of 2× performance improvement over a state of the art baseline. (<a href="/pubs/hotstorage2020.pdf">HotStorage '20</a>)

#### Workload Characterization and Tools
To design efficient architectures, one must understand application 
behavior. Workload characterization is a great way to understand the 
behavior of contemporary applications, and narrow down the sources of 
inefficiencies and performance bottlenecks in contemporary architectures.
As a result, we have carried out extensive characterization of the 
SPEC 2017 CPU suite to understand its memory behavior. In addition, 
we have also explored if statistical sampling techniques like SimPoint 
remain effective for contemporary workloads. In this project, we observed that for cases like memory hierarchy explorations, SimPoints should 
be used judiciously and with extreme caution in order to derive correct conclusions – inappropriately chosen SimPoint configurations can show large deviations in memory hierarchy behavior as compared to full runs, as reported by prior studies. (<a href="/pubs/icpe2019b.pdf">ICPE '19</a>, <a href="/pubs/iiswc2019.pdf">IISWC '19</a>)



