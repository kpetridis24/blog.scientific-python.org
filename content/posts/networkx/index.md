---
title: "Updates on VF2++"
date: 2022-07-06
draft: false
description: "
Summary of the progress on VF2++
"
tags: ["gsoc", "networkx"]
displayInList: true
author: ["Konstantinos Petridis"]

---

This post includes all the major updates since the last post about VF2++. Each section is dedicated to a different
sub-problem and presents the progress on it so far. General progress, milestones and related issues can be
[found here](https://github.com/kpetridis24/networkx/milestone/1).

## Node ordering

The node ordering is one major modification that **VF2++** proposes. Basically the nodes are examined in an order that
makes the matching faster, by firstly examining nodes that are more likely to match. This part of the algorithm has been
implemented, however there is an issue. The existence of detached nodes (not connected to the rest of the graph) causes
the code to crash. Fixing this bug will be a top priority during the next steps.

## $T_i$ and $\tilde{T_i}$

According to the VF2++ paper notation:

$$T_1=\{u\in V_1 \ m: \exists \tilde{u} \in m: (u,\tilde{u}\in E_1)\}$$

where $E_1$ contains all teh edges of the first graph and $m$ is a dictionary, mapping every node of the first graph to
a node of the second graph. Now if we interpet the above equation, we conclude that $T_1$ contains uncovered neighbors
of covered nodes. In simple terms, it includes all the nodes that do not belong in the mapping $m$ yet, but are
neighbors of nodes that are in the mapping. In addition,

$$\tilde{T_1}=\(V_1 \ m \ T_1\)$$
