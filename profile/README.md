<p align="center"><img src="https://raw.githubusercontent.com/DynGraphLab/.github/main/profile/dyngraphlab-logo.png" alt="DynGraphLab Logo"></p>

> We develop and engineer algorithms for **fully dynamic graph problems** -- efficiently maintaining solutions as edges and vertices are inserted and deleted. Developed at the [Algorithm Engineering Group, Heidelberg University](https://ae.ifi.uni-heidelberg.de).

## What We Work On

**Dynamic Graph Algorithms.** Real-world graphs -- social networks, communication networks, web graphs -- evolve over time. Recomputing solutions from scratch after every change is prohibitively expensive. Our research focuses on designing, engineering, and experimentally evaluating algorithms that *dynamically* maintain high-quality solutions to fundamental graph problems under sequences of edge insertions and deletions. We combine theoretical insights with practical algorithm engineering to bridge the gap between theory and practice.

**Dynamic Matching.** Given a graph undergoing edge insertions and deletions, the goal is to maintain a (near-)maximum matching without recomputing it from scratch. We engineer and evaluate several fully dynamic maximal and maximum matching algorithms, including randomized and deterministic approaches such as random walks, blossom-based methods, and algorithms by Neiman-Solomon and Baswana-Gupta-Sen, and test them on real dynamic graph instances.

**Dynamic Edge Orientation.** In the dynamic edge orientation problem, the goal is to orient the edges of a dynamically changing graph such that the maximum out-degree (delta-orientation) is minimized. Low out-degree orientations are a key building block for many dynamic graph algorithms. We provide state-of-the-art exact and heuristic algorithms for this problem, including BFS-based approaches that compute the optimum on more than 90% of instances, and exact algorithms with update times up to 6 orders of magnitude faster than static recomputation. We also engineer approximation algorithms based on fractional relaxations.

**Dynamic Independent Set.** The maximum (weight) independent set problem asks for the largest set of pairwise non-adjacent vertices in a graph. We provide algorithms that maintain high-quality solutions under dynamic updates using *optimal neighborhood exploration*, a local search technique that creates independent subproblems solved to optimality. Applications include dynamic map labeling and vehicle routing.

**Dynamic Reachability.** Maintaining reachability information in a dynamically changing directed graph is a fundamental problem with applications in databases, program analysis, and network monitoring. Codes for the dynamic reachability problem are available at [dyreach.taa.univie.ac.at](https://dyreach.taa.univie.ac.at/).

## Projects

### Dynamic Matching

| Repository | Description |
|:-----------|:------------|
| [DynMatch](https://github.com/DynGraphLab/DynMatch) | Framework implementing fully dynamic maximal matching algorithms including blossom-based, random walk, Neiman-Solomon, and Baswana-Gupta-Sen methods |

### Dynamic Edge Orientation

| Repository | Description |
|:-----------|:------------|
| [DynDeltaOrientation](https://github.com/DynGraphLab/DynDeltaOrientation) | State-of-the-art exact and heuristic algorithms for fully dynamic edge orientation minimizing maximum out-degree |
| [DynDeltaApprox](https://github.com/DynGraphLab/DynDeltaApprox) | Approximation algorithms for dynamic edge orientation based on fractional relaxations (ESA 2025) |

### Dynamic Independent Set

| Repository | Description |
|:-----------|:------------|
| [DynWMIS](https://github.com/DynGraphLab/DynWMIS) | Solver for the fully dynamic maximum weight and cardinality independent set problem using optimal neighborhood exploration |

### Dynamic Reachability

| Repository | Description |
|:-----------|:------------|
| [DynReach](https://github.com/DynGraphLab/DynReach) | Implementations for the dynamic reachability problem ([external codes](https://dyreach.taa.univie.ac.at/)) |

### Benchmarks

| Repository | Description |
|:-----------|:------------|
| [dyngraphlab.github.io](https://github.com/DynGraphLab/dyngraphlab.github.io) | Dynamic graph benchmark instances and organization website with ~10 GB of real-world and synthetic fully dynamic graph sequences |

## Quick Start

### DynMatch

```bash
brew tap dyngraphlab/dyngraphlab && brew install dynmatch
dynmatch FILE --algorithm=dynblossom --dynblossom_maintain_opt
```

Or build from source:

```bash
git clone https://github.com/DynGraphLab/DynMatch && cd DynMatch
./compile_withcmake.sh
./deploy/dynmatch FILE --algorithm=dynblossom --dynblossom_maintain_opt
```

### DynDeltaOrientation

```bash
brew tap dyngraphlab/dyngraphlab && brew install dyndeltaorientation
dyndeltaorientation FILE --algorithm=IMPROVEDOPT
```

Or build from source:

```bash
git clone https://github.com/DynGraphLab/DynDeltaOrientation && cd DynDeltaOrientation
./compile_withcmake.sh -DILP=Off
./deploy/delta-orientations FILE --algorithm=IMPROVEDOPT
```

### DynDeltaApprox

```bash
git clone https://github.com/DynGraphLab/DynDeltaApprox && cd DynDeltaApprox
bazel build -c opt app --define logging=enabled
```

### DynWMIS

```bash
brew tap dyngraphlab/dyngraphlab && brew install dynwmis
dynwmis FILE --algorithm=DynamicOneFast
```

Or build from source:

```bash
git clone https://github.com/DynGraphLab/DynWMIS && cd DynWMIS
./compile_withcmake.sh
./deploy/dynwmis FILE --algorithm=DynamicOneFast
```

## Input Format

All tools use a common dynamic graph sequence format:

```
# n m
1 u v    # insert edge (u, v)
0 u v    # delete edge (u, v)
```

where `n` is the number of vertices, `m` is the number of update operations, and vertex IDs start at 1.

## Licensing

All projects are released under the [MIT License](https://opensource.org/licenses/MIT).

