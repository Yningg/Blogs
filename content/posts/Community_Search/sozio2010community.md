---
title: "The community-search problem and how to plan a successful cocktail party"
date: 2026-06-20
tags: ["Community Search", "Graph Theory", "Information Retrieval"]
categories: Community Search
ShowToc: true
TocOpen: true
---

> This paper is the **first** paper that propose the problem of community search.
> Keywords: $k$-core; Undirected graph; Size-constraints; Greedy algorithm; Heuristic Algorithms

## 1 Motivations
Discovering communities in graphs and social networks has drawn a large amount of attention in recent years. Most of the work has focused in the scenario where communities need to be discovered in an apriori manner, with only reference to the input graph. <u>However, in many application scenarios we are interested in discovering the community defined by a given set of nodes.</u>

### 1.1 Potential Applications
Social-network analysis, collaborative tagging systems, query-log analysis, biology, and others.


## 2 Problem Statements

> **Problem 1 (Generic objective function)**: Given an undirected (connected) graph $G = (V, E)$, a set of query nodes $Q \subseteq V$ , and a goodness function $f$, we seek to find an induced subgraph $H = (V_H, E_H )$ of $G$, such that:
> + $V_H$ contains $Q$ ($Q \subseteq V_H$); 
> + $H$ is connected;
> + $f(H)$ is maximized among all feasible choices for $H$.


Functions that capture the **density** of the subgraph $H$ are considered.
+ $\frac{|V_H| \cdot (|V_H|-1)}{2}$: since even in its  simplest form this density definition leads to NP-hard problems, so this definition is not considered.
+ The average degree $f_a(H)$ of the nodes in $H$ ($\frac{2|E_H|}{V_H}$). However, using this measure can lead to non intuitive results.
+ The minimum degree $f_m(H)$ of the nodes in $H$ (<font color=red>Considered</font>).
  + Though it's sensitive to outliers, it does not suffer from the problem of attaching a non-related community.


Another way to avoid the pathological situations of attaching communities that are far way from query nodes, is to **set a distance constraint**:
+ Set $d_G(v, q)$ as the length of the shortest path between nodes $v$ and $q$ in the graph $G$. If $v$ and $q$ are in different connected components, then $d_G(v, q) = \infty$.
+ The distance of $v$ from the query nodes $Q$: $D_Q(G, v) = \sum_{q \in Q} d_G(v, q)^2$
+ The distance of the furthest node from $Q$: $D_Q(G) = \max_{v \in V(G)}\{D_Q(G, v)\}$

> **Problem 2 (Concrete Problem)**: Given an undirected (connected) graph $G = (V, E)$, a set of query nodes $Q \subseteq V$, and a number $d$ to be interpreted as a distance constraint, we seek to find an induced subgraph $H = (V_H, E_H)$ of $G$, such that:
> + $V_H$ contains $Q (Q \subseteq V_H)$;
> + $H$ is connected;
> + $D_Q(H) \leq d$;
> + The minimum degree function $f_m(H)$ is maximized among all feasible choices for $H$.


## 3 Community Search Algorithms

### 3.1 Communities Without Size Constraints

<span style="font-size: 13px;">*The GREEDY algorithm was proposed and studied by Asahiro et al. and later analyzed by Charikar, who showed that it achieves a factor 2 approximation guarantee for the densest-subgraph problem.*</span>

<span style="font-size: 13px;">*A factor 2 approximation means: The solution the algorithm gives you is guaranteed to be <u>at least half as good as</u> the best possible solution.</span>

#### 3.1.1 **GREEDY algorithm**
> + Start by setting $G_0 = G$ and proceed by deleting one node in each step;
> +  For each t-th step of execution,
>       + Delete a node $u$ that has minimum degree in $G_{t−1}$. and all the edges incident to $u$ from $G_{t-1}$ to obtain graph $G_t$
>       + Extract the connected component of $G_t$, $G_t^{'}$, which contains all query nodes $Q$
>       + Compute $f_m(G_t^{'})$ and compare with the previous step
> Stop at the step if either (i) at least one of the query nodes $Q$ has minimum degree in the graph $G_{T −1}$, or (ii) the query nodes $Q$ are no longer connected. Returns the solution $G_O$ for $G_t^{'}$ where $f_m(G_t^{'})$ is maximized ($G_O = arg max \{f_m(G_t^{'})| t=1,...,T-1\}$).

Greedy can be implemented in linear time and can be used to find an optimal solution for any monotone function.

Drawback of GREEDY: it may return subgraphs with very large size. 

#### 3.1.2 Generalization to monotone functions
The algorithm GREEDY can be used to find an optimal solution for any monotone function.

> **Definition 1 (Monotone function)** The function $f$ is monotone non-increasing if for every graph $G$ and for every induced subgraph $H$ of $G$,$f(H) \leq f(G)$. We similarly define $f$ to be monotone non-decreasing by requiring $f(H) \geq f(G)$.
>
> **Definition 2 (Node-monotone function)** A function $f$ is said to be node-monotone non-increasing if for every graph $G$, for every induced subgraph $H$ of $G$, and every node $v$ in $H$, $f(H, v) \leq f(G, v)$. We similarly define node-monotone non-decreasing functions.

The degree function $d(G, v)$, minimum degree function $f_m(G)$ and distance functions $D_Q(G, v)$ and $D_Q(G)$ are all monotone.

The generalization of the community-search problem.

> **Problem 3 (Cocktail party)** We are given an undirected graph $G = (V, E)$, a node-monotone non-increasing function $f: G_V × V \rightarrow \mathbb{R}$, as well as a set of monotone non-increasing properties $f_1, ..., f_k$. We seek to find an induced subgraph $H$ of $G$ that maximizes $f$ among all induced subgraphs of $G$, and satisfies $f_1, ..., f_k$. A similar problem can be defined by considering to minimize monotone non-decreasing functions.

For solving the Problem 3, we generalize the algorithm GREEDY to GREEDYGEN. In detail, the GREEDYGEN algorithm is described as follows:

> + Start from $G_0 = G$
> + For each step:
>   + While $G_t$ is not empty:
>     + Check if $G_t$ satisfies all properties
>       + Return the subgraph which maximizes $f$ among all graphs $G_t$ that are constructed throughout the execution of the algorithm and satisfy all the monotone properties 
>     + Check whether there is a property $f_j$ and a node $v \in V$ such that $v$ violates $f_j$, $j = 1, ..., k$.
>       + If find such a node, delete $v$ and all the incident edges of $v$
>       + Otherwise, delete from $G$ a node $v$ such that $f(G, v)$ is minimum.

The algorithm GreedyGen returns always an optimum solution for Problem 3. The exact running time of the algorithm depends on the constraints employed.


### 3.2 Communities With Size Constraints
<span style="font-size: 13px;">If there is a specified upper bound of the size of output subgraph, the community search problem becomes NP-hard. Therefore, two simple yet effective heuristics algorithms are proposed.</span>

> **Problem 4 (Minimum degree with upper bound on the size)**: Given an undirected (connected) graph $G = (V_G, E_G)$, a set of query nodes $Q \subseteq V$ , a number $d$ (distance constraint), and an integer $k$ (size constraint), we wish to find an induced subgraph $H = (V_H, E_H)$ of $G$, such that:
> + $H$ contains the query nodes ($Q \subseteq H$); 
> + $H$ is connected;
> + $D_Q(H) \leq d$;
> + $|V_H| \leq k$ ($H$ has at most $k$ nodes);
> + The minimum degree of $H$ is maximized.

*The proof of NP-hard of this problem is using the reduction to the **Steiner-tree problem with unit weights**.*

The two heuristics provide a quality–efficiency trade-off: GreedyDist is tries to optimize quality while GreedyFast tries to optimize efficiency.

#### First Heuristic Algorithm: GREEDYDIST($G$, $Q$, $k$, $d$)
The design principle is the simple observation that a tighter distance constraint implies smaller communities (d $\downarrow$, size $\downarrow$). GREEDYDIST uses the algorithm GREEDYGEN as a subroutine.

> + Execute the algorithm GREEDYGEN in order to maximize the minimum degree subject to the distance constraint $d$ that is specified in input.
> + If the query nodes are connected and the size constraint is not satisfied in the output graph, then execute GREEDYGEN again with a tighter distance bound $d' < d$.
> + GREEDYDIST iterates executing GREEDYGEN by decreasing at each step the distance constraint, until:
>   + The size constraint is satisfied, or
>   + The query nodes become disconnected. In this case, GREEDYDIST returns the smallest graph found among all executions of GREEDYGEN that is connected.

#### Second Heuristic Algorithm: GREEDYFAST($G$, $Q$, $k$, $d$)

There is a preprocessing phase where the input graph is restricted to the $k'$ closest nodes to the query nodes. The distance of a node to the query nodes is measured using the function $D_Q$ defined in Equation (1).

After this preprocessing phase, we execute GREEDY on the restricted graph formed in the preprocessing phase. The intuition for doing this is that, the closer a node is to the query nodes, the more likely it belongs to the community.


## Experimental Evaluation

**Datasets**: DBLP, tag, BIOMINE

**Effectiveness metrics**: the minimum degree $f_m$, the average degree (density) $f_a$, size and distance.

**Case study**: show the quality of the algorithm results