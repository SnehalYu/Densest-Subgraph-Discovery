

# Densest Subgraph Discovery

## Project Overview

This project implements and compares two efficient algorithms for Densest Subgraph Discovery (DSD) in large graphs, based on the paper:

**Efficient Algorithms for Densest Subgraph Discovery**  
*Yixiang Fang, Kaiqiang Yu, Reynold Cheng, Laks V.S. Lakshmanan, Xuemin Lin*  
PVLDB, 12(11): 1719-1732, 2019  
[arXiv:1906.00341](https://arxiv.org/abs/1906.00341)

Densest subgraph discovery is a fundamental task in graph mining, with applications in community detection, biological networks, and graph databases. The goal is to find a subgraph of a given graph with the highest density, measured as the average number of edges (or h-cliques) per vertex.

---

## Algorithms

### 1. Exact Algorithm (Algorithm 1: Exact)

This classical approach finds the densest subgraph by solving a sequence of maximum flow problems via binary search. It works for both edge-density and h-clique-density, providing the exact solution but can be computationally expensive for large graphs or higher-order cliques.

**Key Steps:**
- Initialize lower and upper bounds for possible density values.
- Build a flow network for each candidate density.
- Use binary search to converge to the optimal density subgraph.
- The flow network is constructed over all vertices and (h-1)-cliques, and the minimum s-t cut is used to check feasibility.



### 2. Core-Based Exact Algorithm (Algorithm 4: CoreExact)

This advanced algorithm leverages the concept of k-core and k-clique-core to significantly reduce the search space and speed up computation, while still guaranteeing exact results.

**Key Steps:**
- Perform (k, Ψ)-core decomposition to compute clique-core numbers.
- Use tight bounds on density to restrict binary search.
- Build flow networks only on relevant cores, not the entire graph.
- Apply pruning strategies to further reduce computation.
- The flow network size shrinks during the search as the algorithm focuses on smaller, denser subgraphs.

**Advantages:**  
- Achieves up to four orders of magnitude speedup over the classical exact algorithm on real and synthetic datasets.
- The core-based approach is effective for both edge-density and h-clique-density, and can be extended to pattern-density.

---

## Input Format

- Input graphs are provided as edge lists in text files.
- Each line represents an undirected edge: `u v`
- The graph should be simple (no self-loops or parallel edges).

---


3. **Output**
   - The densest subgraph (vertex list), density, and execution time are printed.


---



## Results

CoreExact achieves dramatic speedups over the classical Exact algorithm, especially for larger graphs and higher-order cliques. For example, on moderate-sized graphs, CoreExact can be up to four orders of magnitude faster, while returning the same densest subgraph.

---

## References

- Yixiang Fang, Kaiqiang Yu, Reynold Cheng, Laks V.S. Lakshmanan, Xuemin Lin.  
  "Efficient Algorithms for Densest Subgraph Discovery." PVLDB, 12(11): 1719-1732, 2019.  
 

---

## Individual Contributions

1. **Harsh Bavishi** – Algorithm 1, Report
2. **Aiman** – Agorithm 1, Report
3. **Snehal Yutika** – Algorithm 4, Webpage
4. **Mustafa Poonawala** – Algorithm 1
5. **Sanchit Arora** – Algorithm 4

