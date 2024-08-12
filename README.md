# White-Box Micro-Adaptive Query Processing

This repository provides the implementation of White-Box Micro-Adaptive Query Processing, as described in our paper submitted to ICDE 2025. The project addresses micro-architectural hazards in in-memory data management systems, such as cache misses and branch mispredictions, through hazard-adaptive query execution.


## Hazard-Adaptive Operators

The `BOSSHazardAdaptiveEngine` submodule contains our hazard-adaptive operators:
1. [**SELECT**](https://github.com/jack-pearce/BOSSHazardAdaptiveEngine/blob/93b0e64a574a4fef7d44090c9a5b59018e3779a8/Source/operators/selectImplementation.hpp)
2. [**PARTITION**](https://github.com/jack-pearce/BOSSHazardAdaptiveEngine/blob/93b0e64a574a4fef7d44090c9a5b59018e3779a8/Source/operators/partitionImplementation.hpp) (of a partitioned JOIN)
3. [**GROUP**](https://github.com/jack-pearce/BOSSHazardAdaptiveEngine/blob/93b0e64a574a4fef7d44090c9a5b59018e3779a8/Source/operators/groupImplementation.hpp)


## Repositories (submodules)

Our system integrates these operators using `BOSS`, a composable data management system (DMS). BOSS allows us to combine a number of individual (partially-evaluating) engines (shared libraries) into a complete system. The following five submodules each form an engine:

1. [**BOSSArrowStorageEngine**](https://github.com/jack-pearce/BOSSArrowStorageEngine/tree/320b470f2e2b5e8a88ee22378839b8df7efef540): Storage engine
2. [**BOSSHazardAdaptiveEngine**](https://github.com/jack-pearce/BOSSHazardAdaptiveEngine/tree/93b0e64a574a4fef7d44090c9a5b59018e3779a8): Hazard-adaptive operators
3. [**BOSSNonAdaptiveEngine**](https://github.com/jack-pearce/BOSSNonAdaptiveEngine/tree/b593806b530994c547cb0d259712e748605e3cfd): Non-adaptive JOIN for use with the adaptive PARTITION operator
4. [**BOSSVectorizationCoordinatorEngine**](https://github.com/jack-pearce/BOSSVectorizationCoordinatorEngine/tree/6a1c4212a68ac3c698cf8d4c1f2276ca6ea2bc19): Coordinates execution engines for vectorized query processing

5. [**BOSSVeloxEngine**](https://github.com/jack-pearce/BOSSVeloxEngine/tree/488defc60bc4e7b7cf9e770e22c36b0e71ab4e41): Meta's [Velox execution engine](https://github.com/facebookincubator/velox)

Other submodules:

6. [**BOSS**](https://github.com/jack-pearce/BOSS/tree/9014241a760b8308eaec74295ee2f86e979dfa24): The core composable DMS
7. [**BOSSKernelBenchmarks**](https://github.com/jack-pearce/BOSSKernelBenchmarks/tree/7462c531e7bc4376413aa8a52c61f65d0b4d38a9): Generates test data and runs benchmarks


## Benchmarks

In the future, we will provide a single script to build all engines and run benchmarks. Currently, each repository includes build instructions/scripts in the `README.md` or `Scripts` directory. Benchmarks are managed via [scripts](https://github.com/jack-pearce/BOSSKernelBenchmarks/tree/7462c531e7bc4376413aa8a52c61f65d0b4d38a9/Scripts) in the `BOSSKernelBenchmarks` repository.


## Authors
- Jack Pearce (Imperial College London)
- Hubert Mohr-Daurat (Imperial College London)
- Holger Pirk (Imperial College London)
