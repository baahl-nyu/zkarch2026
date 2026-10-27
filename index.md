<!-- ---
layout: default
title: ZKARCH 2026
--- -->

# ZKARCH 2026

## The 2nd Workshop on Architectures for Zero-Knowledge Proofs and Verifiable Computation

ZKARCH brings together researchers and practitioners working across the zero-knowledge and verifiable-computing stack—from protocols, circuits, compilers, and proof systems to high-performance software and hardware accelerators.

The workshop provides an informal forum for sharing new ideas, identifying common architectural bottlenecks, and building connections across the community. We hope to see you there!

## Workshop Details

| | |
|:--|:--|
| **Date** | October 31, 2026 |
| **Time** | 8:00 AM |
| **Location** | Athens, Greece |

## Scope

Zero-knowledge proofs (ZKPs) and verifiable computation are moving rapidly from cryptographic theory into systems, applications, and real-world deployment. New proof systems, zkVMs, circuit frameworks, and acceleration techniques continue to emerge, each with distinct algebraic structures, performance characteristics, and hardware requirements.

ZKARCH creates a space to critically evaluate these approaches and share lessons across the full stack. Topics of interest include, but are not limited to:

- Architectures and accelerators for ZKPs and verifiable computation
- Hardware–software co-design for provers and verifiers
- Efficient finite-field arithmetic, polynomial commitments, MSMs, NTTs, and hashing
- GPU, FPGA, ASIC, and heterogeneous implementations
- zkVMs, circuits, compilers, runtimes, and programming systems
- Performance characterization, benchmarking, and cost models
- Memory systems, data movement, and distributed proving
- Security, privacy, and side-channel considerations
- Emerging applications and deployment experience


## Program

### Saturday, October 31, 2026 (All times are Athens local time)

| Time | Speaker | Affiliation | Talk Title |
|:--|:--|:--|:--|
| 8:00&nbsp;–&nbsp;8:20&nbsp;AM | | | **Arrival and Networking** |
| 8:20&nbsp;–&nbsp;8:25&nbsp;AM | | | **Welcome & Opening Remarks** |
| 8:25&nbsp;–&nbsp;8:45&nbsp;AM | **Tarunesh Verma** | University of Michigan | ZKProphet: Understanding Performance of Zero-Knowledge Proofs on GPUs |
| 8:45&nbsp;–&nbsp;9:05&nbsp;AM | **Cheng Wang** | Xi’an Jiaotong University | Accelerating Zero-Knowledge Proofs with Unified Architectures |
| 9:05&nbsp;–&nbsp;9:25&nbsp;AM | **Lan Yang** | Fudan University | Scalable NTT and MSM Acceleration for Zero-Knowledge Proofs |
| 9:25&nbsp;–&nbsp;9:45&nbsp;AM | **Naifeng Zhang** | Carnegie Mellon University | Towards Closing the Performance Gap for Cryptographic Kernels Between CPUs and Specialized Hardware |
| 9:45&nbsp;–&nbsp;10:05&nbsp;AM | **Sunchae Kim** | University of Toronto | Efficient HBM-Based PIM Architecture for Linear Complexity Zero Knowledge Proofs |
| 10:05&nbsp;–&nbsp;10:20&nbsp;AM | | | **Coffee Break** |
| 10:20&nbsp;–&nbsp;10:40&nbsp;AM | **Alhad Daftardar** | New York University | Locus: A Framework for Exploring and Optimizing Point Addition Hardware for Zero-Knowledge Proofs |
| 10:40&nbsp;–&nbsp;11:00&nbsp;AM | **Stefanos Chaliasos** | University College London | The State of ZKP Security Tools and Verification Efforts |
| 11:00&nbsp;–&nbsp;11:20&nbsp;AM | **Bowen Duan** | Duke University | Accelerating ZKP Provers from Algorithm to Hardware Stack |
| 11:20&nbsp;–&nbsp;11:40&nbsp;AM | **Yueteng Yu** | Tsinghua University | Accelerating Plonkish Witness Generation on GPUs |
| 11:40&nbsp;–&nbsp;12:00&nbsp;PM | **Brendan Sweezy** | New York University | Accelerating Folding-Based ZKPs for Low-Memory Proving |

## Talk Abstracts

### Tarunesh Verma — ZKProphet: Understanding Performance of Zero-Knowledge Proofs on GPUs

Zero-Knowledge Proofs (ZKP) are protocols which construct cryptographic proofs to demonstrate knowledge of a secret input in a computation without revealing any information about the secret. ZKPs enable novel applications in private and verifiable computing such as anonymized cryptocurrencies and blockchain scaling and have seen adoption in several real-world systems. Prior work has accelerated ZKPs on GPUs by leveraging the inherent parallelism in core computation kernels like Multi-Scalar Multiplication (MSM). However, we find that a systematic characterization of execution bottlenecks in ZKPs, as well as their scalability on modern GPU architectures, is missing in the literature. This paper presents ZKProphet, a comprehensive performance study of Zero-Knowledge Proofs on GPUs. Following massive speedups of MSM, we find that ZKPs are bottlenecked by kernels like Number-Theoretic Transform (NTT), as they account for up to 90% of the proof generation latency on GPUs when paired with optimized MSM implementations. Available NTT implementations under-utilize GPU compute resources and often do not employ architectural features like asynchronous compute and memory operations. We observe that the arithmetic operations underlying ZKPs execute exclusively on the GPU's 32-bit integer pipeline and exhibit limited instruction-level parallelism due to data dependencies. Their performance is thus limited by the available integer compute units. While one way to scale the performance of ZKPs is adding more compute units, we discuss how runtime parameter tuning for optimizations like precomputed inputs and alternative data representations can extract additional speedup. With this work, we provide the ZKP community a roadmap to scale performance on GPUs and construct definitive GPU-accelerated ZKPs for their application requirements and available hardware resources.

[Link to paper](https://arxiv.org/abs/2509.22684)

### Cheng Wang — Accelerating Diverse Zero-Knowledge Proofs with Unified Architectures

Zero-knowledge proofs (ZKPs) are widely deployed cryptographic protocols for privacy-preserving blockchains and verifiable computing. Domain-specific hardware has been proposed to accelerate their expensive proof generation, but existing designs are limited to a single protocol and a narrow set of kernels. As a result, they fail to cover the diverse algorithms that offer different tradeoffs for various application scenarios. In this talk, I will present GenZA, a general and efficient accelerator for diverse ZKP protocols, including Groth16, HyperPlonk, and Plonky2. Following the unified architecture design philosophy, GenZA adopts a homogeneous array of hardware units that can be flexibly reconfigured to support data bitwidths from 64-bit up to 768-bit, as well as both general and special field moduli. Novel kernel mapping strategies enable efficient execution of all dominant kernels on the same hardware substrate with high resource utilization. GenZA achieves two orders of magnitude speedup over CPUs and 1.64× to 2.51× higher performance per area than prior ZKP accelerators.

[Link to paper](https://ieeexplore.ieee.org/document/11617503/)

### Yang Lan — Scalable NTT and MSM Acceleration for Zero-Knowledge Proofs

Zero-knowledge proofs (ZKPs) are increasingly used in blockchain and verifiable computing, where proof generation involves two major computational kernels: Multi-Scalar Multiplication (MSM) and Number-Theoretic Transform (NTT). In this talk, we first introduce distributed MSM acceleration, which can efficiently scale across multiple computing nodes due to its inherent parallelism. We then focus on distributed NTT acceleration, which presents unique challenges. Unlike MSM, NTT involves global data dependencies that require intensive all-to-all communication across nodes. Furthermore, synchronization mismatches can cause network contention, while inefficient data layouts limit memory bandwidth utilization. To address these challenges, we present Omni, a scalable multi-FPGA NTT accelerator. Omni introduces a streaming global transpose flow to overlap communication with computation, One-to-One Permutation Synchronization (OPS) to avoid network contention, and Communication-Aware Streaming Layout (CASL) to improve memory access efficiency. Our eight-FPGA system completes a 2³⁰-scale MSM in approximately 5 seconds and a 2³⁰-point NTT in 1.469 seconds, demonstrating the feasibility of distributed FPGA acceleration for large-scale ZKP workloads.

[Link to paper](https://epapers2.org/asscc2026/ESR/paper_details.php?paper_id=1026)

### Naifeng Zhang — Towards Closing the Performance Gap for Cryptographic Kernels Between CPUs and Specialized Hardware

Specialized hardware like application-specific integrated circuits (ASICs) remains the primary accelerator type for cryptographic kernels based on large integer arithmetic. Prior work has shown that commodity and server-class GPUs can achieve near-ASIC performance for these workloads. However, achieving comparable performance on CPUs remains an open challenge. This work investigates the following question: How can we narrow the performance gap between CPUs and specialized hardware for key cryptographic kernels like basic linear algebra subprograms (BLAS) operations and the number theoretic transform (NTT)? To this end, we develop an optimized scalar implementation of these kernels for x86 CPUs at the per-core level. We utilize SIMD instructions—specifically AVX2 and AVX-512—to further improve performance, achieving an average speedup of 38 times and 62 times over state-of-the-art CPU baselines for NTTs and BLAS operations, respectively. To narrow the gap further, we propose a small AVX-512 extension, dubbed multi-word extension (MQX), which delivers substantial speedup with only three new instructions and minimal proposed hardware modifications. MQX cuts the slowdown relative to ASICs to as low as 35 times on a single CPU core. Finally, we perform a roofline analysis to evaluate the peak performance achievable with MQX when scaled across an entire multi-core CPU. Our results show that, with MQX, top-tier server-grade CPUs can approach the performance of state-of-the-art ASICs for cryptographic workloads.

[Link to paper](https://dl.acm.org/doi/10.1145/3725843.3756120)

### Sunchae (Chris) Kim — Efficient HBM-Based PIM Architecture for Linear Complexity Zero Knowledge Proofs

Zero-knowledge proofs (ZKPs) are emerging as a core technology for privacy-preserving computation. Despite steady progress in protocol and algorithm design, generating these proofs remains computationally intensive, driving growing interest in hardware acceleration for kernels such as number-theoretic transform (NTT) and multi-scalar multiplication (MSM). Among them, the sumcheck protocol offers a compelling alternative with O(n) prover complexity compared to O(n log n) for NTT-based approaches, yet our analysis reveals its execution is fundamentally memory-bound, with severely underutilized compute. This characteristic demands a memory-centric acceleration strategy, in contrast to compute-centric approaches of prior work. To this end, we propose SumcheckPIM, an HBM-based processing-in-memory architecture optimized for the sumcheck protocol. SumcheckPIM introduces 256-bit modular arithmetic units at the bank level to support real-world field sizes, a Fiat-Shamir unit on the logic die for global accumulation and challenge generation, and an inter-bank processing unit enabling protocol completion without host interaction. We also propose a DRAM-aware folding scheme that maximizes row buffer locality through row packing and bank ping-ponging. Our design achieves this while maintaining JEDEC compliance with minimal modifications to existing commercial HBM-PIM architectures. We demonstrate that SumcheckPIM delivers both high performance and efficiency, achieving 5.3×–13.3× and 334.2×–361.1× speedup over GPU and CPU baselines, respectively.

[Link to paper](https://dl.acm.org/doi/10.1145/3797905.3807843)

### Alhad Daftardar — Locus: A Framework for Exploring and Optimizing Point Addition Hardware for Zero-Knowledge Proofs

Elliptic-curve point addition (PADD) is a fundamental building block of multi-scalar multiplication (MSM), one of the most computationally expensive operations in many zero-knowledge proof (ZKP) systems. Despite its importance, designing efficient PADD hardware is far from straightforward. Different elliptic curves, arithmetic implementations, and architectural choices introduce a wide range of performance and area trade-offs, yet prior hardware designs have explored only a small fraction of these possibilities. We introduce Locus, a framework that automatically generates ASIC and FPGA implementations of point addition for different elliptic curves, enabling systematic exploration of this design space. Using Locus, we evaluate over 1,000 design points to understand how different design choices affect hardware efficiency. Our results demonstrate a 2.71× geometric-mean speedup and 3.11× geometric-mean area reduction compared to prior ASIC implementations, translating to a 3.15× improvement in end-to-end proof generation when integrated into an existing ZKP accelerator at equal area. Beyond these performance gains, Locus provides insights into the architectural trade-offs involved in designing efficient cryptographic hardware.

[Link to paper](https://arxiv.org/pdf/2609.18846)


### Stefanos Chaliasos — ZKP Security Tools and Verification: Coverage, Effectiveness, Adoption, and Challenges

Zero-knowledge proofs (ZKPs) have become a core technology for privacy and verifiable computing. They are used to secure blockchains that handle billions of dollars and identity applications dealing with sensitive personal data. However, ZKP systems are complex, and subtle implementation errors can completely break their guarantees, letting attackers forge money or false proofs of identity. Researchers and practitioners have therefore developed a growing set of bug detection and formal verification methods to secure these systems. Yet their real-world effectiveness and adoption remain unclear. In this paper, we aim to shed light on the state of ZKP security tooling. We first systematize the landscape of these tools and observe that most target Circom, leaving newer DSLs and zkVMs with limited support. We then evaluate six tools across 70 real-world vulnerabilities and find that while the tools detect 45.7% of bugs on isolated targets, their effectiveness drops to 19.6% on full codebases, with important vulnerability classes left unaddressed. We also present the first systematic analysis of formal verification efforts, revealing that current work focuses primarily on constraint correctness and identifying key gaps and risks. Finally, we survey 48 practitioners, showing that development and security remain human-led, LLMs are widely used, and practitioners prioritize tools with clearer guarantees and lower integration effort. Overall, our results highlight the need for better integration of security tooling with the development and auditing process, and we provide actionable insights for researchers and practitioners.

[Link to paper](https://arxiv.org/pdf/2607.23752)

### Bowen Duan — Toward Unified ZKP Acceleration: From Efficient MSM to General-Purpose Prover Architectures

Zero-knowledge proofs (ZKPs) are increasingly important for privacy-preserving computation and verifiable systems, but proof generation remains computationally expensive. This talk explores two complementary directions toward efficient and flexible ZKP acceleration. First, we focus on multi-scalar multiplication (MSM), a major bottleneck in curve-based ZKP systems. Building on Pippenger's algorithm, we explore opportunities to identify and reuse redundant point operations across scalar windows to improve computational efficiency. Second, we discuss the challenges of designing general-purpose prover architectures for heterogeneous ZKP workloads. Curve-based and hash-based protocols require substantially different operand widths, making efficient acceleration on a unified hardware platform challenging. We introduce our ongoing efforts toward a reconfigurable architecture based on modular arithmetic that can accommodate these diverse requirements Together, these efforts highlight the potential of algorithm-hardware co-design for accelerating future ZKP applications.

### Yueteng Yu — Accelerating Plonkish Witness Generation on GPUs

Prior work on Zero-knowledge proof (ZKP) acceleration has largely focused on backend computations, such as number-theoretic transform (NTT) and multi-scalar multiplication (MSM), while leaving witness generation unaccelerated. Because witness must be generated for each new circuit input, this stage can limit the overall benefits of backend acceleration. Efficient GPU execution of Plonkish witness generation is challenging: heterogeneous gate types and data dependencies complicate scheduling, while irregular memory accesses reduce memory efficiency. This work addresses these challenges by jointly optimizing scheduling and data layout. Type-aware layered scheduling groups independent gates of the same type while preserving dependencies, reducing kernel launches and improving parallel execution. An output-aligned witness layout arranges intermediate values according to the execution schedule, enabling coalesced output writes and input-index table accesses while reducing address-mapping overhead. On an NVIDIA RTX 4090, scheduling reduces kernel launches by 23.2%–76.0%, and the combined optimizations deliver an average 2.0× speedup over a GPU baseline using naive scheduling and the original witness layout. The resulting GPU implementation achieves a 146.3× speedup in witness generation over the original CPU-based Plonky2 implementation.

[Link to paper](https://doi.org/10.1145/3797905.3807842)


## Organizers and Contact

Alhad Daftardar (PhD Candidate, NYU) - adj9396@nyu.edu

Jianqiao "Cambridge" Mo (PhD Candidate, NYU) - jqmo@nyu.edu

Brendan Sweezy (PhD Student, NYU) - bcs7944@nyu.edu

Brandon Reagen (Associate Professor, NYU) - bjr5@nyu.edu

## Previous Workshop

The [first ZKARCH workshop](https://wp.nyu.edu/baahl/zkarch-2025/) was held with MICRO 2025 in Seoul, Korea.

