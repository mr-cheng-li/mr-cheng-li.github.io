## Welcome to Cheng Li's Website

Most recently, I have joined the Department of Computer Science at University of Science and Technology of China (USTC) as a research professor. My research interests lie in various topics related to computer systems such as operating systems, distributed systems, databases and etc, particularly in improving performance, consistency, fault tolerance, and availability of the above mentioned systems.

Prior to joining USTC, I was an associated researcher with my PhD supervisor [Rodrigo Rodrigues](http://www.gsd.inesc-id.pt/~rodrigo/) at [INESC-ID, Portugal](http://www.gsd.inesc-id.pt/), and a senior member of technical staff at [Oracle Labs Swiss](https://labs.oracle.com/pls/apex/f?p=94065:23:2478385225960::NO::P23_LOCATION_ID:69). 

In 2016, I obtained my PhD degree from the Dependable Systems Group at the [Max Planck Institute for Software Sytems (MPI-SWS)](www.mpi-sws.org) and [Saarland University](http://www.cs.uni-saarland.de/) in Germany. Before studying at MPI-SWS, I obtained my bachelor degree from [Nankai University](http://nankai.en.school.cucas.cn/) in 2009.

### Collaborations

It is my great honor to work with the following brilliant computer scientists (sorted by last name in an alphabetical order): [Yungang Bao](http://asg.ict.ac.cn/baoyg/), [Allen Clement](http://www.mpi-sws.org/~aclement/), [Miguel Castro](https://www.microsoft.com/en-us/research/people/mcastro/), [Pedro Fonseca](https://homes.cs.washington.edu/~pfonseca/), [Johannes Gehrke](http://www.cs.cornell.edu/johannes/), [Zhenyu Guo](https://imzhenyu.github.io/about/), [Flavio Junqueira](https://github.com/fpj), [João Leitão](http://asc.di.fct.unl.pt/~jleitao/research.php), [Daniel Porto](https://sites.google.com/site/danielporto/), [Nuno Preguiça](http://asc.di.fct.unl.pt/~nmp/), [Viktor Vafeiadis](https://www.mpi-sws.org/~viktor/), and [Lidong Zhou](https://www.microsoft.com/en-us/research/people/lidongz/). 

### News
- [Sep-05-2017] Congrats to Youxu on his research abstract accepted by [the Student Research Competition at SOSP 2017](https://www.sigops.org/sosp/sosp17/src.html). In this project, we explore data correlations between files to seek opportunities for prefetching metadata of correlated files, in order to scale distributed file systems.

### Current students
- Youxu Chen (co-advised PhD candidate)
- Youhui Bai (co-advised Master)
- Xinyang Shao (co-advised Master)
- Jingbo Su (co-advised Master)

### Previous students
- David Lopes (co-advised Master)

### Open positions for prospective students
I am looking forward to working with talent students who are interested in overcoming challenges in systems research, and want to pursue graduate degrees. In addition, I am happy to supervise bachelor thesis projects. Feel free to send messages to chenglinkcs@gmail.com, if you want to contact me or you can stop by my office (Room 601, High Performance Computing Center, East Campus, USTC).

### Research projects

#### Ongoing projects

##### Building fast and consistent (geo-)replicated systems

Geo-replication, replicating data at geo-graphically dispersed data centers, is a major solution for popular online services to scale themselves to meet the needs of their increasingly growing user base. With this technique, users contact with a nearby data center to get fast response, and coordination among all data centers is required to keep data globally consistent. Due to the high cost of exchanging message in a wide area network, however, offering low latency and maintaining strong consistency can not be achieved simultaneously. As a result, many systems restort to use weak consistency model (eventual consistency), in which each data center independently processes requests and resolves conflicts much later, to avoid immediate coordination for each request. In this project, we proposed a solution allowing multi-level consistency semantics to co-exist in one system. 

- Making Geo-Replicated Systems Fast as Possible, Consistent when Necessary [[pdf](https://people.mpi-sws.org/~chengli/papers/rbOSDI.pdf)][[technical report](https://people.mpi-sws.org/~chengli/trs/rbTR.pdf)][[poster](https://people.mpi-sws.org/~chengli/posters/rbPoster.pdf)]. Cheng Li, Daniel Porto, Allen Clement, Johannes Gehrke, Nuno Preguica, and Rodrigo Rodrigues, In Proceedings of the 10th USENIX Symposium on Operating Systems Design and Implementation (OSDI 2012), Hollywood, CA, USA
- Geo-Replication: Fast If Possible, Consistent If Necessary [[pdf](https://people.mpi-sws.org/~chengli/papers/p81.pdf)]. Cheng Li, Valter Balegas, Mahsa Najafzadeh, Daniel Porto, Allen Clement, Sergio Duarte, Carla Ferreira, Johannes Gehrke, João Leitão, Nuno Preguiça, Rodrigo Rodrigues Marc Shapiro and Viktor Vafeiadis, IEEE Data Engineering Bulletin, Volume 39, Page 81-92. IEEE Computer Society. March 2016.

Most recently, (geo-)replication has been widely adopted by online service providers (such as Google, Amazon, Yahoo!, Microsoft, and etc) to offer their customers a good user experience in terms of low-latency access. To achieve this goal requires system builders to solve a fundamental tension between consistency semantics and performance benefits. The recent proposals including our prior work RedBlue consistency suggest that strong consistency is an obstacle to scale out a replicated system since it requires high-cost coordination, and avoiding coordination and taking advantage of eventual consistency are the major solutions to make a replicated system fast enough. However, to precisely determine which consistency level for each operation leads to a huge amount of non-trivial work. In addition, without a tool, manual classification can be error-prone, and is not scalable. For these reasons, we present SIEVE, a tool that relieve Java programmers from this decision process, allowing applications to automatically extract good performance when possible, while resorting to strong consistency whenever required by the target semantics. Taking as input a set of application-specific invariants and small annotations regarding merge semantics, SIEVE performs a combination of static and dynamic analysis, offline and at runtime. We evaluate SIEVE using two web applications and show that the automatic classification overhead is low, and the performance improvement enabled by replication is significant. 

- Automating the Choice of Consistency Levels in Replicated Systems [[pdf](https://people.mpi-sws.org/~chengli/papers/sieve-usenix-atc-final.pdf)]. Cheng Li, João Leitão, Allen Clement, Nuno Preguiça, Rodrigo Rodrigues and Viktor Vafeiadis, In Proceedings of the 2014 USENIX Annual Technical Conference (USENIX ATC 2014), Philadelphia, PA, USA

Replication has been widely adopted to build highly scalable services, but this goal is often compromised by the coordination required to ensure application-specific properties such as state convergence and invariant preservation. In this paper, we propose a principled mechanism to minimize coordination in replicated systems via the following components: a) a notion of restriction over pairs of operations, which captures the fact that the two operations must be ordered w.r.t. each other in any partial order; b) a generic consistency model which, given a set of restrictions, requires those restrictions to be met in all admissible partial orders; c) principles for identifying a minimal set of restrictions to ensure the above properties; and d) a coordination service that dynamically maps restrictions to the most efficient coordination protocols. Our preliminary experience with example applications shows that we are able to determine a minimal coordination strategy. 

- Minimizing Coordination in Replicated Systems [[pdf](https://people.mpi-sws.org/~chengli/papers/a8-Li.pdf)]. Cheng Li, João Leitão, Allen Clement, Nuno Preguiça and Rodrigo Rodrigues, In Proceedings of the Workshop on on Principles and Practice of Consistency for Distributed Data (PaPoC'15), Bordeaux, France
- Building Fast and Consistent (Geo)Replicated Systems: from Principles to Practice [[pdf](https://people.mpi-sws.org/~chengli/thesis/final_version_thesis_cheng.pdf)]. Cheng Li. PhD Thesis. MPI-SWS. Defended in May 2016

##### Scaling distributed file systems via prefetching metadata of correlated files

Distributed file systems (dfs) have become key data storage components to building scalable Internet services. In these systems, normally, files and their metadata are decoupled so that a dedicated metadata server (mds) is responsible for fetching metadata before letting clients access files directly from data server. A survey identified that the number of IOs to mds is substantial and accounts for 50% in the overall IOs to the whole dfs. As a result, the performance of mds is very crucial to scale dfs. In this project, we explore the potential of correlating files and prefetching their metadata by a single metadata read to reduce IO traffic to mds.

##### Scaling logging and recovery in databases on multi-core

Write-ahead-log (WAL) is a key technique used in databases to ensure data durability and maintain recovery consistency in presence of failures. However, the traditional design sequentially flushes log entries into a single log data structure and thus is not scalable. Moreover, it imposes stronger ordering constraints over transactions than their actual dependencies. When recovering from a failure, a sequential scan must be performed to retrieve transactions whose updates were not persistent and apply them in a serial order. The recovery process is slow since it does not take advantage of parallelisms enabled by multi-core machines at all. In this project, we attempt to design a scalable logging method to relax ordering constraints of logged transactions so that we can maintain a set of distributed logs that can be written and read in parallel.

##### Fast In-memory Key-Value Stores

In-memory key-value stores have been intensively integrated into many applications by major Internet service providers such as Amazon, Faceook, Twitter and so on, to offer fast responses. Most of kv store implementations opimitize performance for read-intensive workloads. However, more recently, studies show that a wide range of applications demonstrate a significant amount of updates and scans in their workloads, which perform poorly w.r.t state-and-the-art solutions. In this project, we aim to build a scalable in-memory kv store that scales well for update and scanning queries. To achieve this, we have to solve two challenges: (a) using scan-friendly index data structure like SkipList without compromising the speed of read and write queries; and (b) reducing write-write conflicts in presence of high concurrency and avoiding cache line transfers across cpu cores.

- Fast Scans and Updates on In-memory Key Value Stores (Under review)

#### Past projects

##### Resource-efficent Fault Tolerance
We present a new technique for designing distributed protocols for building reliable stateful services called Visigoth Fault Tolerance (VFT). VFT introduces the Visigoth model, which makes it possible to calibrate the timing assumptions of a system using a threshold of slow processes or messages, and also to distinguish between non-malicious arbitrary faults and correlated attack scenarios. This enables
solutions that leverage the characteristics of data center systems, namely their secure environment and predictable performance, in order to allow replicated systems to be more efficient with respect to the utilization of resources than those designed under asynchrony and Byzantine assumptions, while avoiding the need to make a system synchronous, or to restrict failure modes to silent crashes. We
implemented a VFT protocol for a state machine replication library, and ran several benchmarks. Our evaluation shows that VFT has comparable performance to existing schemes and brings significant benefits in terms of the throughput per dollar, i.e., the server cost for sustaining a certain level of request execution.

- Visigoth Fault Tolerance [[pdf](https://people.mpi-sws.org/~chengli/papers/a8-porto.pdf)][[technical report](https://people.mpi-sws.org/~chengli/trs/vftTR.pdf)]. Daniel Porto, João Leitão, Cheng Li, Aniket Kate, Allen Clement, Flavio Junqueira and Rodrigo Rodrigues, In Proceedings of of the European Conference on Computer Systems (EuroSys'15), Bordeaux, France

##### Finding and recovering from concurrency bugs

When analyzing bug reports from the bug database of MySQL, a highly concurrent application, we found a very interesting thing: some concurrency bugs when triggered firstly silently corrupted internal states but became visible to users much later. We named this class of bugs latent bugs. Detecting latent bugs is a challenge, but it also provides an oppotunity to recover latent bugs before they are seen by users. Currently we're trying to build a novel tool to detect latent bugs. Our main idea is to check whether the concurrent executions are linearizable by comparing the output and the internal states after concurrent executions and sequential executions. Once the detector is built, we will use it at run-time with the goal of allowing transparent recovery for the latent concurrency bugs. 

- Finding Complex Concurrency Bugs in Large Multi-Threaded Applications [[pdf](https://people.mpi-sws.org/~chengli/papers/eurosys11-pike.pdf)]. Pedro Fonseca, Cheng Li, and Rodrigo Rodrigues, In Proceedings of the 6th European Professional Society on Computer Systems (EuroSys 2011), Salzburg, Austria
- A study of the Internal and External Effects of Concurrency Bugs [[pdf](https://people.mpi-sws.org/~chengli/papers/bug_study_dsn2010.pdf)]. Pedro Fonseca, Cheng Li, Vishal Singhal and Rodrigo Rodrigues, In Proceedings of the DSN 2010 - 40th IEEE/IFIP International Conference on Dependable Systems and Networks, Chicago, USA

### Professional activities (recent)
- ACM SOSP Poster Session Co-Chair 2017 (with Gernot Heiser)
- ACM Transactions on Storage reviewer
- IEEE/ACM Transactions on Networking reviewer
- APSys 2017 PC member 2017
- ICAC 2017 reviewer 2017
- DSN 2017 reviewer 2017

### Teaching
- Principles and Techniques of Compiler, USTC, Fall, 2017 (with [Prof. Yuezhang](http://staff.ustc.edu.cn/~yuzhang/))
